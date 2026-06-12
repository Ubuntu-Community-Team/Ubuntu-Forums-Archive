---
title: "Compilation of SAGE mathematics suite failed?"
date: 2011-05-21
forum: General Help
---

### Post by groundnut on 2011-05-21
I have just compiled SAGE, a mathematics suite.

While running the program I get an Import Error as you can see below.

Can someone tell me what the problem is?


terminal response:

tony@xp:~/Aplicaties/sage-4.6.2$ ./sage
----------------------------------------------------------------------
| Sage Version 4.6.2, Release Date: 2011-02-25                       |
| Type notebook() for the GUI, and license() for information.        |
----------------------------------------------------------------------
---------------------------------------------------------------------------
ImportError                               Traceback (most recent call last)

/home/tony/Aplicaties/sage-4.6.2/local/lib/python2.6/site-packages/IPython/ipmaker.pyc in force_import(modname)
     64         reload(sys.modules[modname])
     65     else:
---> 66         __import__(modname)
     67 
     68 

/home/tony/Aplicaties/sage-4.6.2/local/bin/ipy_profile_sage.py in <module>()
      5     preparser(True)
      6 
----> 7     import sage.all_cmdline
      8     sage.all_cmdline._init_cmdline(globals())
      9 

/home/tony/Aplicaties/sage-4.6.2/local/lib/python2.6/site-packages/sage/all_cmdline.py in <module>()
     12 try:
     13 
---> 14     from sage.all import *
     15     from sage.calculus.predefined import x
     16     preparser(on=True)

/home/tony/Aplicaties/sage-4.6.2/local/lib/python2.6/site-packages/sage/all.py in <module>()
     97 from sage.calculus.all   import *
     98 
---> 99 from sage.server.all     import *
    100 import sage.tests.all as tests
    101 

/home/tony/Aplicaties/sage-4.6.2/local/lib/python2.6/site-packages/sage/server/all.py in <module>()
      1 
----> 2 #from server1.all import *

      3 from notebook.all import *
      4 from wiki.all import *
      5 from trac.all import *
      6 

/home/tony/Aplicaties/sage-4.6.2/local/lib/python2.6/site-packages/sage/server/notebook/all.py in <module>()
     20 
     21 # Import the new separated Sage notebook.

---> 22 from sagenb.notebook.all import *
     23 
     24 

/home/tony/Aplicaties/sage-4.6.2/devel/sagenb/sagenb/notebook/all.py in <module>()
     14 from sage_email import email
     15 
---> 16 from notebook_object import notebook, inotebook
     17 
     18 from interact import interact, input_box, slider, range_slider, selector, checkbox, input_grid, text_control, color_selector

/home/tony/Aplicaties/sage-4.6.2/devel/sagenb/sagenb/notebook/notebook_object.py in <module>()
     15 import time, os, shutil, signal, tempfile
     16 
---> 17 import notebook as _notebook
     18 
     19 import run_notebook

/home/tony/Aplicaties/sage-4.6.2/devel/sagenb/sagenb/notebook/notebook.pyc in <module>()
     44 import server_conf  # server configuration
     45 import user_conf    # user configuration
---> 46 import user         # users
     47 from   template import template, prettify_time_ago
     48 

/home/tony/Aplicaties/sage-4.6.2/devel/sagenb/sagenb/notebook/user.py in <module>()
      1 # -*- coding: utf-8 -*

      2 import copy
----> 3 import crypt
      4 import cPickle
      5 import os

ImportError: No module named crypt
Error importing ipy_profile_sage - perhaps you should run %upgrade?
WARNING: Loading of ipy_profile_sage failed.

sage:

---

