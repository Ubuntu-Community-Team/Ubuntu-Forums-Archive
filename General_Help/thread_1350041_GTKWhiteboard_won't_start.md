---
title: "GTKWhiteboard won't start"
date: 2009-12-08
forum: General Help
---

### Post by jmeister67 on 2009-12-08
I'm a teacher trying to make the switch from Windows to Ubuntu. I've been experimenting with a Wii Whiteboard setup and tried GTKWhiteboard with Ubuntu 9.10. I installed it and it worked a few times. I installed another program (Whiteboard 0.3.4.2), and tried it a few times. I tried to go back to GTKWhiteboard and it just hangs without ever really starting. I tried starting it via terminal and noticed the following: ZeroDivisionError: float division. Any trouble shooting tips would be a great help. I'm definitely new to Ubuntu...please be gentle.

---

### Post by Willis77 on 2010-01-24
I'm also impressed with GTKWhiteboard and have had success with it that I have not had with others. With the other whiteboard software you mentioned, I have trouble with both calibrating and sensitivity to IR, which is too bad, because it looks pretty slick.

Anyway, I'm running GTKWhiteboard successfully on 9.04 Jaunty, and 9.10 Karmic. Although it worked at first, an upgrade broke it. After a little legwork, I've managed to solve my issues with it. In the meantime, the package has been upgraded a couple of times, so you might find a newer version just works for you.

If you wind up needing to solve the issues I did, here are the pointers:

A very good site in French that details clearly some simple, but advanced fixes:

[http://forum.ubuntu-fr.org/viewtopic.php?pid=2385177](http://forum.ubuntu-fr.org/viewtopic.php?pid=2385177)

I used Google translate, then polished it a bit to get the info below. Note that the author references gtkwhiteboard_1.3+dfsg-5_all.deb, but in Karmic, it's gtkwhiteboard_1.3+dfsg-5.1_all.deb, and there's even a gtkwhiteboard_1.3+dfsg-5.2_all.deb available for Sid.

Additionally, I had a problem because the 0.16 version of python-bluez had a bug that prevented connection for me on some machines. I therefore uninstalled 0.16, then downloaded and manually installed version 0.18  (See here: [http://code.google.com/p/pybluez/issues/detail?id=22](http://code.google.com/p/pybluez/issues/detail?id=22)) It's kind of an ugly solution (especially since I had to remove the dependency from the deb file), but it works, and when Ubuntu updates their version of python-bluez, I can fix the deb file, if there's not a new one that works by then.

Hope this helps.

--------------------------------------------
jbreizh # 35 

28/01/2009, at 06:54

Re: TBI + wiimote + ubuntu 

hello,

I'm also playing with the wiimote on Ubuntu and I also happen at the same conclusion that "wiimote whiteboard" is not very sensitive (it also consumes a lot of cpu). On the other hand, I try the python version "gtk wiimote whiteboard" and its much more effective ([http://www.stepd.ca/gtkwhiteboard/](http://www.stepd.ca/gtkwhiteboard/)). Unfortunately it is somewhat more complicated to install.  In fact there is a package for ubuntu, but there are problem dependent (libbluetooth2).  Therefore the hack. Deb for it to pass.

1) Download the package gtkwhiteboard_1.3+dfsg-5_all.deb ([http://packages.ubuntu.com/karmic/gtkwhiteboard](http://packages.ubuntu.com/karmic/gtkwhiteboard)) and put it in your "home" directory.

2) Create a folder called "gtkwhiteboard_1.3+dfsg-5" in the "home"

```
jb@furious:~$ mkdir gtkwhiteboard_1.3+dfsg-5_all
``` 

Create a folder called "DEBIAN" inside this folder.

```
jb@furious:~$ mkdir gtkwhiteboard_1.3+dfsg-5_all/DEBIAN

```

3) Unzip the. Deb files in "gtkwhiteboard_1.3+dfsg-5" 3)

```
jb@furious:~$ dpkg-deb -x gtkwhiteboard_1.3+dfsg-5_all.deb gtkwhiteboard_1.3+dfsg-5_all
jb@furious:~$ dpkg-deb -e gtkwhiteboard_1.3+dfsg-5_all.deb gtkwhiteboard_1.3+dfsg-5_all/DEBIAN
```

4) You can now edit the control file:

```
jb@furious:~$ gedit gtkwhiteboard_1.3+dfsg-5_all/DEBIAN/control

```

You have to change  libbluetooth2 (>= 3.30) to libbluetooth3 (>= 4.12)  (depends on the version on your pc. Check in synaptic) I also changed python-wxgtk2.6 to python-wxgtk2.8 to avoid reinstalling. [This is where I also removed the reference to python-bluez, since 0.16 has a bug and 0.18 doesn't register if installed manually.]

5) All you have to do now is to rebuild the package:

```
jb@furious:~$ dpkg-deb -b gtkwhiteboard_1.3+dfsg-5_all
```

6) You can install the package by double-clicking on "gtkwhiteboard_1.3+dfsg-5_all.deb" in your "home" directory

It remains to be tested. From what I've seen:

+more sensitive
+less CPU consumed
+faster (the cursor follows the pen really)
+more options (clickable area ...)

-less-accurate
-less fine-calibration interface
-one-wiimote
good day

jb

---

### Post by ingo.knito69 on 2010-08-19
had the same problem and I'think it happened when I saved strange calibrating spots. Next time when gtkwhiteboard was started these values caused a divided by zero error. I'm not a programmer but the steps below worked for me. Now I always deselect "save options on exit" when I leave gtkwhiteboard :-) 

open a terminal
sudo gedit /usr/share/gtkwhiteboard/perspective.py
search for idet = 1.0
insert following lines before that line
        a = 1
        b = 1
        c = 1
        A = 1
        D = 1
        G = 1
save
close
sudo python /usr/share/gtkwhiteboard/gtkwhiteboard.py


hope it works for you

---

### Post by Murilo_M on 2011-05-19
Hallo,

gtkwhiteboard will not start correctly if you mismatch the sequence by calibration.

open  a terminal ( ctrl+alt+T), go to the user directory and delete the file .gtkwhiteboard 

cd
rm -fr .gtkwhiteboard

and then start as usual. All calibrations were deleted

Regards,

Murilo

---

