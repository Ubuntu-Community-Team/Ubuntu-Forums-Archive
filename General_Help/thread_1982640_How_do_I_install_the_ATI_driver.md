---
title: "How do I install the ATI driver?"
date: 2012-05-18
forum: General Help
---

### Post by QIII on 2012-05-18
"[B]The author of this post has edited and moved this material to the the BinaryDriverHowto/ATI Community Help Wiki at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

This thread will no longer be monitored by the author, who asks that you refer to the Wiki and create new posts in the appropriate forum if you need further assistance.[/B]"

This has been asked a lot, and I have answered a lot, so I figured it was worth a central post for me to refer people to.  Remember, this is what I have found to work and your mileage may vary.

Just a bit of set up. 

For several years, every fourth and tenth month, Canonical has received the xx.4 and xx.10 drivers for inclusion in the Ubuntu repos during the final Beta testing phase -- before the driver is presented for public consumption.  Phoronix has been publishing irritated articles since about 2009 every time this happens.  "Ubuntu gets the candy" sort of thing.

I have heard that soon the intermediate updates will be available during non-release months, but that is hearsay and I can't speak for Canonical.  I'll wait and see and update as necessary.

Please note that the following is for the time-of-release version.  There is a "post-release-updates" version, which I suspect will be the one that will update as ATI releases new drivers, but I am not certain.  I do know that as I have experimented with the "post-release-updates" version, I have found myself unable to start Catalyst Control Center.  That just may be unique to my situation.

You should first try to install the driver using the graphical Additional Drivers method.  However, for some users the graphical installation method has proven to be  problematic.  I don't use it anyway, choosing instead to do it via the  command line.  This is what I do for the normal time-of-release version.   It completely avoids the complicated, and often vain, process of  trying to install the driver manually from AMD's website.

