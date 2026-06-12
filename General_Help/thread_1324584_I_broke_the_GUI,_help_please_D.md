---
title: "I broke the GUI, help please :D"
date: 2009-11-12
forum: General Help
---

### Post by SimpleFear on 2009-11-12
EDIT: SOLVED IT ON MY OWN... SORRY FOR THE THREAD.  I hate when forum newbies clog the boards with useless posts, especially on their first post.... .... haha sorry!!!
Hopefully this helps someone else...

Alright, well let me start off by apologizing for my stupidity.  Also I'm a complete newbie to linux... I was using 8.04, but I'm FAR more comfortable in Windows... Now that that is out of the way, hopefully you guys can help me out!
  
Was using 9.10 and wanted to regress to 8.10 so I could use hardware accelerated 3d with my Radeon9600.

Here is the guide so you can kind of follow along and see where I went wrong, and what I can do to fix it:
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

Followed the guide throughout, then ran into some troubles when reinstalling came.

I then reinstalled following instructions but left this off as it would not install with this added to the end:
fast-user-switch-applet=2.24.0-0ubuntu6 (I believe it said bad package or something)
I then locked the versions as it suggests through the synaptic package manager... but noticed fast-user-switch-applet wasn't installed (Because I left it off obviously)...
So when I went to install that, it said I needed GDM.  So I went to install GDM and it said it had to remove a lot and reinstall a lot so i skipped it.
I'm now guessing GDM is the theme manager that 8.10 uses that isn't compatible with 9.10???
When I tried to do the command to replace the sources.list file it wouldn't let me, it also wouldn't let me use the GUI to do so, so I'm still using the edited sources.list at the moment.

Soo like a scrub I rebooted, now all I get is the terminal.


In the terminal I attempt to sudo apt-get install gdm and get:
```
Some packages could not be installed.  This may mean that you have requested an impossible situation or if you are using the unstable distribution that sme required packages have not yet been created or been moved out of incoming.
The following info may help resolve the situation:

The following packages have unmet dependencies:
gdm: depends: libdmx1 but it is not going to be installed
depends: libglade2-0 (>1:2.6.1) but it is not going to be installed
depends: libgnomecanvas2-0(>=2.11.1)but it is not going to be installed
etc. Same message for all, I'll list the rest of the packages:
libgtk2.0-0 (>=2.14.1)
librsvg2-2 (>=2.18.1)
libxext6
libxinerama1
libxrandr2 (>2:1.2.0)
xbase-clients
gksu (>=1.0.7)
librsvg2-common
zenity
xserver-xorg

```Any way to save me?  I can use a live disk to backup my docs (52gb) but I don't have an external hdd on me at the moment so that will have to wait.

Thanks in advance for your time and help!
If I could fix this without losing my stuff that would be super!

If I can just reload my sources backup I'm sure I could just reinstall all the missing packages for 9.10 (unless the locked versions are going to mess me up) and then try again... as in, do a full backup and do a proper install of 8.10.

EDIT: when I try to replace the sources.list I get "permission denied"... derr I'm not logged in as superuser... derr I need more sleep lol...  ok used sudo to replace the sources file, and updated the package list to Karmic...  Now how do I replace all the packages and unlock the one's I've locked... which is 40 packages btw =\.

Edit: reinstalling xserver-Xorg and anything else I can... only 6 packages wouldn't upgrade, will let you know what happens next

EDIT: Have GUI back, now to go through and unlock everything :D... sorry for the thread, hopefully it helps someone else!


HOW IT WAS SOLVED:
Reinstalled the original sources.list with = sudo cp /home/user/Documents/sources.list /etc/apt/sources.list
Then used sudo apt-get update (to update package list to karmic)
Then tried to just do a basic upgrade, but wouldn't allow it SO:
sudo apt-get install xorg-server which installed all but 6 of the missing packages.
then
startx
GUI loaded without troubles... Then went to:
synaptic package manager and went through and unlocked every package that was locked (NOTE: Synaptic kept crashing, but persistence paid off!)
Then used update manager to update remaining 6 packages.
... but, shutdown/reboot functionality was lost.
So, used:
sudo apt-get install ubuntu-desktop and it installed another 6 missing files.
Now I get no signal from video card :(.

---

### Post by coldReactive on 2009-11-12
sudo apt-get install ubuntu-desktop

see if that works.

---

### Post by SimpleFear on 2009-11-12
> **coldReactive said:**
> sudo apt-get install ubuntu-desktop

see if that works.


I think I fixed it on my own here, but for future reference what does this command do???

---

### Post by coldReactive on 2009-11-12
> **SimpleFear said:**
> I think I fixed it on my own here, but for future reference what does this command do???

It installs the entire ubuntu-desktop package (gdm/gnome stuff/etc.)

By the way, make sure to tell how you solved it.

---

### Post by SimpleFear on 2009-11-12
> **coldReactive said:**
> It installs the entire ubuntu-desktop package (gdm/gnome stuff/etc.)

By the way, make sure to tell how you solved it.

Oh ok cool thanks!  I may still use this if I run into any additional problems, seems fine now though.

Added the solution to bottom of original thread.

Thanks!

EDIT: LOL I lost my restart/shutdown button.  Have to do a hard reset (not even terminal/ctrl+alt+del will shut it down)  will see if reboot helps.
UGH i lied its not fixed.  Lost videocard output :(.

On a plus I can connect to my pc from another computer and attempt to grab the files.

---

