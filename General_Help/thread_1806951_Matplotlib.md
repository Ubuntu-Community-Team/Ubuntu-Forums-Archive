---
title: "Matplotlib"
date: 2011-07-18
forum: General Help
---

### Post by abottrill on 2011-07-18
Hi all, 
Keep getting this error when I try to import matplotlib. was working fine before and don't think I have changed anything.  anyone got any ideas?

When I try to remove and the reinstall the what I hoped was the stable version from the repository it still gives the same error

File "/usr/bin/ipython", line 28, in <module>
    IPython.Shell.start().mainloop()
  File "/usr/lib/pymodules/python2.6/IPython/Shell.py", line 1240, in start
    shell = _select_shell(sys.argv)
  File "/usr/lib/pymodules/python2.6/IPython/Shell.py", line 1197, in _select_shell
    import matplotlib
  File "/usr/lib/pymodules/python2.6/matplotlib/__init__.py", line 766, in <module>
    rcParams = rc_params()
  File "/usr/lib/pymodules/python2.6/matplotlib/__init__.py", line 684, in rc_params
    fname = matplotlib_fname()
  File "/usr/lib/pymodules/python2.6/matplotlib/__init__.py", line 601, in matplotlib_fname
    path =  get_data_path() # guaranteed to exist or raise
  File "/usr/lib/pymodules/python2.6/matplotlib/__init__.py", line 248, in wrapper
    ret = func(*args, **kwargs)
  File "/usr/lib/pymodules/python2.6/matplotlib/__init__.py", line 522, in _get_data_path_cached
    defaultParams['datapath'][0] = _get_data_path()
  File "/usr/lib/pymodules/python2.6/matplotlib/__init__.py", line 518, in _get_data_path
    raise RuntimeError('Could not find the matplotlib data files')
RuntimeError: Could not find the matplotlib data files

---

### Post by abottrill on 2011-07-19
Have sorted the problem by rolling back to matplotlib-0.99.1.1 would like 1.01 at some point but atleast it is now working as before.

---

