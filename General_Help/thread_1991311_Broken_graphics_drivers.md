---
title: "Broken graphics drivers"
date: 2012-05-30
forum: General Help
---

### Post by tecs on 2012-05-30
Hello there,

I have a nasty problem related to Gnome and video card drivers, that I can't seem to fix. Any help will be appreciated!

[SIZE="3"]**The problem**[/SIZE]
After using the PC for some time (10+ hrs, sometimes earlier) glitches like these, but not limited to, start to appear: pages opened in chrome are black until scrolled up and down, buttons become invisible in UI throughout the whole system, some filenames dissapear from icons, edited text in gedit becomes invisible (working on HTML/PHP pages only highlighted syntax (opening and closing brackets, parenthesis and quotes) remain visible). Restarting the computer, Xorg, gnome-session or unity provide a temporary fix (10+ hrs again).

[SIZE="3"]**What I did wrong...**[/SIZE]
Because I needed the latest GIMP at the time (2.7?), I installed it from its DEV PPA, which also required some packages from Gnome 3 DEV PPA. I believe somewhere in time, an update from the G3 PPA, caused this problem.

[SIZE="3"]**How I tried to fix it**[/SIZE]
I did some research and found very limited information about my problem, which points to a bug in a video driver for Intel video cards, which apparently has a memleak. I removed the PPA and tried reinstalling Gnome and ubuntu-desktop to their stock versions , which didn't fix the problem.

Also recompiled video card drivers with a supposedly stable version. Problem persists, but time till breakdown is now extended to about 4 days. Steps taken:
```
sudo apt-get install git libtool libpciaccess-dev xutils-dev xserver-xorg-dev

mkdir git
cd git

git clone git://anongit.freedesktop.org/mesa/drm -b master
git clone git://anongit.freedesktop.org/xorg/driver/xf86-video-intel -b master

cd drm
./autogen.sh
./configure
make
sudo make install

cd ../xf86-video-intel
./autogen.sh
./configure

# src/intel_dri.c as of this version:
# http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/commit/?id=a21bdbe3e312b40b936c5c68c84f5c1bc0f9fb88
# needs modification because make fails on compile
# here is a diff

# @@ -379,7 +379,7 @@
#  }
#  
#  #else
# -
# +typedef enum { false, true } bool;
#  static DRI2Buffer2Ptr
#  I830DRI2CreateBuffer(DrawablePtr drawable, unsigned int attachment,
#  		     unsigned int format)

# in simple terms, you can add (without the # symbol):
# typedef enum { false, true } bool;
# to src/intel_dri.c on line 382

make
sudo make install

```

[SIZE="3"]**Recreating the bug**[/SIZE]
My laptop uses shared video memory and I guess filling that up causes the problem. I can successfully recreate it using `stress --vm 150 --vm-bytes 100MB --vm-hang 0` (fill up the ram). Also browsing on Chromium with lots of graphics heavy tabs and using Gimp seem to cause the problem to appear faster (help the memleak fill the ram).

[SIZE="3"]**When the bug occurs**[/SIZE]
```
Xorg.0.log is flooded with

[ 84428.555] (WW) intel(0): intel_uxa_prepare_access: bo map failed: No space left on device
[ 84428.555] (WW) intel(0): intel_uxa_prepare_access: bo map failed: No space left on device
```

```
kern.log and syslog are flooded with
[82929.434974] [drm:drm_gem_create_mmap_offset] *ERROR* failed to allocate offset for bo 0
[82929.536345] [drm:drm_gem_create_mmap_offset] *ERROR* failed to allocate offset for bo 0
```

There are no preceding errors in the logs.
Also screenshots attached below.

[SIZE="3"]**System information**[/SIZE]
Toshiba Satellite L300-11H
Intel GMA X3100
2GB RAM
12.04 LTS i686
3.2.0-24-generic
Chromium 18.0.1025.151

---

### Post by tecs on 2012-05-31
bump && new attachment

This is really hindering with my work efficiency. If can get away without a new install that would be great. Otherwise I would need a way to restore all my settings. I maintain a week back, day by day archive of backups (containing /home, /var/lib/mysql, /var/spool/cron, /etc /root, /usr/local/bin, /usr/local/sbin and the output of dpkg --get-selections) I can use to restore on a fresh install, but I am afraid that will cause the same problem again.

---

### Post by mastablasta on 2012-05-31
have you tried switching to unity 2D ? 
 
also i suggets you report a bug on launch pad since it seems to me you can reporduce it.

---

### Post by tecs on 2012-06-03
> **mastablasta said:**
> have you tried switching to unity 2D ? 
 
also i suggets you report a bug on launch pad since it seems to me you can reporduce it.

Didn't make a difference, except it took longer from boot till UI breakdown.

Is there a way to reinstall everything from Unity back to graphic card drivers to stock 12.04 versions, without affecting other settings. Problem is I have no idea which packages are affected and which versions were stable.

---

### Post by tecs on 2012-06-04
Still no suggestions?