### Post by hulkman on 2011-05-21
This is a bug in Ubuntu 11.04.  It is to be fixed in Sage 4.7.  Right now there is a sage 4.7 Alpha release found here: [http://www.google.com/url?sa=D&q=http://sage.math.washington.edu/home/release/sage-4.7.alpha4/sage-4.7.alpha4.tar](http://www.google.com/url?sa=D&q=http://sage.math.washington.edu/home/release/sage-4.7.alpha4/sage-4.7.alpha4.tar) I'm sure the bug is fixed in this alpha release though.

---------------------
[http://www.dotdeb.com](http://www.dotdeb.com) has a lot of deb packages.

---

### Post by groundnut on 2011-05-22
thank you hulkman.

Apparently I still have the same problem after compiling 4.7 alpha.

response:

[email]tony@xp:~/Aplicaties/sage-4.7.alpha[/email]4$ ./sage
----------------------------------------------------------------------
| Sage Version 4.7.alpha4, Release Date: 2011-04-11                  |
| Type notebook() for the GUI, and license() for information.        |
----------------------------------------------------------------------
**********************************************************************
*                                                                    *
* Warning: this is a prerelease version, and it may be unstable.     *
*                                                                    *
**********************************************************************
---------------------------------------------------------------------------
ImportError                               Traceback (most recent call last)

/home/tony/Aplicaties/sage-4.7.alpha4/local/lib/python2.6/site-packages/IPython/ipmaker.pyc in force_import(modname)
     64         reload(sys.modules[modname])
     65     else:
---> 66         __import__(modname)
     67 
     68 

/home/tony/Aplicaties/sage-4.7.alpha4/local/bin/ipy_profile_sage.py in <module>()
      5     preparser(True)
      6 
----> 7     import sage.all_cmdline
      8     sage.all_cmdline._init_cmdline(globals())
      9 

/home/tony/Aplicaties/sage-4.7.alpha4/local/lib/python2.6/site-packages/sage/all_cmdline.py in <module>()
     12 try:
     13 
---> 14     from sage.all import *
     15     from sage.calculus.predefined import x
     16     preparser(on=True)

/home/tony/Aplicaties/sage-4.7.alpha4/local/lib/python2.6/site-packages/sage/all.py in <module>()
    104 from sage.calculus.all   import *
    105 
--> 106 from sage.server.all     import *
    107 import sage.tests.all as tests
    108 

/home/tony/Aplicaties/sage-4.7.alpha4/local/lib/python2.6/site-packages/sage/server/all.py in <module>()
      1 
----> 2 #from server1.all import *

      3 from notebook.all import *
      4 from wiki.all import *
      5 from trac.all import *
      6 

/home/tony/Aplicaties/sage-4.7.alpha4/local/lib/python2.6/site-packages/sage/server/notebook/all.py in <module>()
     20 
     21 # Import the new separated Sage notebook.

---> 22 from sagenb.notebook.all import *
     23 
     24 

/home/tony/Aplicaties/sage-4.7.alpha4/devel/sagenb/sagenb/notebook/all.py in <module>()
     14 from sage_email import email
     15 
---> 16 from notebook_object import notebook, inotebook
     17 
     18 from interact import interact, input_box, slider, range_slider, selector, checkbox, input_grid, text_control, color_selector

/home/tony/Aplicaties/sage-4.7.alpha4/devel/sagenb/sagenb/notebook/notebook_object.py in <module>()
     15 import time, os, shutil, signal, tempfile
     16 
---> 17 import notebook as _notebook
     18 
     19 import run_notebook

/home/tony/Aplicaties/sage-4.7.alpha4/devel/sagenb/sagenb/notebook/notebook.pyc in <module>()
     44 import server_conf  # server configuration
     45 import user_conf    # user configuration
---> 46 import user         # users
     47 from   template import template, prettify_time_ago
     48 

/home/tony/Aplicaties/sage-4.7.alpha4/devel/sagenb/sagenb/notebook/user.py in <module>()
      1 # -*- coding: utf-8 -*

      2 import copy
----> 3 import crypt
      4 import cPickle
      5 import os

ImportError: No module named crypt
Error importing ipy_profile_sage - perhaps you should run %upgrade?
WARNING: Loading of ipy_profile_sage failed.

sage:

---

### Post by groundnut on 2011-05-22
I will tell you what I have done.

I applied the following 3 commands:

sudo apt-get upgrade && sudo apt-get install build-essential m4 gfortran
sudo apt-get install imagemagick texlive
make

---

