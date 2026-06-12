---
title: "error with python or pygtk specifically with ubuntu"
date: 2006-01-30
forum: General Help
---

### Post by cpjeffl on 2006-01-30
Hello all-

I am new to linux and ubuntu.  Someone gave me a python file.  When I try and run it using the command "python base.py" I get the error:

Traceback (most recent call last):
  File "base.py", line 3, in ?
    import pygtk
ImportError: No module named pygtk

Line 3 is

pygtk.require('2.0')

This file works on windows and Fedora.  Please help me get it working on Ubuntu so I don't have to go back to Windows.

Thank You!

---

### Post by amohanty on 2006-01-30
> sudo apt-get install python-gtk2

HTH
AM

---

### Post by cpjeffl on 2006-02-01
thank you for the suggestion, but that wasn't the problem.  I already have python-gtk2 installed.  I also have python-gtk2-dev installed.

Any other ideas?

---

### Post by cpjeffl on 2006-02-01
When I was installing pygtk on windows, it demanded python 2.3 and would not accept python 2.4.  So I just tried installing python2.3 and python2.3-dev on my Ubuntu box to see if it was the same problem.  This did not solve the problem

---

### Post by amohanty on 2006-02-01
I believe python-gtk2 is a dependency pkg ie it always associates with the latest package (which per synaptic is something like 2.4). I think you can safely comment out the line to make it work. Or else, just change that number to the version number specified in synaptic.

AM

---

### Post by cpjeffl on 2006-02-01
Here are the first few lines of the file:

start code
----------------------------------------------

#!/usr/bin/env python

import pygtk
pygtk.require('2.0')
import gtk
import pango
import time

-----------------------------------------------
end code

I tried removing the line import pygtk, that didn't solve the problem

I also tried changing the 2.0 to 2.4 which didn't work

Any other suggestions?

---

### Post by amohanty on 2006-02-01
> I tried removing the line import pygtk, that didn't solve the problem

what is the error here?

AM

---

### Post by cpjeffl on 2006-02-01
The error is:

Traceback (most recent call last):
  File "base.py", line 3, in ?
    pygtk.require('2.0')
NameError: name 'pygtk'is not defined

when I change the 2.0 to 2.4 I get the same error except 

pygtk.require('2.4')

Thank you for all the help... sorry I didn't include the error last time

---

### Post by amohanty on 2006-02-01
If you were to comment the line, whats the problem then?

AM

---

### Post by cpjeffl on 2006-02-02
removing the pygtk.require('2.4')

gives the error

Traceback (most recent call last):
  File "base.py", line 3, in ?
    import gtk
ImportError: No module named gtk


then if I remove the import gtk line I get

Traceback (most recent call last):
  File "base.py", line 3, in ?
    import pango
ImportError: No module named pango


I'm not sure what else to try

---

### Post by amohanty on 2006-02-02
[QUOTE=cpjeffl]removing the pygtk.require('2.4')

gives the error

Traceback (most recent call last):
  File "base.py", line 3, in ?
    import gtk
ImportError: No module named gtk


then if I remove the import gtk line I get

Traceback (most recent call last):
  File "base.py", line 3, in ?
    import pango
ImportError: No module named pango


I'm not sure what else to try[/QUOTE]


Ok so that means that removing the line does not cause any problems, Its the other stuff that does. I dont have access to my boxen right now, but it seems you might need some python dev libs. I will post the thing when I get home.

AM

---

### Post by cpjeffl on 2006-02-06
Do you have any more suggestions?  The problem is still not solved.  Thank you again for all your help.

---

