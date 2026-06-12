---
title: "Window manager took early retirement."
date: 2011-10-16
forum: General Help
---

### Post by xeddog on 2011-10-16
I just shot myself in the foot and need a little help with the bandages.  I just finished a minor system cleanup where I used the Ubuntu Software Center to remove a couple of applications.  Eclipse is the only one that I remember, but nothing that seemed like it should be dangerous or cause any issues.  I also used "Edit Menus" to delete some dead entries in my applications menu, most of which just said something like "A Wine Application" (about 40 of them) or some such.

When I did a reboot, I am sitting there waiting and waiting for the system to finish booting when I realize it HAS finished booting.  There was no cursor on the screen, and the one window that was open on the secondary display (Gyachi) had no window decorations.  %$##%!!!

When I moved the mouse around I noticed that I could get the upper panel to drop (it's auto-hide), and I could watch the icons on it and when the "invisible" cursor was on the terminal icon I could launch a terminal window.  I don't know a whole lot about linux so I don't really know what to do to fix this.  But in the terminal window I can type "compiz &" and at least get a machine that I can work with.  The only problem seems to be that all of the desktop icons are still not being displayed any more.  I didn't have too many to start with, but they were for applications and nfs shares that I sometimes use.

The only thing that I have done is use Synaptic to re-install gdm, compiz, metacity, and emerald all to no avail.  So the questions are:  How do I fix my window manager, and how do I get my desktop icons back?


Thanks, and be gentile

Wayne

64-bit Ubuntu 10.10 Maverick
Intel I-7 processor with 6GB ram
1GB SATA disk
nVidia 9550 graphics

---

### Post by xeddog on 2011-10-17
Well, I think I have been making some progress but unfortunately it's negative progress.  I found out that if I start nautilus from a terminal window I can get my desktop icons back, so I used Synaptic to re-install nautilus.  Didn't help any.  As long as nautilus is running I have the desktop icons, but I cannot even minimize the nautilus window without losing the desktop icons again.  Also, after re-installing nautilus, when I go to Places>Home Folder and select any folder in the upper segment (Home Folder, etc.), the folder tries to open using File Roller instead of nautilus.

Wayne

---

### Post by sanderd17 on 2011-10-17
can you reinstall gnome-desktop? This should contain all default ubuntu packages.

If this doesn't help, you must have deleted some themes that you used.

---

### Post by xeddog on 2011-10-18
I re-installed the desktop and it didn't help at all.  I have found a way to get my desktop icons back, but it only works until the next boot which is daily.  I can go to Places>Computer.  In the window that opens I right-click on Filesystem>Open with other Application, and then type in "nautilus" in the custom command field.  I get a new window, but when I close it it looks like the desktop icons stay.

But I still have to do that, and I still have to manually start compiz to get window management.  I think it is time to give a fresh install of Ubuntu a serious look because I do have one more problem as well.  This one started several days before all of this other stuff.  Browser performance is really bad.  I have used both Firefox and Chrome and the problem is the same, they seem to be very slow at name resolution.  


[excrement]!!

Wayne

---