I would happily post a bug on launchpad but I cannot really reproduce it - I can make it happen, but I cannot reproduce the circumstances in which it is possible for it to happen (eg. what I installed, in which package does it occur...)

---

### Post by traditionalist on 2012-06-04
I had  bit of  think about this.  First of all, get this;

[http://www.remastersys.com/](http://www.remastersys.com/)

Run a full backup using this and burn the result to a DVD.  You need to back up your data separately but all your settings and software are preserved.

Now you can proceed to make more backups and each time excluding something ( the program allows you to exclude things), no need to burn these, just run them from an iso in a VM.  This way you should be able to eliminate any faults. Once you have a stable system again, burn that to a DVD. You can now install the healthy system back to your machine.  It should work OK.  I have done something very similar due to faulty graphic drivers and everything worked fine.

---

### Post by Zill on 2012-06-04
> **tecs said:**
> ...Is there a way to reinstall everything from Unity back to graphic card drivers to stock 12.04 versions, without affecting other settings.
It is *possible* that you have a hardware failure that might only become apparent after things have warmed-up over a period of time.

I suggest that you try the Ubuntu 12.04 Live CD (i.e. running solely from the Live CD, not the version installed to your HDD).  Run this for a day or so and see if the problem re-occurs.  If so then it looks like your hardware is on the way out. :-(

However, if the Live CD runs OK then it looks like your software may be either buggy or corrupted and you could follow the advice given by traditionalist above.

---

### Post by tecs on 2012-06-05
> **Zill said:**
> It is *possible* that you have a hardware failure that might only become apparent after things have warmed-up over a period of time.

As I thought, my hardware is fine. I have a stable system with my CPU cores, system (?) and video card temperatures over 80degC for a prolonged time. With normal use, I rarely go over 55. I ran the Live CD just fine, while trying to force the memleak using gimp and stress.


> **Zill said:**
> However, if the Live CD runs OK then it looks like your software may be either buggy or corrupted and you could follow the advice given by traditionalist above.

I am not afraid of screwing up something and being left with system in need of reinstall, so I don't think I'll go through the hassle of backups. I just have no idea where to start from.

To redefine/clarify my question:

What would be the correct course of action to get everything Gnome 3 related, window manager, X, graphic drivers, etc. back to stock 12.04 versions?
(Without regard to backups, data loss, just-in-case scenarios and so on - I got that covered).

---

### Post by Zill on 2012-06-05
> **tecs said:**
> ...What would be the correct course of action to get everything Gnome 3 related, window manager, X, graphic drivers, etc. back to stock 12.04 versions?
(Without regard to backups, data loss, just-in-case scenarios and so on - I got that covered).
I suggest that you would find it *very* difficult, if not impossible, to return your current installation to a "stock 12.04 version".

As long as you have good backups of your *data* (i.e. your home directory), then the best way to get back to defaults is to do a full reinstall of Ubuntu 12.04.

---

### Post by dino99 on 2012-06-05
your issue is clearly a memory leak (probably with gimp); but your logs might help you know what exactly is happening (~/.xsession-errors, /var/log/)

maybe you can purge your ppa(s) then reinstall them (sudo ppa-purge ....)

---

### Post by tecs on 2012-06-05
> **dino99 said:**
> your issue is clearly a memory leak (probably with gimp); but your logs might help you know what exactly is happening (~/.xsession-errors, /var/log/)

Problem appears even if I haven't used Gimp in the current session. It can be caused from 'excessive' browsing with chromium (but not firefox), browsing my 18MP pictures with the image viewer and so on. As for the logs there's nothing new there apart from what I've posted in the first post.


> **Zill said:**
> I suggest that you would find it very difficult, if not impossible, to return your current installation to a "stock 12.04 version".

I've just found [this link]("http://comments.gmane.org/gmane.comp.freedesktop.xorg.drivers.intel/7502"), where the same problem is discussed and a presumably working solution is given:

> ...
If you checkout the master branch of both

  git://anongit.freedesktop.org/mesa/drm
and
  git://anongit.freedesktop.org/xorg/driver/xf86-video-intel

You should have a working driver.

I managed to clone both links using git but I couldn't compile them. I guess I didn't download the right version or something...

both failing miserably on autogen.sh and ./configure

Any pointers?

---

### Post by tecs on 2012-06-06
Apparently I successfully compiled and installed those packages. Will write in a couple of days to tell if it worked for good.

It might help someone, so here are the steps I made to install them:

```
sudo apt-get install git libtool libpciaccess-dev xutils-dev xserver-xorg-dev

mkdir git
cd git

git clone git://anongit.freedesktop.org/mesa/drm -b master
git clone git://anongit.freedesktop.org/xorg/driver/xf86-video-intel -b master

cd drm
./autogen.sh
./configure
make
sudo make install

cd ../xf86-video-intel
./autogen.sh
./configure

# src/intel_dri.c as of this version:
# http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/commit/?id=a21bdbe3e312b40b936c5c68c84f5c1bc0f9fb88
# needs modification because make fails on compile
# here is a diff

# @@ -379,7 +379,7 @@
#  }
#  
#  #else
# -
# +typedef enum { false, true } bool;
#  static DRI2Buffer2Ptr
#  I830DRI2CreateBuffer(DrawablePtr drawable, unsigned int attachment,
#  		     unsigned int format)

# in simple terms, you can add (without the # symbol):
# typedef enum { false, true } bool;
# to src/intel_dri.c on line 382

make
sudo make install

```

---

### Post by tecs on 2012-06-10
Already 80 hours into a continuous session and no problems whatsoever! Thanks to all of you, who helped!

Solution can be found in my previous post and will be copied to my first post for Google purposes :)

---

### Post by Zill on 2012-06-10
> **tecs said:**
> ...Solution can be found in my previous post and will be copied to my first post for Google purposes :)
I am pleased that you figured out how to resolve the problem and have updated the thread with your comprehensive info.

