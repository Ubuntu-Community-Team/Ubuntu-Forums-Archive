---
title: "White screen crash at login"
date: 2011-10-11
forum: General Help
---

### Post by FLCL on 2011-10-11
When I logged in the screen just froze for a second and then faded out to complete white and then to black. Restarting resulted in a busybox, so I repair it and boot again only to
have the same thing happen. Why is Ubuntu crashing as soon as I log in?

** EDIT 3: ** Well, It seems like everything keeps breaking right when it feels like I'm going to resolve it.Pretty lost at this point. Back to getting this error ```
fatal server error: could not create lock file in /tmp/.tX0-lock 
``` when I log out of a failsafe session and try to start another.

(back on live CD. chroot into mounted volume /dev/sda1) It says need read/write to purge fglrx 

```
mikado@ubuntu:~$ dpkg --force-all --purge fglrx
dpkg: operation requires read/write access to dpkg status area

```
 

**EDIT 2- most recent update**: I ran ```
 sudo dpkg-reconfigure -phigh xserver-xorg
``` under root and under my user, then I backed out to root and ran ```
 startx
``` and it loaded 80%! [SCREEN SHOT]("http://i.imgur.com/7WMgn.png"). How do we get the rest? I don't know what to do from here. So close..
         ** Sub-edit** It would appear, I was/am using fglrx drivers- at least they are on my system, determined by using ```
locate fglrx 
```
X11 Directory:
```
 app-defaults             xinit                 Xreset.d
cursors                  xkb                   Xresources
default-display-manager  xorg.conf.failsafe    Xsession
fonts                    xorg.conf.old         Xsession.d
rgb.txt                  xorg.conf.original-0  Xsession.options
X                        Xreset                Xwrapper.config 
```
  ** Sub Edit 2:**It would appear I cannot use synaptic,
```
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

W: Not using locking for read only lock file /var/lib/dpkg/lock

```
Cannot user sudo apt-get update either, cannot fetch anything although I am connected to the net (clearly)
**EDIT** Ok, making a proper post using the live cd, instead of my phone. This is to cover everything I have posted and haven't posted. 
[B]Ubuntu 10.10
ATI Radeon Mobility HD 5730
[/B]

**The issue:** When I logged in I got the White Screen of Death, following reboot I got a busybox. No prob, I fixed the busybox, but WSoD repeated on login. If I boot into normal mode, I get the WSoD and cannot drop into shell- screen goes white and when I reboot I get another busybox. 
It would seem that the file system has been stuck in read only mode.
When I used failsafeX with basic graphics mode, I received the following:
```
fatal server error: could not create lock file in /tmp/.tX0-lock
```
```
xauth: error in locking authority file /home/mikado/.Xauthority
```
```
Install problem! the configuration defaults for GNOME Power Manager have not been installed correctly. please contact your system administrator.
```

**Now:** I would have seem to been able to eliminate the xauth and fatal server errors, or at least they no longer pop up when logging in with failsafeX. 
** Last time I attempted to boot into normal mode, I did not get a white screen, but** nothing loaded, log in sound file played,  conky loaded and then disappeared leaving me with the default background image and cursor  Attempting to go into shell causes WSoD and thus a busybox. Nothing is loading once I log in. **Where do we go from here?** :confused: Please help!

---

### Post by FLCL on 2011-10-11
Update- fixed again, tried booting into limited graphics mode with fail-safe graphics mode. Dont know what happens but the only thing that loaded was my conky script and default background. No bars or anything, some message about gnome failing install but it glitched out so I couldn't read. I dropped myself into command line and logged in amd attempted to start te x server manually, which failed. 
"fatal server error: could not create lock file in /tmp/.tX0-lock"
amd "xauth: error in locking authority file /home/mikado/.Xauthority"

The hell is going on?

---

### Post by smurphy_it on 2011-10-11
Sounds like the video card driver.  Jump into a shell and issue the following command:

```
lspci | grep -i display
lsmod |grep -i video
```

Then post the contents back here.

---

### Post by FLCL on 2011-10-11
the first command returned nothing and the second returned: 
> 
uvcvideo        55943 0
videodev        43098 1 uvcvideo
v411_combat 13359 2 uvcvideo,videodev
video              18712 0
output               1883 1 video 

---

### Post by FLCL on 2011-10-11
tried to reset the driver but drive is read-only.  tried resolution found here: [http://ubuntuforums.org/showthread.php?t=917306](http://ubuntuforums.org/showthread.php?t=917306) but ran into another error > sudo: Can't open /var/lib/sudo/don/tty1: Read-only file system  :/ ran fsck on drive with -fy .

edit - can't change permissions in root prompt, tells me read only file system. Pretty sick of this at this point, worked fine until this morning :/. Is there any hope at all of salvaging this OS or did is it completely dead?

---