(***Note: this method will**** not work*** for these [legacy cards]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx") and the legacy driver for them will not work with xserver.  If you have one of these cards, you will have to use the default open source driver or purchase a different card.)

(***Note:***  There are a couple of posters I have been working with whose integrated graphics are not behaving as expected:  The reported model is incorrect and/or acceleration is not working properly.  The operation of integrated graphics can be somewhat dependent on how the motherboard has been configured by the OEM.  If you have an integrated graphics chip and this does not work, please add a comment to this thread and PM me to say it is there. In your post (not in the PM), please describe the OEM and model/version of the mobo as well as the model/version of the graphics chip.  If I start to see a pattern, I may be able to do some more detailed research. ***DO NOT*** ask for help in the PM.  I delete PM requests for help.  Nobody else gets to learn from communications behind closed doors.)

(***Note**:  *If your machine has **hybrid Intel/AMD switchable graphics**, please consult the thread [here]("http://ubuntuforums.org/showthread.php?t=1930450") first.)

1.  Save backup copy of xorg.conf in case this doesn't work.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
```2.  Remove/purge current fglrx and fglrx-amdcccle  *(If you have used a method outside of aptitude, apt, Software Center or Synaptic, follow the other party's instructions for removal.)*
```
sudo apt-get remove --purge fglrx*
``` 3.  Reboot

4. Install lthe driver.
 ```
sudo apt-get install fglrx fglrx-amdcccle
```5.  Generate a fresh xorg.conf BEFORE REBOOTING!
```
sudo aticonfig --initial
```6.  Reboot again.

If you cannot get the Catalyst Control Center to launch, try from the terminal:
```
sudo amdcccle
```To get hardware acceleration, you need to add four more packages. *** Please note*** that this has been problematic for some users who have hybrid Intel/ATI switchable graphics, so please only do this if you do not have hybrid graphics.  I am currently reviewing how to make this work in that case.

```
sudo apt-get install xvba-va-driver libva-glx1 libva-egl1  vainfo
```*(**Update June 19, 2012: ** it seems that for at least two users, the 64-bit version of libva-egl1 did not install because it could not be found.  If you get a message that no install candidate is found, please install the .deb from [here]("https://launchpad.net/ubuntu/+source/libva/1.0.15-4/+build/3368543") and then install the other three.  If you are running a 32 bit system and encounter this problem, please leave a post and I will make an update.)*

You can test to see if you have installed them correctly thus:

```
sudo vainfo
```When installed correctly, you should get the following:

```
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD

```(***June 19, 2012, ******Update with regard to fglrx-updates****:   I attempted to install the fglrx-updates and fglrx-amdcccle-updates  packages again.  Although the packages installed, the AMD development branch  was still 8.960, which is the 12.4 driver found in the Ubuntu 12.04 repo  at the time of release.  I was able to get CCC to work, but I had to  fully qualify the path in the command line:  *

```
gksudo /usr/lib/fglrx/bin/amdcccle
```[I] After uninstalling the "-updates" versions and reinstalling the "normal" packages, I was still unable to run 
[/I] 
```
gksudo amdcccle
```* and had to use the fully qualified path.  Bear this in mind if you choose to install fglrx-updates and fglrx-amdcccle-updates and cannot get CCC to run.)*

---

### Post by Face-Ache on 2012-05-19
Hi QIII, thank you for posting this detailed 'How to'.

I have a couple of questions if you don't mind. I am using Ubuntu 11.10.

I installed my ATI driver via the 'Additional Drivers' GUI in the Dash. I had two options, "ATI/AMD proprietary FGLRX graphics driver", and "ATI/AMD proprietary FGLRX graphics driver (post-release-updates)"

I currently have just the "ATI/AMD proprietary FGLRX graphics driver" driver installed. Is the post-release-updates one a stand-alone package, or should it be installed along with the "ATI/AMD proprietary FGLRX graphics driver" one?

The reason i ask, is because i never seem to be able to install the post-release-updates one (it always fails), even after i have removed the one that just says "ATI/AMD proprietary FGLRX graphics driver".

I seem to have some issues at times with my display going haywire when i Alt-Tab to switch between windows, and it's becoming quite annoying (often it locks up my whole system, and i have to reset it via the power button!). So i am wondering if there is some way in which i can update these drivers to hopefully resolve this issue?

Would appreciate any advice that you can give me on this problem.

My graphics card is an ATI Radeon HD 5450.

Many thanks.

---

### Post by kolinab on 2012-05-19
Nice Howto.

One suggestion you didn't ask for: I think this thread would have a higher profile if the subject line were changed. Right now the subject line "How do I install the ATI Driver?" leads me to think I am about to find an unsolved question, not a howto. 

Maybe I'm just being pedantic.

---

### Post by QIII on 2012-05-19
@Face-Ache: I modified the text to make your question more clear.

@kolinab:  The subject is intended to model the sort of search terms someone with a question might use.

---

### Post by kolinab on 2012-05-19
Yeah, you're right about the subject line - it does work both ways. Why didn't I think of that? :)

---

### Post by Face-Ache on 2012-05-20
Thanks QIII. I did everything in your post, and after i reboot and continue with the remaining steps, i get;
```
chris@chris-ubuntu:~$ sudo apt-get install xvba-va-driver libva-glx1 libva-egl1  vainfo
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libva-egl1
chris@chris-ubuntu:~$ sudo vainfo
sudo: vainfo: command not found
```

Any ideas?

---

### Post by Zvlwab on 2012-05-21
This didn't work for me either:
```
sudo apt-get install fglrx fglrx-amdcccle
```

But this worked like a charm:
```
sudo apt-get install fglrx-updates
```

---

### Post by QIII on 2012-05-21
@Face-Ache -  Do you have the universe and multiverse repos enabled?

---

### Post by QIII on 2012-05-21
> **Zvlwab said:**
> This didn't work for me either:
```
sudo apt-get install fglrx fglrx-amdcccle
```


Did you get any error messages?

---

### Post by Zvlwab on 2012-05-21
> **QIII said:**
> Did you get any error messages?

I don't really know anymore, everything was laggy.
Did you try ```
sudo apt-get install fglrx-updates
```

---

### Post by Face-Ache on 2012-05-21
> **QIII said:**
> @Face-Ache -  Do you have the universe and multiverse repos enabled?

Yep, i do;

---

### Post by QIII on 2012-05-21
@Zvlwab

Yes.  Please see original post.

I've been at this computer thing for a day or two.

---

### Post by QIII on 2012-05-21
@Face-Ache

On my cell phone on the Pacific Coast goofing off.  No wi-fi so I can't SSH back home.  I'm wondering if libva-egl1 is in the Oneiric repo.  May not be.

Give me a day to find out.

Edit:  Got enough 3G to check.  libva-egl1 is in the libva package.  I'll have to figure out why you are not getting it.

---

### Post by Face-Ache on 2012-05-22
It's okay QIII, it seems to be sorted out now.

I was frequently getting the thing where my display went haywire whenever i tried to alt-tab between open apps, whether Compiz was running or not - which told me it wasn't related to the Compiz install. It was becoming an issue for me, as i'm so used to switching apps that way - i just couldn't break the habit.

I suspect the haywire issue was *possibly* in relation to the Screenlets i had running, but i wasn't too sure.

So i thought it was time for me to upgrade to 12.04. As you can see, it didn't go so smoothly (initially at least anyway);
[http://ubuntuforums.org/showthread.php?p=11957520#post11957520](http://ubuntuforums.org/showthread.php?p=11957520#post11957520)

So, moving on from that embarrassment, i followed the steps in your original post in this thread, and it all went smoothly; libva-egl1 installed without issue, and 'sudo vainfo' gave pretty much the exact same result as you posted.

Once i'd installed the drivers as per your post, all my initial problems of Cairo Dock disappearing etc, were resolved.

Thanks again for your help here QIII. Very much appreciated - you're *The Man *:D

(as an aside, the alt-tab issue seems to be totally resolved in 12.04 - been thoroughly testing it, and it looks like it's now all good).

---

### Post by samwillc on 2012-05-27
A huge thanks to [QIII]("http://ubuntuforums.org/member.php?u=628170") and [[COLOR=#97310e]**coffeecat**[/COLOR]]("http://ubuntuforums.org/member.php?u=129087") for setting me on the right path with the ati card. Ditched the nvidia and went back to the radeon HD5450.

Can I ask, will this method keep the drivers updated should new ones come out?

Sam.

---

### Post by chome4 on 2012-05-30
Followed everything up to reboot. Then I got:

Signal out of range

H: 74.9KHz   V:59.9Hz

Mode should be below...

1280 x 1024 75Hz

and no way of getting back to my desktop!

---

### Post by Bucky Ball on 2012-05-30
> **kolinab said:**
> ... "How do I install the ATI Driver?" leads me to think I am about to find an unsolved question, not a howto. 



It should be: 'HOWTO: Install ATI Drivers' and in the 'Tutorials and Tips' section as it is a HOWTO/tutorial. The title is misleading. ;)

---

### Post by traditionalist on 2012-05-30
I have an ATI Radeon HD 5800 series card.  I have managed to install the drivers and catalyst a few times using various methods but each time it only runs for a while and then fails catastrophically.  However, I thought, "nothing ventured, nothing gained", and tried this method.  I have just tried it three times with the same result, it works after a fashion but catalyst is not installed and after login I get a screen of coloured garble.

This is catastrophic for a newbie as he has no idea how to recover, ( I know,it happened to me loads of times and each time I had to reinstall the complete system new).

 I am going to reinstall again now and log the procedure as well as I can.  I really would like to have my card working properly, the generic drivers do work after a fashion but with a few problems. Getting the proper drivers to work properly would be a major bonus.  But this has not worked yet.

---

### Post by traditionalist on 2012-05-30
This time it appears to have worked. After I used the command sequence for an update posted by zvlwab;

```
sudo apt-get install fglrx-updates
```

This is what happened; 

```
mike@mike-P55A-UD7:~$ sudo apt-get install fglrx-updates
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fglrx-amdcccle-updates
The following packages will be REMOVED:
  fglrx fglrx-amdcccle
The following NEW packages will be installed:
  fglrx-amdcccle-updates fglrx-updates
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 72.5 MB of archives.
After this operation, 9,216 B disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/restricted fglrx-updates amd64 2:8.960-0ubuntu1 [66.6 MB]
11% [1 fglrx-updates 8,236 kB/66.6 MB 12%]                    366 kB/s 2min 55s^Cmike@mike-P55A-UD7:~$ sudo apt-get install fglrx-updates
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fglrx-amdcccle-updates
The following packages will be REMOVED:
  fglrx fglrx-amdcccle
The following NEW packages will be installed:
  fglrx-amdcccle-updates fglrx-updates
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 72.5 MB of archives.
After this operation, 9,216 B disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/restricted fglrx-updates amd64 2:8.960-0ubuntu1 [66.6 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/restricted fglrx-amdcccle-updates amd64 2:8.960-0ubuntu1 [5,924 kB]
Fetched 64.2 MB in 2min 55s (365 kB/s)                                         
(Reading database ... 247064 files and directories currently installed.)
Removing fglrx-amdcccle ...
dpkg: fglrx: dependency problems, but removing anyway as you requested:
 xvba-va-driver depends on fglrx-driver (>= 1:10-9) | fglrx (>= 2:8.840) | fglrx-updates (>= 2:8.840); however:
  Package fglrx-driver is not installed.
  Package fglrx is to be removed.
  Package fglrx-updates is not installed.
 xvba-va-driver depends on fglrx-driver (>= 1:10-9) | fglrx (>= 2:8.840) | fglrx-updates (>= 2:8.840); however:
  Package fglrx-driver is not installed.
  Package fglrx is to be removed.
  Package fglrx-updates is not installed.
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package fglrx-updates.
(Reading database ... 246794 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.960-0ubuntu1_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx-updates (2:8.960-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.960 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-24-generic
Building for architecture x86_64
Building initial module for 3.2.0-24-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-24-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package fglrx-amdcccle-updates.
(Reading database ... 247022 files and directories currently installed.)
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.960-0ubuntu1_amd64.deb) ...
Setting up fglrx-amdcccle-updates (2:8.960-0ubuntu1) ...
mike@mike-P55A-UD7:~$ ^C
mike@mike-P55A-UD7:~$ 

```

It has never done anything like that before so it may have actually worked.  I am going to reboot now and check.

---

### Post by traditionalist on 2012-05-30
It has lost all settings, the screen is a coloured garble and the catalyst control centre is no longer there.

So, though it appears to work, it does not in fact work.  Catalyst has disappeared altogether;

```
mike@mike-P55A-UD7:~$ sudo amdcccle
[sudo] password for mike: 
sudo: amdcccle: command not found
mike@mike-P55A-UD7:~$ ^C
mike@mike-P55A-UD7:~$ 


```the main screen is a garble of colour and various windows, and my second monitor no longer works.

EDIT: This is what it looks like; ( I took a photo );  [[IMG]http://img163.imageshack.us/img163/8392/pict0001wu.th.jpg[/IMG]](http://img163.imageshack.us/i/pict0001wu.jpg/)

I will now reinstall the generic drivers by reinstalling the whole system. I have done this numerous times now because of these problems, and even getting the generic drivers to work properly initially took a long time and a great deal of frustration. They don't work properly, there are odd effects, but at least they are stable.

---

### Post by traditionalist on 2012-05-30
Tried a few things before reinstalling. 

```
mike@mike-P55A-UD7:~$ sudo apt-get install fglrx-updates
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fglrx-updates is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mike@mike-P55A-UD7:~$ ^C
mike@mike-P55A-UD7:~$ 


```

```
mike@mike-P55A-UD7:~$ sudo amdcccle [sudo] password for mike:  sudo: amdcccle: command not found mike@mike-P55A-UD7:~$ ^C mike@mike-P55A-UD7:~$
```

so, back to reinstalling everything again....................

---

### Post by traditionalist on 2012-05-30
Ran it again after reinstalling;

```
mike@mike-P55A-UD7:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
[sudo] password for mike: 
mike@mike-P55A-UD7:~$ sudo apt-get remove --purge fglrx*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'xorg-driver-fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-kernel-source' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle-updates' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-driver-dev' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-updates' for regex 'fglrx*'
Note, selecting 'fglrx-control-qt2' for regex 'fglrx*'
Note, selecting 'fglrx-updates-dev' for regex 'fglrx*'
Note, selecting 'fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-glx' for regex 'fglrx*'
Note, selecting 'fglrx-modaliases' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx*'
Note, selecting 'fglrx-driver' for regex 'fglrx*'
Note, selecting 'fglrx-control' for regex 'fglrx*'
Package fglrx-amdcccle is not installed, so not removed
Package fglrx-dev is not installed, so not removed
Package fglrx-updates-dev is not installed, so not removed
The following package was automatically installed and is no longer required:
  lib32gcc1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  fglrx* fglrx-amdcccle-updates* fglrx-updates* xvba-va-driver*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 221 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 247064 files and directories currently installed.)
Removing xvba-va-driver ...
Removing fglrx ...
Purging configuration files for fglrx ...
update-initramfs: deferring update (trigger activated)
update-rc.d: /etc/init.d/atieventsd exists during rc.d purge (use -f to force)
dpkg: error processing fglrx (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing fglrx-amdcccle-updates ...
Removing fglrx-updates ...
Removing all DKMS Modules
Done.
update-alternatives: warning: alternative /usr/lib/fglrx/ld.so.conf (part of link group x86_64-linux-gnu_gl_conf) doesn't exist. Removing from list of alternatives.
update-alternatives: warning: alternative /usr/lib/pxpress/ld.so.conf (part of link group x86_64-linux-gnu_gl_conf) doesn't exist. Removing from list of alternatives.
update-alternatives: warning: /etc/alternatives/x86_64-linux-gnu_gl_conf is dangling, it will be updated with best choice.
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: warning: alternative /usr/lib/fglrx/alt_ld.so.conf (part of link group i386-linux-gnu_gl_conf) doesn't exist. Removing from list of alternatives.
update-alternatives: warning: alternative /usr/lib/pxpress/alt_ld.so.conf (part of link group i386-linux-gnu_gl_conf) doesn't exist. Removing from list of alternatives.
update-alternatives: warning: /etc/alternatives/i386-linux-gnu_gl_conf is dangling, it will be updated with best choice.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-initramfs: deferring update (trigger activated)
Purging configuration files for fglrx-updates ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
mike@mike-P55A-UD7:~$ sudo apt-get install fglrx fglrx-amdcccle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  fglrx fglrx-amdcccle
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 72.5 MB of archives.
After this operation, 220 MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/restricted fglrx amd64 2:8.960-0ubuntu1 [66.6 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/restricted fglrx-amdcccle amd64 2:8.960-0ubuntu1 [5,924 kB]
Fetched 72.5 MB in 3min 18s (365 kB/s)                                         
Selecting previously unselected package fglrx.
(Reading database ... 246782 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.960-0ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.960-0ubuntu1_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx (2:8.960-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.960 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-24-generic
Building for architecture x86_64
Building initial module for 3.2.0-24-generic
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-24-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle (2:8.960-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
mike@mike-P55A-UD7:~$ 

```

Catalyst is there;

[[IMG]http://img137.imageshack.us/img137/2221/workspace1001c.th.png[/IMG]](http://img137.imageshack.us/i/workspace1001c.png/)

Set up, and now rebooting;

---

### Post by traditionalist on 2012-05-30
Result;

[[IMG]http://img710.imageshack.us/img710/753/pict0003mr.th.jpg[/IMG]](http://img710.imageshack.us/i/pict0003mr.jpg/)

conclusion;  I am just wasting my time because the drivers don't work for my card.

---

### Post by QIII on 2012-05-30
Chome4:  What is the model of your card?

Traditionalist:  it is odd that your dock seems relatively unscathed.  I'll look in to that.

BuckyBall:  I actually titled it exactly as most people would google it...

---

### Post by traditionalist on 2012-05-30
Reinstalled the system. Nothing else installed, just the generic drivers.  Set up dual monitors using system settings.

Result, works and is stable but with some odd effects, and is nowhere near as fast as it should be;

[[IMG]http://img28.imageshack.us/img28/6030/workspace1001z.th.png[/IMG]](http://img28.imageshack.us/i/workspace1001z.png/)

---

### Post by traditionalist on 2012-05-30
> **QIII said:**
> Chome4:  What is the model of your card?

Traditionalist:  it is odd that your dock seems relatively unscathed.  I'll look in to that.

BuckyBall:  I actually titled it exactly as most people would google it...

It's a Sapphire Radeon HD 5800 series.

---

### Post by traditionalist on 2012-05-30
Just as a matter of interest, this very nearly put me off trying to use Ubuntu at all. I just kept getting system crashes with no chance of recovery because I simply did not know how to do it.  I got to the point I am presently at as a result of extremely extensive trial and error. I reinstalled the complete system at least forty times in the first week. Not such a bad thing for me as it happens, as I learned a very great deal in a short time as a direct result of it. However, no "normal" user has either the time or the inclination to mess about like this.

Now I would rather throw the card away, ( although it is quite new and was expensive) than do without Ubuntu. But I can well imagine the vast majority of newbies simply giving up in disgust. This is my third week of using Ubuntu, and there is no way you will get it away from me now, I think it is marvelous. But I also now think that ATI stinks.

As soon as I find a card that runs reliably with Ubuntu, this one is either going in the bin, or to some Lucky Windows Seven user ( where it works perfectly well).

I am a VERY experienced computer technician, and if I was close to giving up, somebody with very little knowledge or experience is going to be tearing their hair out and cursing Ubuntu with  a vengeance. Although the problem is quite obviously with the ATI drivers.  The exact same system runs perfectly well ( albeit rather slowly) on an old "el cheapo" box I have sitting here with integrated Intel Graphics and a Celeron processor.

ATI needs to get their act together on this. When their own drivers do not function on their high end cards it is a very sad state of affairs. It also reflects extremely badly ( if unjustly) on Ubuntu.

Obviously you have gone to some lengths here to provide "fixes", but the only result for people having problems like this is that they give up because the fixes do not work. They can not do so if the drivers are faulty, which they obviously are.

---

### Post by traditionalist on 2012-05-30
Deleted, double post

---

### Post by QIII on 2012-05-30
You don't know that it is the vast majority.  You are basing that on a few examples here, which is a place where people come when they are having problems.  People don't come to help forums when things go right.  This is called "referral bias" and conclusions drawn are invalid because of that.  It cannot be said that the evidence we have indicates that there is a systemic problem with AMD/ATI drivers.  People have problems they present here with NVIDIA drivers, too.  Furthermore, I use 58xx and 69xx series cards on several machines.  (Also an old 42xx card.)

Don't get me wrong.  I understand this is a big problem for you and this should not have been such a pain.  You are rightfully frustrated.  I would be.

But remember that there are also Windows help forums aplenty.  That does not mean the vast majority of Windows users encounter problems.

Yes, this should be sorted out and I will try to do what I can.  Perhaps in doing so we will each learn something we can pass back up the line for future improvement.

Since you said you had tried various methods (direct download from AMD?) it may be something completely divorced from Ubuntu itself.  For instance, have you tried disabling integrated graphics if you mobo has such and allows it to be disabled?  I did that on my GA 890 FXA UD7.  (And I'd love to throw that stupid Silent Pipe in the trash!)

---

### Post by traditionalist on 2012-05-30
> **QIII said:**
> You don't know that it is the vast majority.  You are basing that on a few examples here, which is a place where people come when they are having problems.  People don't come to help forums when things go right.  This is called "referral bias" and conclusions drawn are invalid because of that.  It cannot be said that the evidence we have indicates that there is a systemic problem with AMD/ATI drivers.  People have problems they present here with NVIDIA drivers, too.  Furthermore, I use 58xx and 69xx series cards on several machines.  (Also an old 42xx card.)

Don't get me wrong.  I understand this is a big problem for you and this should not have been such a pain.  You are rightfully frustrated.  I would be.

But remember that there are also Windows help forums aplenty.  That does not mean the vast majority of Windows users encounter problems.

Yes, this should be sorted out and I will try to do what I can.  Perhaps in doing so we will each learn something we can pass back up the line for future improvement.

Since you said you had tried various methods (direct download from AMD?) it may be something completely divorced from Ubuntu itself.  For instance, have you tried disabling integrated graphics if you mobo has such and allows it to be disabled?  I did that on my GA 890 FXA UD7.  (And I'd love to throw that stupid Silent Pipe in the trash!)

Indeed you are of course correct on the subject of referral bias.  However, I thought I made it clear I was referring to the "vast majority"  of those who were having problems, not the "vast majority overall".

As far as I am aware I tried all the available methods without success, including direct downloads from AMD, coupled with the sustained and agonising perusal of unbelievable amounts of pure and completely useless bumpf, all based on the assumption that I must be doing something wrong.  Of course it was all pointless and the frustration and waste of time and effort due simply to the fact that the drivers do not work on my machine with this ATI card even when successfully installed.

I am not particularly frustrated, merely disappointed that the card does not work as advertised in this situation. It works perfectly well on Windows 7.

I am a qualified engineer and have been involved with electronics and  computers professionally for most of my adult life. I am now retired,  and I don't actually "need" any of this stuff any more, but I like to  know that what I have is functioning in an optimal manner.

This is my motherboard on my main machine;

[http://www.gigabyte.us/products/product-page.aspx?pid=3324#ov](http://www.gigabyte.us/products/product-page.aspx?pid=3324#ov)

I did throw the silent pipe in the trash! :)

[[IMG]http://img831.imageshack.us/img831/5193/pict0004zn.th.jpg[/IMG]]("http://img831.imageshack.us/i/pict0004zn.jpg/")

I use this;

[http://www.arctic.ac/en/p/cooling/cpu/4/freezer-7-pro-rev.-2.html](http://www.arctic.ac/en/p/cooling/cpu/4/freezer-7-pro-rev.-2.html)

---

### Post by QIII on 2012-06-01
Traditionalist -

Just a quick check in to let you know I haven't forgotten about you.  Still looking for an answer to this issue.

---

### Post by traditionalist on 2012-06-01
> **QIII said:**
> Traditionalist -

Just a quick check in to let you know I haven't forgotten about you.  Still looking for an answer to this issue.

Thank you, that is most considerate of you.  For the moment the system is running stable and well using the generic drivers.  There are a few quirks, but nothing critical.

---

### Post by idiotprogrammer on 2012-06-08
I just wanted to throw out that I've been getting lots of random crashes on 12.04 with my Radeon 2600HD card. 

Using the utility in SYSTEM SETTINGS, i was able to load the proprietary FGLRX driver, but not the post-release update. The log files show that it wasn't able to find it.  

And I get random fatal crashes about  once per day (I describe it in this thread: [http://ubuntuforums.org/showthread.php?t=1997103](http://ubuntuforums.org/showthread.php?t=1997103) ) 

Annoying as hell. I love the latest ubuntu except for the fact that it crashes more often than Windows ME or Windows 95. 

Although I play some videos, I don't make heavy use of multimedia on this machine. I'm wondering: what would be a good strategy for managing this problem: 

a)disable compiz? b)disable unity? c)uninstall the proprietary driver or d)all of the above or e)just wait a month or so for the Ubuntu people to fix Compiz/Unity stuff and wait for the problem to go away? 

How does the free driver compare to the proprietary driver in terms of stability? in terms of long term support?

---

### Post by QIII on 2012-06-08
The open source driver is, and will probably remain, stable.  Those who develop it do a commendable job of engineering into what is generally a black box.  They should be commended.  However, the open source driver does not provide the full features of the proprietary driver.  It works well and serves its users well.

Traditionalist is having problems with his card and the proprietary driver.  Search as I might, I have not been able to find anything that exactly fits his issue so I can't offer a recommendation for him.

However, it is a hasty generalization to say that his problem and yours and 100 others indicates a universal problem.  For millions of users things work right.  We don't see them here because they don't come here seeking an answer for why things are working right.

In my post I mention that the graphical install method does not work for some users.  If you used that method and are having a problem, you may be in that group.

Give the command line method I describe and leave some feedback, please.

Is your GPU integrated in the motherboard?

---

### Post by bbemmerful on 2012-06-10
Thankyou! for taking the time to make this tutorial.

---

### Post by Bucky Ball on 2012-06-10
> **QIII said:**
> @Face-Ache -  Do you have the universe and multiverse repos enabled?

? Ha.

---

### Post by QIII on 2012-06-10
Ah, Bucky...

I hope I entertained you since it's in main.  

Unfortunately, I'm not always at my machine and can't look at the package source repo.

---

### Post by Drowz0r on 2012-06-19
Hello.

The driver seems to install but I get terrible frame rates for some reason.

Also when trying to install the accelerator I get:

```
drowz0r@Prime:~$ sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libva-egl1
```

Any idea what to do?

---

### Post by QIII on 2012-06-19
Could you go to the software center or Synaptic and do a search for it?  It should be in libva in the main repo.  If you don't find it anywhere, I'll look when I get home and submit a Launchpad report if I can't find it.

You could also try [here]("https://launchpad.net/ubuntu/+source/libva/1.0.15-4/+build/3368543") to get it.  Down towards the bottom, under "Built files", you should see a .deb for libva-egl1.

---

### Post by Drowz0r on 2012-06-19
> **QIII said:**
> Could you go to the software center or Synaptic and do a search for it?  It should be in libva in the main repo.  If you don't find it anywhere, I'll look when I get home and submit a Launchpad report if I can't find it.

You could also try [here]("https://launchpad.net/ubuntu/+source/libva/1.0.15-4/+build/3368543") to get it.  Down towards the bottom, under "Built files", you should see a .deb for libva-egl1.

Hello

Thanks for your reply. I found it on the link you posted almost right away. Downloaded and installed without any issues, but I still get:

```
drowz0r@Prime:~$ sudo vainfo
sudo: vainfo: command not found
```:(

SO, I installed vainfo and  libva-glx1 from the software centre but the elg one didn't seem to be there. Now I get:

```
drowz0r@Prime:~$ sudo vainfo
[sudo] password for drowz0r: 
libva: libva version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/fglrx_drv_video.so
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
```

I'm on Ubuntu 11.10 if that matters.

---

### Post by QIII on 2012-06-19
It may be that because one of the files was not found, nothing got installed.

Try to install xvba-va-driver by itself now.  A symlink should be created, but some have had issues with that.

By the way, what sort of hardware do you have?  Is it an integrated Intel/ATI setup or purely ATI?

---

### Post by Drowz0r on 2012-06-19
> **QIII said:**
> It may be that because one of the files was not found, nothing got installed.

Try to install xvba-va-driver and libva-glx1 now.

By the way, what sort of hardware do you have?  Is it an integrated Intel/ATI setup or purely ATI?

The xvba-va-driver was missing too. Just installed that one.

Spec in my signature, it's a dedicated new GFX card into an existing PC which is ATI. The PC has an intel CPU but I don't think that matters...

Gonna reboot and post results in a sec.


---

Done.

So, this looks better:

```

drowz0r@Prime:~$ sudo vainfo
[sudo] password for drowz0r: 
libva: libva version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.32
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD
```Ran a game (Diablo 3) and it just freezes :( (After a reboot it runs but with only about 20 FPS still)

Ran HL1 and it went ok

Ran WCIII and it ran but was extremely low frame rate.

---

### Post by QIII on 2012-06-19
Well, good and bad, then.

Can you tell me what your frame rate is before it crashes or on another game that doesn't crash?

Although it is NOT a good benchmark, glxgears may be interesting to see.  Can you install glxgears and run it from the command line and let me know your framerates?

Also, open Catalyst Control Center from the command line

```
sudo amdcccle
```and set all the anti-aliasing and the graphics quality to their lowest and step up from there to see where things go haywire.

Your 6870 should be doing better than it is.

---

### Post by Drowz0r on 2012-06-19
> **QIII said:**
> Your 6870 should be doing better than it is.

Tell me about it! Two lesser Nvidia cards ran a whole lot better than this. One averaged at about 40FPS while a newer one ran at about 50FPS. I actually sent one of the Nvidia cards back for this more powerful card... but for some reason it runs at 20FPS?

> **QIII said:**
> Well, good and bad, then.

Can you tell me what your frame rate is before it crashes or on another game that doesn't crash?



It averages at 20FPS but if I move around a bunch it can drop to like  5FPS or lower. It seems to crash mostly after playing the game for 20  minutes or something.

> 
Although it is NOT a good benchmark, glxgears may be interesting to see.   Can you install glxgears and run it from the command line and let me  know your framerates?
I'll install it and update in a sec. (Having trouble finding where to get it from) (edit - just realised you just run it:

```
22341 frames in 5.0 seconds = 4468.096 FPS
22378 frames in 5.0 seconds = 4475.261 FPS
23143 frames in 5.0 seconds = 4628.403 FPS
18995 frames in 5.0 seconds = 3798.907 FPS
22557 frames in 5.0 seconds = 4511.220 FPS
22570 frames in 5.0 seconds = 4513.833 FPS
22411 frames in 5.0 seconds = 4482.082 FPS
```


> 
Also, open Catalyst Control Center from the command line

```
sudo amdcccle
```and set all the anti-aliasing and the graphics  quality to their lowest and step up from there to see where things go  haywire.Everything is off/at the lowest setting already.

---

### Post by QIII on 2012-06-19
Framerates that high are not unusual for glxgears running with all the quality settings cranked down.  And, like I said, glxgears is not a good benchmark.  Let me do some looking around.

Edit:  While I'm looking around...

If you are using Compiz, try setting VBlank to "off".  If I recall correctly, that's something like this (off the top of my head):

CompizConfig Settings Manager > OpenGL > Sync To VBlank > OFF

---

### Post by Drowz0r on 2012-06-19
> **QIII said:**
> Framerates that high are not unusual for glxgears running with all the quality settings cranked down.  And, like I said, glxgears is not a good benchmark.  Let me do some looking around.

I'll just post these extra things, in case they help rule stuff out:

I tried different power cables to the card (from the PSU) in case it was failing to draw enough power and just dying or something but no change. My PSU is 750 Watts, which is like 350 more than what the card needs, or something.

Tried adjusting a bunch of settings in game, turning off V-sync and stuff but no change.

Runs the same on monitor1 and monitor 2.

If there is anything else I can do, I'm quite happy to test.

---

### Post by Drowz0r on 2012-06-19
> **QIII said:**
> 
Edit:  While I'm looking around...

If you are using Compiz, try setting VBlank to "off".  If I recall correctly, that's something like this (off the top of my head):

CompizConfig Settings Manager > OpenGL > Sync To VBlank > OFF

I don't think I'm using Compiz. At least I can't find it in my system anywhere heh. Nothing in the Cataylzt thing about it anyway.

---

### Post by Drowz0r on 2012-06-19
Ok, so I just tried:

```

sudo apt-get install fglrx-updates
```It removed 3 files and installed 3 files. It seemed to install a bunch of stuff that was missing. Now my game runs at about 30-40FPS but it crashes after about 2 minutes. Looking at other posts... do these ATI drivers only work for Ubuntu 12.04 and not 11.10? I'm trying to stay on 11.10 as 12.04 causes me a lot of problems in PlayOnLinux.

P.S. What would I need to do to re-install the drivers, in case something was broken or they didn't install right? Worth a shot I suppose.

---

### Post by QIII on 2012-06-19
fglrx-updates and fglrx-amdcccle-updates should update the fglrx versions as AMD puts them out, plus the time it takes for the version to be tested and packaged by a MOTU (Master of the Universe -- the volunteers who keep the Universe and Multiverse repos up to date).

Installing one set will just replace the other.

At the time I wrote the initial post, the Catalyst Control Center did not seem to install properly and I could not get CCC to start, which I mentioned.

(Edit:  See my edit of the original post with regard to this issue.  It's at the bottom of the original.)

You should be fine by now.  However, I can't say for sure if the driver has actually been updated to 12.5 (May) or 12.6 (June - if that has been released) but I'll check when I get home and update my post as appropriate.

As for the crash, is it still on the same game?  Do other games work better now?

---

### Post by Drowz0r on 2012-06-20
> **QIII said:**
> fglrx-updates and fglrx-amdcccle-updates should update the fglrx versions as AMD puts them out, plus the time it takes for the version to be tested and packaged by a MOTU (Master of the Universe -- the volunteers who keep the Universe and Multiverse repos up to date).

Installing one set will just replace the other.

At the time I wrote the initial post, the Catalyst Control Center did not seem to install properly and I could not get CCC to start, which I mentioned.

(Edit:  See my edit of the original post with regard to this issue.  It's at the bottom of the original.)

You should be fine by now.  However, I can't say for sure if the driver has actually been updated to 12.5 (May) or 12.6 (June - if that has been released) but I'll check when I get home and update my post as appropriate.

As for the crash, is it still on the same game?  Do other games work better now?

Nah all games were the same. I've upgraded my distribution to 12.04. It's gone back to the generic drivers it seems and I need to reinstall my wine stuff. I'll try that and get back to you and then try the above ^

---

Edit 20/06/2012

Well updated to 12.04 and it installed the dirvers will no issue at all. All of them in one clean sweep.

The output is:
```

drowz0r@Prime:~$ sudo vainfo
[sudo] password for drowz0r: 
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD

```Which seems fine to me.

Some games are running fine. The older ones where frame rate is expected to be right even on low end cards (HL and Portal). Tried to run WCIII and it was a little better but went insainly laggy when upping the graphics and that's a pretty old game. Having to re-install Diablo 3 after the 12.04 upgrade so I'll have to see how that goes. After further testing, it seems 12.04 can't do some of the stuff 11.10 could do, at least not with stability... I can't seem to get diablo 3 running so I tested some other games that it should be able to run. WCIII with upped graphics, which it should be able to do extremely easily, was about 2FPS.

It's showing the driver as active as well when I check "additional drivers"... so I don't get it.

I was given this link by the guys who sold me the card: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

I don't know if that's just the same thing as your terminal stuff but on a website. I'm going to try these and see how it goes...

---edit

Lol, ok, so, those drivers actually work fine in 12.04. WCIII, HL and Portal run without issue. Need to some how get Diablo 3 working and if that works it should be fine...

---

### Post by Drowz0r on 2012-06-21
Diablo 3 did not like those drivers at all... there is also a "for testing only" watermark I can't get rid of.

I actually returned the card today. Going to buy an nvidia one instead - but thank you for all your efforts! That would have taken me weeks of working out otherwise...

---

### Post by athampan on 2012-06-25
@QIII, I wanted to thank you for your post (it was bit difficult getting to it as it doesn't show up high on search engines).  My Dell N5010 with ATI Mobility Radeon HD 4650 was overheating with linux for over a year (since I bought it).  Reinstalling the ATI driver as you suggested, completely took care of the overheating problem.

Thank you once again (wish there was a way to mod up your post on google).

---

