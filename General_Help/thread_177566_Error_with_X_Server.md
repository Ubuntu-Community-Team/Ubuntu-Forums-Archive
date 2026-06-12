---
title: "Error with X Server"
date: 2006-05-16
forum: General Help
---

### Post by csshuckster on 2006-05-16
I am installing Ubuntu 5.10 on a COMPAQ Presarion V5000 laptop. I have all the requirements to run 5.10, but I am getting this error when the CD is installing:

**[COLOR="DarkRed"]"Failed to start the X server (your graphical interface). It is likely it is not set up correctly. Would you like to view the X server output to diagnose the problem?"[/COLOR]**

When I do that... I get this screen:

[B][COLOR="DarkRed"]"X Window System version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating Syatem: Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
Before reporting any problems, check [http://wiki.x.org](http://wiki.x.org) to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time Tue May 16 11:24:38 2006
(==) using config file: /etc/X11/xorg.conf"
Skipping
"/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o": No symbols found
Skipping
"/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o": No symbols found
Skipping
"/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o": No symbols found
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o": No symbols found
(EE) RADEON(0): [dri] DRIScreenInit failed. Disabling DRI.

*** If unresolved symbols were reported above, they might not
*** be the reason for the server aborting.

Fatal server error:
Caught signal 4. Server aborting

Please consult the The X.Org Foundation support 
at [http://wiki.X.Org](http://wiki.X.Org) for help.

Please also check the log file at "/var/log/Xorg.0.log" for additional information.[/COLOR][/B]

Now... my problem is... I have no clue what all this means, so, is there anyone that could guide me in the right direction? Thanks in advance!

---

### Post by eggmanpete on 2006-05-16
can you post the contents of the x server config file please.
it is done from the command line by:
> cd /etc/X11
and then
> nano xorg.conf
you can miss out anything that has a hash (#) infront of it as they are comments.

---

### Post by csshuckster on 2006-05-16
Turns out there was no xorg.conf file. So I guess my next question is, where do I go from here? :-|

---

### Post by Argent on 2006-05-16
ignoring that last post, 
> sudo nano /etc/X11/xorg.conf
then enter your password, and find where it says
> driver: "ati"
to 
> driver: "vesa"
I don't entirely understand it (I'm probably more of a noob than you are), so you might be having a bigger problem, but basically the ubuntu ati video card drivers are a bit screwy. Same way for other linux distributions, from what I hear.
I had the same problem. Hope I could help!

---

### Post by csshuckster on 2006-05-17
I'm told to restart GDM when ready.

After I click out from the error screen, the computer locks up it seems when checking the battery state.

](*,) 

How do I get into the terminal, through linux, to start running all these commands to try and get this fixed and get the right driver?

I have the Radeon Xpress 200M Card driver version 8.202.0.0

---

### Post by csshuckster on 2006-05-17
OK, got into the terminal somehow and did everything that was posted but nothing happened, so I went to this thread: [http://www.ubuntuforums.org/showthread.php?t=171565](http://www.ubuntuforums.org/showthread.php?t=171565) and I am following that for now.

---

### Post by mjziegle on 2006-05-17
When you are in the terminal run 

sudo apt-get install xorg-driver-fglrx

then run 

dpkg-reconfigure xserver-xorg
select fglrx from the list

The problem is that the default xserver driver for ATI doesn't know about the R200 version in your laptop.  The easiest solution is to install the ati proprietary driver which is mentioned above.

Or update the whole distribution with

sudo apt-get dist-upgrade

This will get you the free ati driver version which works with the R200 natively.

Had this problem with my laptop and desktop which both had R200s.  It's not a big deal.  It's fixed by default with newest build of dapper.

To get to the terminal push alt-ctrl-f2.  It's unlikely you don't have /etc/X11/xorg.conf on your system since one is installed by default.

By the way.  That thread is garbage.  Compiling your own driver is a very bad idea.  That ati installer puts garbage all over your system and is impossible to uninstall.  Whenever possible use the packages in the archives.  They are designed to be easily installed and removed and upgraded.  Plus it's a heck of a lot less complicated.

Good Luck,

Matt

---

