---
title: "Where are my installed programs and why r they there?"
date: 2010-04-15
forum: General Help
---

### Post by drreed on 2010-04-15
This is getting old. Since nobody else seems to have this problem I guess it must be me.
A couple of days ago I installed something called kpdf-kde3. I didn't use it right away, but today when I tried I got the "file not found" business. So I looked on the menu, and couldn't find it. 
So I did this:

root@bt:~# apt-get install kpdf-kde3
Reading package lists... Done
Building dependency tree
Reading state information... Done
kpdf-kde3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.

root@bt:~# find / -name kpdf-kde3
/opt/kde3/lib/mime/packages/kpdf-kde3
/opt/kde3/share/doc/kpdf-kde3
/opt/kde3/share/menu/kpdf-kde3

root@bt:~# ls -l /opt/kde3/share/menu
total 28
-rw-r--r-- 1 root root  655 Mar 17  2009 kate-kde3
-rw-r--r-- 1 root root  380 Mar  2  2009 kghostview-kde3
-rw-r--r-- 1 root root  337 Mar 17  2009 klipper-kde3
-rw-r--r-- 1 root root 1242 Mar 17  2009 konqueror-kde3
-rw-r--r-- 1 root root  304 Mar  2  2009 kpdf-kde3
-rw-r--r-- 1 root root  360 Mar  2  2009 ksnapshot-kde3
-rw-r--r-- 1 root root  437 Mar  2  2009 kview-kde3

*****Note the above  are not executables****

root@bt:~# file /opt/kde3/share/menu/kpdf-kde3
/opt/kde3/share/menu/kpdf-kde3: ASCII text

****hmmm*****

root@bt:~# kate /opt/kde3/share/menu/kpdf-kde3

** Begin /opt/kde3/share/menu/kpdf-kde3 contents **

?package(kpdf):\
    needs="X11"\
    section="Applications/Viewers"\
    hints="KDE"\
    title="KPDF"\
    icon32x32="/usr/share/pixmaps/kpdf.xpm"\
    icon16x16="/usr/share/pixmaps/kpdf-16.xpm"\
    command="/**opt/kde3/bin/kpdf**"

# Icon 32x32 kpdf/cr32-app-kpdf.png kpdf.xpm
# Icon 16x16 kpdf/cr16-app-kpdf.png kpdf-16.xpm

** End  /opt/kde3/share/menu/kpdf-kde3 contents **

**Now we're getting somewhere . . .**

root@bt:~# file /opt/kde3/bin/kpdf
/opt/kde3/bin/kpdf: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped
root@bt:~#

[B]What is /opt/kde3/bin and why is it there? 
what does this mean? [/B] **section="Applications/Viewers"\**

Section of what? A menu tree? I don't have an Applications/viewers menu that is visible from the GUI. It's in Applications/Graphics. Is that a section in another configuration file somewhere?

Since that looks like a menu entry.  Inspired, I checked the menus again,( every one) until I found it in "Graphics", which I suppose sort of makes sense, but I wouldn't have put it there.
Section of what? A menu tree? I don't have an Applications/viewers menu that is visible from the GUI. It's in Applications/Graphics. Is that a section in another configuration file somewhere?


This brings me to part B of this frustrating post!

I'm getting tired of concatenating my $PATH env variable every time I run into this. I really need a persistent $PATH like I used to be able to set in .profile, which also doesn't seem to work the way I think it should.

I've searched for solutions to this and found several ways to do it, and all of them seem (to me) to make this a lot more difficult than it should be.

Could someone tell me a fast, simple way to add a directory to my path that my shell will remember every time I login.

There may be more hidden program directories here than this one. :(


*** Found this ***

Part B was solved by editing /etc/environment, not .profile
Now I can run any of those programs from the console.

I'd still like to know why those files are in a tree called /opt, and why the install renamed the executables by dropping the "-kde3" suffix.

---