### Post by amohanty on 2006-02-06
ok two things:
1. Look in /usr/lib and see if there is  afolder called **pygtk**. If not reinstall python-gtk2
2. In the command line try:
> aseem@kandinsky:/$ python
Python 2.4.2 (#2, Sep 30 2005, 21:19:01)
[GCC 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import gtk
>>>


If instead of the next prompt you get errors its still not installed.

Finally you can try :
> pygtk-demo

if it says not found, you still dont have python-gtk2 installed.
reinstall from synaptic/

AM

---

### Post by cpjeffl on 2006-02-09
Hi Sorry I took so long to reply.  I didn't have access to my Ubuntu box yesterday

So as you can see it appears that I don't have gtk properly installed:

jlabarge@jeff-ubuntu:/usr/lib$ python
Python 2.4.2 (#1, Jan 24 2006, 22:29:37)
[GCC 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import gtk
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
ImportError: No module named gtk
>>>


>>> pygtk-demo
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
NameError: name 'pygtk' is not defined
>>>

So I tried installing it, and my box thinks that it is properly installed.


jlabarge@jeff-ubuntu:~$ sudo apt-get install python-gtk2
Reading package lists... Done
Building dependency tree... Done
python-gtk2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
jlabarge@jeff-ubuntu:~$



jlabarge@jeff-ubuntu:~$ sudo apt-get install python-gtk2-dev
Reading package lists... Done
Building dependency tree... Done
python-gtk2-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.


I thought a view of my folders might help too

jlabarge@jeff-ubuntu:/usr/lib$ ls py
pygtk/     python2.3/ python2.4/

jlabarge@jeff-ubuntu:/usr/bin$ ls py
pydoc              pygettext          pygtk-codegen-2.0  python2.3
pydoc2.3           pygettext2.3       pygtk-demo         python2.4
pydoc2.4           pygettext2.4       python


Please let me know what packages you think that I am missing, or if there are packages that are conflicting.

Thank you again for your help

---

### Post by amohanty on 2006-02-09
Can you verify that you have the following files:
> /usr/lib/python2.4/site-packages/pygtk.pth
/usr/lib/python2.4/site-packages/pygtk.py.python2.4-gtk2
/usr/lib/python2.4/site-packages/pygtk.pyo
/usr/lib/python2.4/site-packages/pygtk.py
/usr/lib/python2.4/site-packages/pygtk.pyc



ALso this:
>  pygtk-demo

This to be done on the command line _not_ inside the python interpreter shell, which is what you tried.

HTH
AM

---

### Post by cpjeffl on 2006-02-10
Thanks for the quick response

Yes all those files exist

jlabarge@jeff-ubuntu:~$ ls /usr/lib/python2.4/site-packages/pygtk.p*
/usr/lib/python2.4/site-packages/pygtk.pth
/usr/lib/python2.4/site-packages/pygtk.py
/usr/lib/python2.4/site-packages/pygtk.pyc
/usr/lib/python2.4/site-packages/pygtk.pyo
/usr/lib/python2.4/site-packages/pygtk.py.python2.4-gtk2

Also, when I type pygtk-demo a GUI pops up that says:

Application main window
Demonstrates a typical application window, with menubar, toolbar, statusbar.

So, the demo appears to work

If the demo works, does that mean that pygtk is correctly installed?

Thanks again

---

### Post by cpjeffl on 2006-02-13
From Beginning Python by Peter Norton and other authors, I added this file to my project:

```

#!/usr/bin/env python
"""
findgtk.py - Find the pyGTK libraries, wherever they are.
"""
import os
import sys
sys.path.append("/usr/lcoal/lib/python2.3/site-packages/")

def try_import():
	import sys
	"""tries to import gtk and if successful, returns 1"""
#print "Attempting to load gtk... Path=%s"%sys.path
#To require 2.0
	try:
		import pygtk
		pygtk.require("2.0")
	except:
		print "pyGTK not found.  You need GTK 2 to run this."
		print "Did you \"export PYTHONPATH=/usr/local/lib/python2.2/site-packages/\" first?"
		print "Perhaps you have GTK2 but not pyGTK, so I will continue to tyrn loading."

	
	try:
		import gtk,gtk.glade
		import atk,pango #for py2exe
		import gobject
	except:
		import traceback,sys
		traceback.print_exc(file=sys.stdout)
		print "I'm sorry, you apparently do not have GTK2 installed - I tried"
		print "to import gtk, gtk.glade, and gobject, and I failed."

		return 0
	return 1

if not try_import():
	site_packages=0
#for k in sys.path:
#	if k.count("site-packages"):
#		print "existing site-packages path %s found\n%k
#		site_packages=1
	if site_packages == 0:
		from stat import *
#print "no site-packages path set, checking.\n"
		check_lib = [ "/usr/lib/python2.2/site-packages/",
						"/usr/local/lib/python2.2/site-packages/",
						"/usr/local/lib/python2.3/site-packages/" ]
		for k in check_lib:
			try:
				path=os.path.join(k,"pygtk.py")
#print "Path=%s"%path
				if open(path)!=None:
#print "appending", k
					sys.path=[k]+sys.path
					if try_import():
						break
			except:
				pass
	if not try_import():
		sys.exit(0)


```

This is then included in the original file as:

```


#!/usr/bin/env python

#import serial
import findgtk
import pygtk
pygtk.require('2.0')
import gtk
import pango
import time


```

This yeilds the following results:

jlabarge@jeff-ubuntu:~/IEEE/robo_program$ python base.py
pyGTK not found.  You need GTK 2 to run this.
Did you "export PYTHONPATH=/usr/local/lib/python2.2/site-packages/" first?
Perhaps you have GTK2 but not pyGTK, so I will continue to tyrn loading.
Traceback (most recent call last):
  File "/home/jlabarge/IEEE/robo_program/findgtk.py", line 24, in try_import
    import gtk,gtk.glade
ImportError: No module named gtk
I'm sorry, you apparently do not have GTK2 installed - I tried
to import gtk, gtk.glade, and gobject, and I failed.
pyGTK not found.  You need GTK 2 to run this.
Did you "export PYTHONPATH=/usr/local/lib/python2.2/site-packages/" first?
Perhaps you have GTK2 but not pyGTK, so I will continue to tyrn loading.
Traceback (most recent call last):
  File "/home/jlabarge/IEEE/robo_program/findgtk.py", line 24, in try_import
    import gtk,gtk.glade
ImportError: No module named gtk
I'm sorry, you apparently do not have GTK2 installed - I tried
to import gtk, gtk.glade, and gobject, and I failed.


Does this help you narrow down the problem?  What else can I try?

---

### Post by amohanty on 2006-02-13
Try this:

> export PYTHONPATH=/usr/local/lib/**python2.4**/site-packages/

Note that I use python2.4 because thats where your pytgtk stuff is.
And try again.
You do not need to use the file that you provided above in most cases.

Also this **#!/usr/bin/env python** should probably be **#!/usr/bin/python**

HTH
AM

---

### Post by cpjeffl on 2006-02-13
None of those changes worked.  bummer.

any other ideas?

---

### Post by amohanty on 2006-02-14
ok post the output of the following:

> 09:05 AM $ python
Python 2.4.1 (#1, May 27 2005, 18:02:40) 
[GCC 3.3.3 (cygwin special)] on cygwin
Type "help", "copyright", "credits" or "license" for more information.
>>> **import sys**
>>> **print sys.path**
['', '/usr/lib/python24.zip', '/usr/lib/python2.4', '/usr/lib/python2.4/plat-cygwin', '/usr/lib/python2.4/lib-tk', '/usr/lib/python2.4/lib-dynload', '/usr/lib/python2.4/site-packages']
>>> 


AM

---

### Post by cpjeffl on 2006-02-14
this is the output that you asked for

> 
jlabarge@jeff-ubuntu:~$ python
Python 2.4.2 (#1, Jan 24 2006, 22:29:37)
[GCC 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> print sys.path
['', '/usr/local/lib/python24.zip', '/usr/local/lib/python2.4', '/usr/local/lib/python2.4/plat-linux2', '/usr/local/lib/python2.4/lib-tk', '/usr/local/lib/python2.4/lib-dynload', '/usr/local/lib/python2.4/site-packages']
>>>



There are some differences between our outputs, however I don't know if I need everything that you have so I am just going to wait for a reply.  Thanks again for your help

---

### Post by amohanty on 2006-02-15
Dude everything seems to be fine. pygtk seems to be in your path, you have the required files, they seem to be of the right version. As a last ditch effort, start python in **/usr/local/lib/python2.4/site-packages/**. And then try a:
> import gtk

Also in synaptic check to see if all of these are installed:
python2.4-glade2
python2.4-gnome2
python2.4-gnome2-extras
python2.4-gtk2
python-glade2
python-gnome2
python-gnome2-extras
python-gtk2
python-wxgtk2.6

Also try uninstalling version 2.3 if you have it.


HTH
AM

---

### Post by cpjeffl on 2006-02-16
[QUOTE=amohanty]Dude everything seems to be fine. pygtk seems to be in your path, you have the required files, they seem to be of the right version.
[/QUOTE]

haha, well it still isn't working, but at least it wasn't something super obvious.  As a relatively new linux user I'm always afraid that I'm making some really stupid mistake.  I really appreciate all your help.


[QUOTE=amohanty]
 As a last ditch effort, start python in **/usr/local/lib/python2.4/site-packages/**. And then try a:
[/QUOTE]

Here is the text from the terminal

> 
jlabarge@jeff-ubuntu:~$ cd /usr/local/lib/python2.4/site-packages/
jlabarge@jeff-ubuntu:/usr/local/lib/python2.4/site-packages$ python
Python 2.4.2 (#1, Jan 24 2006, 22:29:37)
[GCC 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import gtk
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
ImportError: No module named gtk
>>>


And finally, for the instructions

[QUOTE=amohanty]
Also in synaptic check to see if all of these are installed:
python2.4-glade2
python2.4-gnome2
python2.4-gnome2-extras
python2.4-gtk2
python-glade2
python-gnome2
python-gnome2-extras
python-gtk2
python-wxgtk2.6

Also try uninstalling version 2.3 if you have it.


HTH
AM[/QUOTE]

The only package that I didn't have was the python-wxgtk2.6.  I used synaptic to get it, but it didn't fix the problem.  I also uninstalled 2.3 and 2.3-dev (the 2.3-dev was a dependency that synaptic decided to remove)

I know you said that this was a last ditch effort, but can you think of anything else?  I am still stumped.  Thanks again

---

### Post by amohanty on 2006-02-16
Whoa! I just noticed something:
When you listed the location of the gtk python file you listed:
> jlabarge@jeff-ubuntu:~$ ls /usr/lib/python2.4/site-packages/pygtk.p*
/usr/lib/python2.4/site-packages/pygtk.pth
/usr/lib/python2.4/site-packages/pygtk.py
/usr/lib/python2.4/site-packages/pygtk.pyc
/usr/lib/python2.4/site-packages/pygtk.pyo
/usr/lib/python2.4/site-packages/pygtk.py.python2.4-gtk2

Now in your sys.path you gave:
>  jlabarge@jeff-ubuntu:~$ python
Python 2.4.2 (#1, Jan 24 2006, 22:29:37)
[GCC 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> print sys.path
['', '/usr/local/lib/python24.zip', '/usr/local/lib/python2.4', '/usr/local/lib/python2.4/plat-linux2', '/usr/local/lib/python2.4/lib-tk', '/usr/local/lib/python2.4/lib-dynload', '/usr/local/lib/python2.4/site-packages']
>>>

I dont see **/usr/lib/python2.4** in the sys path. No wonder you arent able to import the module.

In python shell try this:
> 
>>> import sys
>>> sys.path.append("/usr/lib/python2.4/site-packages/")
>>> import gtk


That should make it work.

AM

---

### Post by cpjeffl on 2006-02-17
hmm... from /home/jlabarge I tried

> 
jlabarge@jeff-ubuntu:~$ python
Python 2.4.2 (#1, Jan 24 2006, 22:29:37)
[GCC 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> sys.path.append("/usr/lib/python2.4/site-packages/")
>>> import gtk
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
ImportError: No module named gtk
>>>


as you can see it still says that there is no module named gtk

Do I need to do this from another directory?  Any other suggestions?

---

### Post by amohanty on 2006-02-17
Once you do this:
> >>> import sys
>>> sys.path.append("/usr/lib/python2.4/site-packages/")

what does a **print sys.path** return?

AM

---

### Post by amohanty on 2006-02-17
Once you do this:
> >>> import sys
>>> sys.path.append("/usr/lib/python2.4/site-packages/")

what does a **print sys.path** return?

ALso try adding the gtk path to your sys.path via
> 
>>> sys.path.append("/usr/lib/python2.4/site-packages")
>>> sys.path.append("/usr/lib/python2.4/site-packages/gtk-2.0")

AM

---

### Post by cpjeffl on 2006-02-18
ok, well that didn't fix the problem, but there is a different error which might be helpful.  Here is what I did:

> 
jlabarge@jeff-ubuntu:~$ python
Python 2.4.2 (#1, Jan 24 2006, 22:29:37)
[GCC 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> sys.path.append("/usr/lib/python2.4/site-packages/")
>>> print sys.path
['', '/usr/local/lib/python24.zip', '/usr/local/lib/python2.4', '/usr/local/lib/python2.4/plat-linux2', '/usr/local/lib/python2.4/lib-tk', '/usr/local/lib/python2.4/lib-dynload', '/usr/local/lib/python2.4/site-packages', '/usr/lib/python2.4/site-packages/']
>>> sys.path.append("/usr/lib/python2.4/site-packages")
>>> sys.path.append("/usr/lib/python2.4/site-packages/gtk-2.0")
>>> print sys.path
['', '/usr/local/lib/python24.zip', '/usr/local/lib/python2.4', '/usr/local/lib/python2.4/plat-linux2', '/usr/local/lib/python2.4/lib-tk', '/usr/local/lib/python2.4/lib-dynload', '/usr/local/lib/python2.4/site-packages', '/usr/lib/python2.4/site-packages/', '/usr/lib/python2.4/site-packages', '/usr/lib/python2.4/site-packages/gtk-2.0']
>>> import gtk
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 33, in ?    import gobject as _gobject
ImportError: /usr/lib/python2.4/site-packages/gtk-2.0/gobject.so: undefined symbol: PyUnicodeUCS4_AsUnicode
>>>


I think the /usr/lib/python2.4/site-packages and gtk-2.0 got added because they show up in the print.  However, it has a problem with the gtk-2.0 for some reason.

Any ideas?

---

### Post by amohanty on 2006-02-19
> >>> import gtk
Traceback (most recent call last):
File "<stdin>", line 1, in ?
File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 33, in ? import gobject as _gobject
ImportError: /usr/lib/python2.4/site-packages/gtk-2.0/gobject.so: undefined symbol: PyUnicodeUCS4_AsUnicode
>>>

Ahh the joys of unicode... This might shed some light:
[http://python.fyxm.net/doc/FAQ.html#when-importing-module-xxx-why-do-i-get-undefined-symbol-pyunicodeucs2](http://python.fyxm.net/doc/FAQ.html#when-importing-module-xxx-why-do-i-get-undefined-symbol-pyunicodeucs2)

Usually a clean reinstall of pygtk, python-dev and any associated packages should fix it. Did you make sure that you dont have two versions of python?

AM

---

### Post by cpjeffl on 2006-02-19
ok, I looked in synaptic and these two items (obviously they are not code, but I had to use those tags to get it to keep my spacing)

```

package     | installed version    | Latest version
=================================================
python        2.4.2-0ubuntu2         2.4.2-0ubuntu2
python2.4     2.4.2-1                2.4.2-1


```

Are these two versions are python?  If so, which one should I get rid of?

Also, when you say that I need to reinstall python and python-dev, does it have to be from source or can I use synaptic? How do I know which one is correctly compiled with a unicode that matches my ubuntu?

---

### Post by amohanty on 2006-02-19
> Are these two versions are python? If so, which one should I get rid of?

None. the one called python is just a dependency pkg that depends on the latest version of python.

> Also, when you say that I need to reinstall python and python-dev, does it have to be from source or can I use synaptic?

Synaptic will be fine. Also reinstall python gtk and associated lib pkgs.


> How do I know which one is correctly compiled with a unicode that matches my ubuntu?

From the link I provided you:
> >>> import sys
>>> if sys.maxunicode > 65535:
...     print 'UCS4 build'
... else:
...     print 'UCS2 build'



Your libs cannot recognize ucs4


HTH
AM

---

### Post by cpjeffl on 2006-02-19
Indeed you were correct and that python command returned 

> UCS2 build

Using synaptic I marked the following packages for reinstallation

python2.4-dev
python2.4-gtk2
python-gtk2
python-gtk2-dev

This did not fix the problem.  I got the same problem

> >>> import gtk
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 33, in ?    import gobject as _gobject
ImportError: /usr/lib/python2.4/site-packages/gtk-2.0/gobject.so: undefined symbol: PyUnicodeUCS4_AsUnicode


I thought maybe it would help to do a complete removal and then install, however when I did "Mark for Removal" it said that it was going to uninstall gimp-python and ubuntu-desktop.  I don't think I should have to uninstall the desktop to change this.  

Should mark for reinstallation do it?

---

### Post by amohanty on 2006-02-20
No you dont need to do a complete reinstall for this. Keep in mind that ubuntu-desktop is not really a package, it is a dependency package that makes sure that certain things are installed in the system.

Having said that you shouldnt need to do that. A reinstall of pygtk should have fixed the problem, and seeing that I dont have that prob, you shouldnt either. Other than attempting to install py-gtk from source, something I wouldnt recommend for now at least, I dont see what else I can tell you. Unfortunately since I dont encounter this problem, its a bit difficult to really figure it out.

However now that you know the actual problem, ie unicode, why not repost the problem with a more meaningful title like: python UCS2/4 problem or something to that effect. Hopefully somebody who has actually run into this problem and fixed it may be able to help you out.

AM

---

### Post by cpjeffl on 2006-02-21
Ok, that sounds like a good next step.  Thank you very much for all your help.

I will post the solution to this if I figure it out.

Thanks again!

---

### Post by wile_e8 on 2006-02-27
Hello, I found this thread because I was running into errors with pygtk.  I tried to follow [post=692118]this[/post] post to install gdesklets, but it caused problems with pygtk and gtk.  I uninstalled them, but I ended up with the same "no module named pygtk" error that started this thread when I tried to run applications that used them (like gmail-notify).  I ran into some of the same errors in this thread with the same resolution to the missing module by appending sys.path when I was running python.  However, this fix only last for the python session.  Is there any way to fix the path for programs that call python and pygtk?  Does this make sense at all?  I have no idea if it will help, but I've already tried for help in [thread=136863]this[/thread] thread, but couldn't find a resolution there.  Maybe that will help describe my problem.

---

### Post by tnasniv on 2006-03-11
Same problem but with dapper

---

### Post by wile_e8 on 2006-03-12
I found a solution to my problem.  I had a version of python installed at /usr/local/bin/python and any calls to python were running from there, instead of the standard ubuntu location of /usr/bin/python.  I deleted the folder with the new installation, and after that the standard version was getting called and everything worked fine.  Maybe that is your problem too, good luck.

---

### Post by WelterPelter on 2006-04-02
wile_e8, I found that folder and deleted its contents. Now Python apps run, but not the Python shell. DId you have to fiddle with any path variables to get yours to work?

Correction: actually, a reboot got it all working right.

---

### Post by SilvaRizla on 2008-01-12
I've got the same problem in Gutsy, but don't have python in local/bin

Any other ideas anyone?

---

### Post by SilvaRizla on 2008-01-12
Doesn't matter,  I did have another version, deleted it and its now sorted.  Thanks guys

---

