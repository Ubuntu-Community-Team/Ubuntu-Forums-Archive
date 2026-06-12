---
title: "New user, new 10.10 locks up after login"
date: 2011-01-24
forum: General Help
---

### Post by wulkenator on 2011-01-24
I am a new user and just installed Ubuntu 10.10 on an older PC along side Windows XP. Everything boots fine in Ubuntu, until I log in. At this point I just get a blank purple window. No icons or start menu or anything. I am able to log in fine in safe mode.
 
Any suggestions would be appreciated.
 
W

---

### Post by medic2000 on 2011-01-24
What is your grapic card?

---

### Post by dnguyen1963 on 2011-01-24
> **wulkenator said:**
> I am a new user and just installed Ubuntu 10.10 on an older PC along side Windows XP. Everything boots fine in Ubuntu, until I log in. At this point I just get a blank purple window. No icons or start menu or anything. I am able to log in fine in safe mode.
 
Any suggestions would be appreciated.
 
W

Stay far away from Ubuntu 10.04 or later on older computers.  Look at the thread on random freezes to see what I am talking about.  If you really want to use Linux on an old computer, use PCLinuxOS/Xfce or Ubuntu 8.04 (if you can find it - no support though).

---

### Post by JGJones on 2011-01-24
Can you try the following:

In the Login screen, click on your username. Do not enter your password just yet.

At bottom, some new texts will appear when you click on your username.

They are in order Language | Keyboard layout | Session

You want to click on the 3rd one - Session. It will say Ubuntu Desktop Edition. Change this to Ubuntu Desktop Edition (Safe Mode)

Then enter your password and log in.

Once you have logged in, if you do get a normal desktop, then please go to System in the menu and click on Preferences. Then go to Appearance.

The Appearance window will then open. Click on the Visual Effects tab and select None (this will remove any 3D effects).

(in geeky terms, if my memory serve me correctly this will make your Gnome desktop use the Metacity window manager instead of Compiz window manager. Compiz give you the 3D effects)

Then you should be able to log in normally.

Please let us know if this worked.

---

### Post by wulkenator on 2011-01-25
OK. so I tried the steps in reply #4.  It was already set to "none" for 3d graphics.  This did not help my problem.  
 
The suggestion to try a different version PCLinuxOS appealed to me so I'm going to try it.
 
I am going to try the PCLinux version in dual boot with WindowsXP.  In doing further research, here is what I'm thinking I need to do.  What are your thoughts?
 
1.  uninstall Ubuntu from the Live CD.
2.  From my WinXP disk manager, delete the Ubuntu partition.
3.  Edit the boot.ini file (delete the 2nd choice of boot options) as I don't have my WinXP disks.
 
Then I should be able to install the new version of Linux.
 
Anyone see any problems with this?  Any other suggestions?
 
THanks in advance for your help.

---

### Post by wulkenator on 2011-01-25
**Re: New user, new 10.10 locks up after login** 
OK. so I tried the steps in reply #4. It was already set to "none" for 3d graphics. This did not help my problem. 

The suggestion to try a different version PCLinuxOS appealed to me so I'm going to try it.

I am going to try the PCLinux version in dual boot with WindowsXP. In doing further research, here is what I'm thinking I need to do. What are your thoughts?

1. uninstall Ubuntu from the Live CD.
2. From my WinXP disk manager, delete the Ubuntu partition.
3. Edit the boot.ini file (delete the 2nd choice of boot options) as I don't have my WinXP disks.

Then I should be able to install the new version of Linux.

Anyone see any problems with this? Any other suggestions?

THanks in advance for your help.

---

