---
title: "no screens found after upgrade"
date: 2005-02-14
forum: General Help
---

### Post by dude2425 on 2005-02-14
I upgraded hoary about a week ago, with the 2.6.10-3 kernel, and ever since I am unable to startx with my nvidia drivers. The genaric nv drivers work fine, but the nvidia dont. I've got all the restricted kernel stuff, and all that, but it still gives me no screens found. I thought it was because something didn't get uploaded yet in the repository, but after a few days, there are no updates, and it still wont work. It worked just fine before I upgraded.

---

### Post by ollietc on 2005-02-14
Try this...

modprobe nvidia
startx

If that works, then complete the following so it will load on reboot.

Edit /etc/modules
add 'nvidia' to the end of the file. (The ' is to be left out)

---

### Post by dude2425 on 2005-02-14
The first thing I did when installing the drivers was to add nvidia to /etc/modules but it still does nothing to help. It's still there too. As I said, before I upgraded it worked just fine, but after it just doesn't like me very much.

---

### Post by dude2425 on 2005-02-19
I just tryed using the 2.8 kernel that was installed with warty and still get no screens found so I'm thinking that maybe it isn't a problem with the kernel, but a problem with something else I upgraded in hoary.

I did a "cat /root/.synaptic/log/2005-02-10* >> ~/synapticlog" to get all the logs for the first time I upgraded after reinstalling after it stoped working for me in hopes somebody would know why I'm having these problems (hope it's not too long though, I'm just desperate to play UT2004).
> Commit Log for Thu Feb 10 14:17:56 2005


Upgraded the following packages:
bug-buddy (2.9.3-0ubuntu1) to 2.9.91-0ubuntu1
evolution-webcal (2.0.1-0ubuntu1) to 2.1.91-0ubuntu2
gconf-editor (2.9.3-0ubuntu1) to 2.9.91-0ubuntu1
gstreamer0.8-doc (0.8.8-1) to 0.8.9-1
gstreamer0.8-tools (0.8.8-1) to 0.8.9-1
gthumb (3:2.6.1-3) to 3:2.6.3-1
libc6 (2.3.2.ds1-20ubuntu6) to 2.3.2.ds1-20ubuntu8
libc6-dev (2.3.2.ds1-20ubuntu6) to 2.3.2.ds1-20ubuntu8
libc6-i686 (2.3.2.ds1-20ubuntu6) to 2.3.2.ds1-20ubuntu8
libeel2-2 (2.9.90-0ubuntu4) to 2.9.91-0ubuntu1
libeel2-data (2.9.90-0ubuntu4) to 2.9.91-0ubuntu1
libgcc1 (1:4.0-0pre6ubuntu1) to 1:4.0-0pre6ubuntu3
libgnomevfs2-0 (2.9.90-0ubuntu3) to 2.9.91-0ubuntu1
libgnomevfs2-common (2.9.90-0ubuntu3) to 2.9.91-0ubuntu1
libgstreamer0.8-0 (0.8.8-1) to 0.8.9-1
libgstreamer0.8-dev (0.8.8-1) to 0.8.9-1
libnautilus-extension1 (2.9.90-0ubuntu2) to 2.9.91-0ubuntu1
libpq3 (7.4.7-1) to 7.4.7-2ubuntu1
linux-doc-2.6.10 (2.6.10-15) to 2.6.10-16
linux-headers-2.6.10-3 (2.6.10-15) to 2.6.10-16
linux-headers-2.6.10-3-686 (2.6.10-15) to 2.6.10-16
linux-image-2.6.10-3-386 (2.6.10-15) to 2.6.10-16
linux-image-2.6.10-3-686 (2.6.10-15) to 2.6.10-16
linux-patch-ubuntu-2.6.10 (2.6.10-15) to 2.6.10-16
linux-source-2.6.10 (2.6.10-15) to 2.6.10-16
linux-tree-2.6.10 (2.6.10-15) to 2.6.10-16
locales (2.3.2.ds1-20ubuntu6) to 2.3.2.ds1-20ubuntu8
nautilus (2.9.90-0ubuntu2) to 2.9.91-0ubuntu1
nautilus-data (2.9.90-0ubuntu2) to 2.9.91-0ubuntu1
popularity-contest (1.26ubuntu1) to 1.26ubuntu3
python-twisted (1.3.0-5ubuntu1) to 1.3.0-7ubuntu1
python2.3-twisted (1.3.0-5ubuntu1) to 1.3.0-7ubuntu1
python2.3-twisted-bin (1.3.0-5ubuntu1) to 1.3.0-7ubuntu1
python2.4-twisted (1.3.0-5ubuntu1) to 1.3.0-7ubuntu1
python2.4-twisted-bin (1.3.0-5ubuntu1) to 1.3.0-7ubuntu1
ubuntu-base (0.25) to 0.28
ubuntu-desktop (0.25) to 0.28
usbutils (0.70-1ubuntu1) to 0.70-1ubuntu2
xchat (2.4.1-0.1ubuntu2) to 2.4.1-0.1ubuntu3
xchat-common (2.4.1-0.1ubuntu2) to 2.4.1-0.1ubuntu3

Installed the following packages:
cabextract (1.1-1)
msttcorefonts (1.2)
ubuntu-live (0.28)
Commit Log for Thu Feb 10 14:28:04 2005


Installed the following packages:
libglib-perl (1:1.061-1)
libgnome2-canvas-perl (1.002-1)
libgnome2-perl (1.020-1)
libgnome2-vfs-perl (1.003-1)
libgtk2-perl (1:1.061-1ubuntu1)
Commit Log for Thu Feb 10 15:27:41 2005


Removed the following packages:
mozilla-tabextensions

Installed the following packages:
fb-music-high (0.1.1)
fbgetty (0.1.698-6)
fortunes (1:1.99.1-1)
frozen-bubble (1.0.0-6)
frozen-bubble-data (1.0.0-6)
geki2 (2.0.3-4)
geki3 (1.0.3-4)
gimp-data-extras (1:2.0.1-3)
gimp-gap (2.0.2-4)
gimp-svg (2.2.2-1ubuntu1)
gtkboard (0.11pre0-3)
imwheel (1.0.0pre12-2)
lg-all (107)
lg-base (107-1)
lg-issue01to08 (6-1)
lg-issue09 (5-1)
lg-issue10 (7-1)
lg-issue100 (1-1)
lg-issue101 (1-1)
lg-issue102 (1-1)
lg-issue103 (1-1)
lg-issue104 (1-1)
lg-issue105 (1-1)
lg-issue106 (1-1)
lg-issue107 (1-1)
lg-issue11 (6-1)
lg-issue12 (5-1)
lg-issue13 (5-1)
lg-issue14 (5-1)
lg-issue15 (5-1)
lg-issue16 (5-1)
lg-issue17 (6-1)
lg-issue18 (6-1)
lg-issue19 (5-1)
lg-issue20 (5-1)
lg-issue21 (6-1)
lg-issue22 (7-1)
lg-issue23 (6-1)
lg-issue24 (5-1)
lg-issue25 (6-1)
lg-issue26 (7-1)
lg-issue27 (6-1)
lg-issue28 (5-1)
lg-issue29 (4-1)
lg-issue30 (5-1)
lg-issue31 (5-1)
lg-issue32 (4-1)
lg-issue33 (4-1)
lg-issue34 (3-1)
lg-issue35 (3-1)
lg-issue36 (3-1)
lg-issue37 (3-1)
lg-issue38 (2-1)
lg-issue39 (3-1)
lg-issue40 (2-1)
lg-issue41 (3-1)
lg-issue42 (3-1)
lg-issue43 (3-1)
lg-issue44 (3-1)
lg-issue45 (3-1)
lg-issue46 (4-1)
lg-issue47 (3-1)
lg-issue48 (2-1)
lg-issue49 (2-1)
lg-issue50 (2-1)
lg-issue51 (2-1)
lg-issue52 (2-1)
lg-issue53 (2-1)
lg-issue54 (2-1)
lg-issue55 (2-1)
lg-issue56 (2-1)
lg-issue57 (2-1)
lg-issue58 (2-1)
lg-issue59 (2-1)
lg-issue60 (2-1)
lg-issue61 (2-1)
lg-issue62 (2-1)
lg-issue63 (2-1)
lg-issue64 (3-1)
lg-issue65 (2-1)
lg-issue66 (3-1)
lg-issue67 (4-1)
lg-issue68 (2-1)
lg-issue69 (2-1)
lg-issue70 (2-1)
lg-issue71 (2-1)
lg-issue72 (2-1)
lg-issue73 (2-1)
lg-issue74 (2-1)
lg-issue75 (2-1)
lg-issue76 (2-1)
lg-issue77 (2-1)
lg-issue78 (2-1)
lg-issue79 (2-1)
lg-issue80 (2-1)
lg-issue81 (2-1)
lg-issue82 (2-1)
lg-issue83 (2-1)
lg-issue84 (2-1)
lg-issue85 (1-1)
lg-issue86 (1-1)
lg-issue87 (1-2)
lg-issue88 (1-1)
lg-issue89 (1-1)
lg-issue90 (1-1)
lg-issue91 (1-2)
lg-issue92 (1-1)
lg-issue93 (1-1)
lg-issue94 (1-1)
lg-issue95 (1-1)
lg-issue96 (2-1)
lg-issue97 (2-1)
lg-issue98 (1-1)
lg-issue99 (1-1)
lg-subscription (107)
libglade-gnome0 (1:0.17-3)
libgtkextra17 (0.99.17-2.2)
libgtkextra17-dev (0.99.17-2.2)
libkxl0 (1.1.7-8)
libpvm3 (3.4.2-16)
libsdl-console (1.3-3)
libsdl-gfx1.2 (2.0.9-4)
libsdl-image1.2 (1.2.3-6)
libsdl-net1.2 (1.2.5-3)
libsdl-perl (1.20.3-1)
libsdl-ttf2.0-0 (2.0.6-5)
libsvga1 (1:1.4.3-20ubuntu2)
libtidy-dev (20040811-2)
libtidy0 (20040811-2)
libzvt2.0-0 (2.0.1cvs20021009-4)
linuxinfo (1.1.8-8)
lspowertweak (0.99.5-6)
multi-gnome-terminal (1.6.2-10)
nautilus-dbg (2.9.91-0ubuntu1)
neverball (1.4.0-1)
neverdata (1.4.0-1)
openoffice.org2 (1.9.66-0ubuntu8)
openoffice.org2-calc (1.9.66-0ubuntu8)
openoffice.org2-draw (1.9.66-0ubuntu8)
openoffice.org2-impress (1.9.66-0ubuntu8)
openoffice.org2-math (1.9.66-0ubuntu8)
openoffice.org2-writer (1.9.66-0ubuntu8)
povray-3.5 (3.5.0c-10)
povray-3.5-examples (3.5.0c-10)
povray-3.5-includes (3.5.0c-10)
powermanga (0.79-3)
powermanga-data (0.79-3)
rcalc (0.3.99-4)
tidy (20040811-2)
tidy-doc (20040810-1)
tuxracer (0.61-6.4)
tuxracer-data (0.61-2)
tuxracer-extras (0.4-1)
unrar-nonfree (3.4.3-1)
vim-gtk (1:6.3-046+1ubuntu3)
vim-scripts (5-1)
Commit Log for Thu Feb 10 15:46:28 2005


Completely removed the following packages:
gtkboard
Commit Log for Thu Feb 10 16:02:37 2005


Upgraded the following packages:
cpp-3.3 (1:3.3.5-8ubuntu1) to 1:3.3.5-8ubuntu2
g++-3.3 (1:3.3.5-8ubuntu1) to 1:3.3.5-8ubuntu2
gamin (0.0.21-0ubuntu2) to 0.0.23-0ubuntu2
gcc-3.3 (1:3.3.5-8ubuntu1) to 1:3.3.5-8ubuntu2
gcc-3.3-base (1:3.3.5-8ubuntu1) to 1:3.3.5-8ubuntu2
libgamin0 (0.0.21-0ubuntu2) to 0.0.23-0ubuntu2
libstdc++5 (1:3.3.5-8ubuntu1) to 1:3.3.5-8ubuntu2
libstdc++5-3.3-dev (1:3.3.5-8ubuntu1) to 1:3.3.5-8ubuntu2
python (2.4-0ubuntu5) to 2.4-0ubuntu6
python-examples (2.4-0ubuntu5) to 2.4-0ubuntu6
python-gdbm (2.4-0ubuntu5) to 2.4-0ubuntu6
python-minimal (2.4-0ubuntu5) to 2.4-0ubuntu6
python-tk (2.4-0ubuntu5) to 2.4-0ubuntu6
Commit Log for Thu Feb 10 17:12:05 2005


Upgraded the following packages:
gamin (0.0.23-0ubuntu2) to 0.0.23-0ubuntu3
gcc-3.4-base (3.4.3-7ubuntu1) to 3.4.3-9ubuntu1
gnome-system-tools (1.1.90-0ubuntu3) to 1.1.91-0ubuntu1
libgamin0 (0.0.23-0ubuntu2) to 0.0.23-0ubuntu3

Installed the following packages:
system-tools-backends (1.1.91-0ubuntu2)
Commit Log for Thu Feb 10 17:19:46 2005


Installed the following packages:
apt-listchanges (2.58)
apt-show-source (0.10)
apt-show-versions (0.07)
apt-src (0.25.1)
libapt-pkg-perl (0.1.13ubuntu3)
Commit Log for Thu Feb 10 17:21:43 2005


Installed the following packages:
numlockx (1.0-12)
Commit Log for Thu Feb 10 18:37:47 2005


Removed the following packages:
nvidia-glx
nvidia-glx-dev
Commit Log for Thu Feb 10 18:46:19 2005


Installed the following packages:
build-essential (10.1ubuntu1)
fakeroot (1.2.2)
g++ (4:3.3.5-1)
kernel-package (8.119ubuntu3)
libglade2-dev (1:2.5.0-0ubuntu2)
Commit Log for Thu Feb 10 19:23:30 2005


Installed the following packages:
nvidia-glx (1.0.6629-0ubuntu20)
nvidia-glx-dev (1.0.6629-0ubuntu20)
Commit Log for Thu Feb 10 19:23:56 2005


Reinstalled the following packages:
linux-restricted-modules-2.6.10-3-686 (2.6.10.3-4)
Commit Log for Thu Feb 10 19:30:57 2005


Upgraded the following packages:
ubuntu-base (0.28) to 0.29
ubuntu-desktop (0.28) to 0.29
ubuntu-live (0.28) to 0.29

Installed the following packages:
language-support-en (20050208)
mozilla-firefox-locale-en-gb (1.0lang20041216-2ubuntu1)
Commit Log for Thu Feb 10 19:33:02 2005


Installed the following packages:
joystick (20010903-2)
jscalibrator (1:1.5.0-7)
jslaunch (2.0-9)
libjsw-dev (1:1.5.0-7)
libjsw2 (1:1.5.0-7)

---

### Post by mestre on 2005-02-20
I have the same problem here!

---

### Post by mestre on 2005-02-20
I just install the linux-restricted-module package that match my kernel version. And it now works! :)

---

### Post by dude2425 on 2005-02-20
That was actually one of the first things I tried when it happened, but unfortunately it doesn't work. I've tried everything I could think of, and still no go.

---

### Post by CyrilleMortreux on 2005-02-20
Removed the following packages:
nvidia-glx
nvidia-glx-dev
Commit Log for Thu Feb 10 18:46:19 2005

You shouldn't have removed these packages. 

Try to re install them, then modprobe nvidia, and then /etc/init.d/gdm restart

You may find usefull to install the linux-restricted-modules that suits your kernel .

And try ;)

---

