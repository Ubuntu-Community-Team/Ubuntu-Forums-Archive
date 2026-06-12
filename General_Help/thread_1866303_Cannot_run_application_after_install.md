---
title: "Cannot run application after install"
date: 2011-10-21
forum: General Help
---

### Post by MrFizzbin on 2011-10-21
Greetings. I am new to Linux in general, and Ubuntu in particular. That being said, I'm doing a crash corse and trying to figure it out myself. I am here because I feel I have hit a wall and need outside help.
Background: I have recently install Ubuntu 11.10 (64 bit version) within Windows 7 (64) bit.
Hardware does not seem to be an issue: 
AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ Ã— 
Nvidia GTS 8800 
8 GB DDR2 Ram.
My problem: My GF, (bless her lil heart) needs to run an application called AutoDock4 . It is not compatible with Windows 7 64 bit. 
So.. it's crash course time with Linux ...
I have attempted to install this application (
[http://mgltools.scripps.edu/downloads/instructions/linux](http://mgltools.scripps.edu/downloads/instructions/linux)
) which is a suit that includes Autodock4, etc..
It is a manual install through the terminal interface by the way.
 
It seems to oinstall, but when I attempt to run through GUI's shortcut, nothing happens. If I go into the folder and run it ("adt" it is called i believe) through the terminal..it will load and stop at 100% The terminal window returns the following info:
 
-=-=-=-=-=-=-=-=-
setting PYTHONHOME environment
Run AutoDockTools from /home/stephen/MGLTools-1.5.4/mgltools_x86_64Linux2_1.5.4/MGLToolsPckgs/AutoDockTools
Resource file used to customize PMV: /home/stephen/.mgltools/1.5.4/Pmv/_pmvrc
Traceback (most recent call last):
File "/home/stephen/MGLTools-1.5.4/mgltools_x86_64Linux2_1.5.4/MGLToolsPckgs/AutoDockTools/__init__.py", line 373, in runADT
title=title, withShell= not interactive, verbose=False)
File "/home/stephen/MGLTools-1.5.4/mgltools_x86_64Linux2_1.5.4/MGLToolsPckgs/Pmv/moleculeViewer.py", line 315, in __init__
verbose=verbose, trapExceptions=trapExceptions)
File "/home/stephen/MGLTools-1.5.4/mgltools_x86_64Linux2_1.5.4/MGLToolsPckgs/ViewerFramework/VF.py", line 345, in __init__
verbose=verbose)
File "/home/stephen/MGLTools-1.5.4/mgltools_x86_64Linux2_1.5.4/MGLToolsPckgs/ViewerFramework/VFGUI.py", line 277, in __init__
cnf = {"addScenarioButton": False})
File "/home/stephen/MGLTools-1.5.4/mgltools_x86_64Linux2_1.5.4/MGLToolsPckgs/DejaVu/Viewer.py", line 675, in __init__
cp = ClippingPlane(self.rootObject, i, self)
File "/home/stephen/MGLTools-1.5.4/mgltools_x86_64Linux2_1.5.4/MGLToolsPckgs/DejaVu/Clip.py", line 42, in __init__
self.id = self.clipPlaneNames[num]
IndexError: list index out of range
-=-=-=-=-=-=-=
once I press "Enter" in the terminal, the load page of the application and the terminal disapear..
I don't know where to go at this point.. I seem much closer after 2 weeks of piddling around with this, and it's frustrating the heck out of me.. ANY help at this point would be GREATLY appreciated... I'm basically begging here, if you haven't noticed.

---

### Post by dcstar on 2011-10-22
> **MrFizzbin said:**
> 
........
I have attempted to install this application
[http://mgltools.scripps.edu/downloads/instructions/linux](http://mgltools.scripps.edu/downloads/instructions/linux)
which is a suit that includes Autodock4, etc..
It is a manual install through the terminal interface by the way.
.........
I don't know where to go at this point.. I seem much closer after 2 weeks of piddling around with this, and it's frustrating the heck out of me.. ANY help at this point would be GREATLY appreciated... I'm basically begging here, if you haven't noticed.

So what was the response when **you** used the "Contact Us" link on that page for specifically any sort of problem like this?

---