Many thanks.

---

### Post by tecs on 2012-06-10
Thread marked as unsolved again.

Unfortunately 7 hours after declaring the problem as fixed, it appeared again. I guess compiling my drivers helped against the memleak, but not enough. I assume the breakdown cycle is now around 4 days and when the UI falls apart it is not as severe as before.
Problem still persist though...

---

### Post by guysoft on 2012-08-02
Hey all,
**I HAVE A SOLUTION!**
Tested for a week now, prior to it after 4 days the bug would manifest. But thanks to people on #intel-gfx freenode we have workaround.

The solution is to set AccelMethod to "sna". However to day _this rendering option is only available in the git repo_, so you need to compile it. Here is a step by step instruction, and how to test that it works:

1. get the source of the drivers from git and compile it. you will need xorg's dev packages (You would be prompted if you don't have them installed at the autogen command):
```
git clone git://anongit.freedesktop.org/xorg/driver/xf86-video-intel
./autogen
make
```2. install the packages, I recommend you use checkinstall, since it would be easy to remove once thease drivers do make it in to your debain-based distro:
```
#on debian systems, better than make install, if you dont know how to use checkinstall, just use "make install"
checkinstall
```3. Now we need to set "sna" mode, so go this:
In the  "Files" Section in  /etc/X11/xorg.conf make sure you have local/lib/xorg/modules spesified like this:
```
ModulePath   "/usr/local/lib/xorg/modules,/usr/lib/xorg/modules"
```4. make sure you don't have the current intel drivers floating around:
apt-get remove xserver-xorg-video-intel

5. In the "Device" Section in /etc/X11/xorg.conf mark SNA option for rendering:
```
Option "AccelMethod" "sna"
```6. After rebooting (because you want the new driver to get loaded), you can make sure you are running on the new AccelMethod by runniung this:
```
guy@Golem2: $ grep SNA /var/log/Xorg.0.log
[    92.852] (II) intel(0): SNA compiled from 2.20.2-3-gfb38574
[    93.415] (II) intel(0): SNA initialized with Ironlake backend
```
Please confirm this works (after giving your system a few days of uptime)

---

### Post by tecs on 2012-08-12
Hello guysoft,

thanks for the insight on the issue - it is very much appreciated, as I am still experiencing this problem. I just completed the steps above successfully and will report in a few days if everything is OK (usually when working intensively the issue can come up as soon as 3hrs into a Xorg session).

My system didn't have a xorg.conf file, so I had to create one. Here's the minimal configuration I used:

```
Section "Files"
	ModulePath   "/usr/local/lib/xorg/modules,/usr/lib/xorg/modules"
EndSection

Section "Device"
	Identifier "GMA950"
	Driver "intel"
	Option "AccelMethod" "sna"
EndSection
```

This of course broke/defaulted lots of ccsm settings I had, but I'm leaving it at that until I can confirm everything is fixed.

---

### Post by tecs on 2012-08-17
```
uptime
22:26:34 up 3 days,  2:48...
```

I confirm guysoft's solution to successfully eliminate the problem. Last couple of week my system would fall apart after 3-4 hours of heavy use, now it managed 3 days of Photoshop, GIMP, Chromium with 20+ tabs and a disturbingly large number of project files open in Gedit and Bluefish without any problem.

My CCSM setting went back to normal after a restart and everything is as it was before minus the bugs :)

Thanks again for everybody's help. Thread marked as **solved**!

*Edit:*
Can't edit first post, link to solution: [http://ubuntuforums.org/showthread.php?p=12179076#post12145952](http://ubuntuforums.org/showthread.php?p=12179076#post12145952)

---

### Post by drsto on 2013-06-04
Had the same problem for a while. 

Instructions given under #16 works like a charm.

---

### Post by ryanyeah on 2013-08-08
Anyone able to help with this? I've tried the solution in this thread but after I run the autogen script, it doesn't create a Makefile properly. It creates a Makefile.in and Makefile.am but not a proper Makefile that can be used. I have make installed and run 'make' in the correct directory. Any ideas??

---

