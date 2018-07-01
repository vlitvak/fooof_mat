# Matlab support for running FOOOF

Here we offer some support materials for using [FOOOF](https://github.com/voytekresearch/fooof) as a Matlab user. Note that the current options offered here still use the Python implementation, and so do require a working Python install - but that should be easy to do, and instructions are provided below to do so. 

## Matlab Wrapper

The Matlab wrapper, in 'matlab_wrapper' is some Matlab code, that calls the Python implementation of FOOOF. This requires that you have Python & FOOOF installed, but does not require you to ever use or write Python code yourself. 

To try this, clone or download this repository, and then use the the provided matlab code to run FOOOF. The only function you need to run is 'fooof.m', which has documentation on inputs and outputs.

Note that this is a very minimal wrapper - it provides access only to the core algorithm, and not to any of extra utilities, such as plotting model outputs. As the algorithm is really the purpose of FOOOF, you are not lacking any functionality in that sense - all the inputs settings and model outputs are available to you.

#### Dependencies

This Matlab wrapper uses the Python support introduced by Matlab in 2014b, and as such requires that version, or higher, to run.

#### pyversion

Once you have downloaded Python, you shouldn't need to do anything for Matlab to be able to call Python - as long as your Matlab is using the correct Python. If it's not working, this is likely the problem.

You can run `pyversion` to see which Python you are using. Note that you must do this _after installing Python and FOOOF_ (instruction to do so below).
```
% Check which python is being used. 
pyversion

% The print out from above should tell you which Python you are calling
%  It should show that you are using Python version 3.6.
%  It should also show that the 'home' of this python is in the anaconda folder
%  If either of these things are not right, reset which Python you are using, as below

% Set python version to use
%  Note: you must do this first thing after opening Matlab (relaunch if you need to)
%  You should only ever have to run this at most, once. 
pyversion('/anaconda/bin/python')
```

## Matlab -> Python -> Matlab

Since you need to install Python anyways, another potential workflow is to do all of your processing and analysis in Matlab, up to and including calculating power spectra, which you then save out to mat files. You can then load these files in Python, run and explore FOOOF, then save out the model fit results, that can be loaded back into Matlab, if you prefer. 

The benefit of this approach, over using the wrapper, is that you have full access to the FOOOF module in Python, which makes it easier to use utilities to plot outputs and see what's happening. 

An example / template workflow for using this approach, including matlab and python scriptys, is available in 'mat_py_mat'. With this template, you should be able get working with this workflow without having to write almost any Python code. 

## Installing Python & FOOOF

Both workflows above require that Python & FOOOF be installed. The easiest way to do this is as follows:

#### Install Python with Anaconda

To install Python, as well as all the dependencies you need and including tools like Jupyter notebook, go to the [Anaconda Website](https://www.anaconda.com/download/) and download the Python 3.6 version. Install the file you download, and then you're good to go!

Note that your computer may well have a version of Python - but you should still go an install a new one with Anaconda - this ensures that you have all the dependencies you need, and leaves your system Python alone, for safety.

Once you've downloaded Anaconda, you will have a program called 'Anaconda Navigator', which you can use to launch Juypter notebooks, if you want.

#### Install FOOOF

FOOOF can be installed through pip, meaning you just have to run the following from the command line:

`pip install fooof`

If you're on mac, 'command line' means terminal - after installing anaconda, just copy the above command into the terminal, and it should work. If you're on windows, you will need to run this in 'anaconda command prompt' which is basically a command line specifically for managing Python with Anaconda. 

## Potential Matlab Implementation

The above workflows still use the Python implementation of FOOOF. This has some perks, in that running the exact same code means that there are no worries about maintaining and verying the consistency between multiple implementations of the code. However, it does still require this somewhat annoying coordinating between languages, if one wants to use Matlab. The only way to get around this would be to have a re-implemenation of the algorithm in Matlab, in which case it could be used in a stand-alone manner. 

As of right now, there are no plans for us to a full re-implementation of the algorithm in Matlab - it's non-trivial to re-write, test, confirm equivalence, and then continuously maintain two versions. That said, the code is open, so if want to try and do this yourself, go for it!
