---
title: "Ubuntu Software Centre not working"
date: 2009-10-30
forum: General Help
---

### Post by magneze on 2009-10-30
Did a fresh install of Karmic to get all the GRUB2 and ext4 goodness. However, the Software Centre doesn't work.

All the apps say "Not available in the current data"!

What's up and what does this message mean?

---

### Post by smCw6GNakQn300£ on 2009-10-30
What are you trying to install?

It sounds like you don't have the relevant source for it (PPA).

I had that last night for a few things - check the software sources, and make sure you have the multiverse selected.
After that, you might want to do a google search for "xxx ppa" where xxx is the name of the app you want to install...

---

### Post by dj-toonz on 2009-10-30
try this 
 
open up a terimal an type 'sudo apt-get update'
then try again

---

### Post by magneze on 2009-10-30
I've tried installing Flash and Lincity. When they didn't work I tried a few other random apps. All have the same message!

Will try your suggestion dj-toonz ..

---

### Post by magneze on 2009-10-30
Yeah, that did it. Cheers!

Out of interest, what do you think the problem was?

---

### Post by P4man on 2009-10-30
Maybe your mirror is overloaded right now with the new release. Perhaps try going to system > administration > software sources and select a different mirror.  Try download from > other > select best server

edit: never mind :)

---

### Post by jxchamb on 2009-10-30
My software center isn't working this morning.  
It says 0 items available even if I click on Installed Software.
I tried changing servers and I did an apt-get update but no luck.
It was working yesterday and the day before but not today. 

 Anybody else have this issue?

---

### Post by SteveDee on 2009-10-30
> **jxchamb said:**
> My software center isn't working this morning...Anybody else have this issue?

Yeah, I just installed Karmic on a spare computer (thank god) and I can't install anything via Ubuntu Software Centre. But as I can go to Synaptic and install, I assume its the Software Centre code that has the problem.

I also find it very disappointing that the message reads "Not available in the current data" as this is not the kind of meaningless message that users should be presented with. It doesn't help when you are trying to convince family & friends to adopt Ubuntu.

---

### Post by magneze on 2009-10-30
> **SteveDee said:**
> Yeah, I just installed Karmic on a spare computer (thank god) and I can't install anything via Ubuntu Software Centre. But as I can go to Synaptic and install, I assume its the Software Centre code that has the problem.

I also find it very disappointing that the message reads "Not available in the current data" as this is not the kind of meaningless message that users should be presented with. It doesn't help when you are trying to convince family & friends to adopt Ubuntu.Yes, that error message really needs improving. It's meaningless at the moment!

---

### Post by Evie~ on 2010-01-07
Thank you SO MUCH for your helpful tips in this thread, you've just solved another dilemma that I've been tearing my hair out about for the past 3 weeks :D

---

### Post by Mr Potter on 2010-05-07
If like myself you ran into this same problem with clean install 10.04 you may have some luck with this work around.  I usually use the gnome "Main Menu", but this should still work with the "Menu Bar"

Right click the "Main Menu" and select "Edit Menus", Select "Applications in the left pane of the window, then click on "Ubuntu Software Center" in the middle pane, then click the "Properties" button from the right side of the "edit menus" window.  Change text in the field "Command" to:

gksudo software-center

You will be prompted for the administrator password to launch software center, but it will open and function as expected.  

The problem I was having was that when I clicked on the original Software Center menu item nothing would happen. I attempted to re-install software center, but the problem persisted. After attempting to launch it from the command line I received a permission error. Launching with the command  *sudo software-center * worked as expected.  I'm not sure why this permission issue happened, as I installed 10.04 on a formatted drive and out of the box Software Center failed to launch.  I'm going to attempt another install on the same machine and I'll report back if the problem persists.

---

### Post by P4man on 2010-05-07
There is no need to launch software center as root. In fact I suspect its a very bad idea. If its not working normally then its a symptom of sonething else being wrong. Try running software-center from a terminal and see what error it gives.

---

### Post by asamf on 2010-06-09
the easy solution was to uninstall and reinstall ubuntu software center

open terminal and as root  ( type $ sudo su   )

to uninstall ubuntu software center type 
 
     [B]apt-get remove software-center

[/B]and to reinstall it again type
[B] 
     apt-get install software-center

-----------------------------------------------[/B]
this helped me hope it helps you..............:lolflag:):P

---

### Post by damo65 on 2010-07-10
I've not had any problems with 64 bit version for 2 1/2 years, but ran into problems within minutes with the 32 bit version of Software Centre! I thought it was usually the other way round!
ATM I'm using Software Centre as a search engine and installing via Synaptic.

---

### Post by Jetro on 2010-11-04
I get this error when trying to run Software-Center, any ideas?
```
Traceback (most recent call last):
File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 42, in <module>
    from view.viewswitcher import ViewSwitcher, ViewSwitcherList
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 34, in <module>
    from softwarecenter.backend.channel import SoftwareChannel
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 22, in <module>
    from softwarecenter.distro import get_distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 88, in <module>
    distro_instance=_get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 77, in _get_distro
    module =  __import__(distro_id, globals(), locals(), [], -1)
ImportError: No module named LinuxMint

```

Ubuntu 10.04.

---

### Post by P4man on 2010-11-04
Are you running linuxmint? It has its own software center I believe, and I dont think its compatible with ubuntu software center and vice versa.

---

### Post by Jetro on 2010-11-05
Nope! I am running Ubuntu, but I installed a/the Mint menu applet, so I can add it on the Gnome panel. I tried to remove the packages I installed to install the Mint menu, with no success.

---

### Post by eks2212 on 2010-11-16
I install ubuntu 10.10 to different PCs and Laptops. But the **Software Center **is not working at all.
How can I active this?
I use new installation several times. But same problem!
Some one plz help me!

---

### Post by Scout5950 on 2011-06-02
Is the software center not up and running ? It worked fine for me 2 days and I have made no changes. is anyone else having same trouble?

---

### Post by A N on 2011-06-12
i am new to ubuntu, just installed ubuntu 11.04 on my new laptop a few days ago
the ubuntu software centre was working perfectly well for me till yesterday, when i tried to install gparted using the terminal:
sudo apt-get install gparted

it was giving me an error and i was asked to use either the update or fix-missing command, i used the former:
sudo apt-get update

but neither the update reached its successful end after taking a long time, nor does the sw centre now download anything
from then on the software center gives me the error:** check your Internet connection**
i suppose these issues are linked, but all i want is my SW Centre working properly, also rest of the Ubuntu

i posted the same problem in another thread as well, but practised one of the tips i found here and am posting my still persistent problem here.
i tried to remove the sw center but the terminal says:

[B]E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
an@AN-Pavilion:~$ [/B]


HELP PLEASE, A.S.A.P.
I'll be really greatful

---

### Post by todreich on 2011-06-20
This worked perfectly for me. : ) Thanks!

---

