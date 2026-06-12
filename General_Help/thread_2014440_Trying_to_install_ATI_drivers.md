---
title: "Trying to install ATI drivers"
date: 2012-07-01
forum: General Help
---

### Post by Hungry Man on 2012-07-01
Just reinstalled Ubuntu. I downloaded the latest 12.6 driver and it gives some error saying 'one or more tools required for installation can't be found on the system'

---

### Post by Hungry Man on 2012-07-02
I did a force install but still no hardware acceleration.

---

### Post by QIII on 2012-07-02
Your post might have been more helpful if you had cut and pasted what you saw in the terminal.  With what you have given, it is difficult to say exactly what state your machine is in.

Personally, I'd just have installed the 12.4 driver, since it is in the repos and can be installed easily.

Be that as it may, you may ***try*** the following (you can find this in the ATI wiki in my signature), but I can't guarantee it will work with 12.6.  I wrote that section of the wiki based on the fglrx and fglrx-amdcccle in the repo.

Hardware acceleration is not included with the ATI driver directly.  It can be activated by added four additional packages.

```
sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo
``````
sudo vainfo
```You should get something similar to this if the hardware acceleration is activated:


[FONT=monospace]```
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


```[/FONT]

---

### Post by Hungry Man on 2012-07-02
> libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva error: /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so init failed
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit


Getting this error.

---

### Post by QIII on 2012-07-02
Which version of Ubuntu are you using?

---

### Post by Hungry Man on 2012-07-02
12.04.

Is there a simple way to just go back to the default drivers? Those provided accelerated support at least.

---

### Post by QIII on 2012-07-02
The proprietary driver supports 3d and acceleration better than the open source driver.

To uninstall what you installed, you will have to select the packages by name for removal in a package manager or do the following for the three .deb packages you created:

```
sudo dpkg -r package_name
```for each of them.

First, uninstall the packages I suggested to clean them up.

```
sudo apt-get remove --purge xvba-va-driver libva-glx1 libva-egl1 vainfo
```Then uninstall all the packages you used doing the installation from the ATI website.

---

### Post by Hungry Man on 2012-07-02
I used some file I'd downloaded from their site for 12.6. It's how I've always done it. I'll remove what you've said.

---

### Post by QIII on 2012-07-02
Always prefer what is in the repos.  ATI provides their XX.4 and XX.10 to Canonical ahead of release to the general public.  They are tested to work properly.

If you reinstall , see the section on alternate command line installation from the repo in the wiki. If you install that way and do the acceleration bit and still get the error about the .so not being found, we can fix that.

---

### Post by Hungry Man on 2012-07-02
Same error.

---

### Post by Hungry Man on 2012-07-02
If it would be easier I'd be willing to just use the open source drivers. I really just want to get the 3D support for Unity that lets me change  the panel size etc.

---

### Post by QIII on 2012-07-02
If when you say "same error", does that mean you went through the entire dpkg -r stuff, reinstalled fglrx via command line and installed the acceleration bit?

If it is the acceleration component error, it would be extremely helpful if you would cut and paste what is displayed in the terminal when you try to install the four packages I suggested so it can be viewed.  One of them did not install properly.  I know which one it probably is, but I need to confirm.

Unless the panel size issue is functionality specifically dependent on the open source driver, and for all I know it may be, there should be no reason why that functionality would not be available whrn the fglrx driver is installed -- even without acceleration, 3D should work.

---

### Post by QIII on 2012-07-02
Ah.  Duplicate.

---

### Post by Hungry Man on 2012-07-02
Sorry, that was vague. I meant vainfo gives the same error and I still don't have gpu acceleration.

> libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva error: /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so init failed
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit


I've installed these exact (12.6) drivers before on Ubuntu 12.04. It was just the other day. The problem is I had to reformat for other reasons... but I know it's possible.

---

### Post by QIII on 2012-07-02
I need to know what you get when you try to install the acceleration packages, before you run vainfo.  One of them isn't installing.

---

### Post by Hungry Man on 2012-07-02
> sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo
[sudo] password for colin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libva-egl1 is already the newest version.
libva-glx1 is already the newest version.
vainfo is already the newest version.
xvba-va-driver is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I dont think I'ive had any errors installing these.

> sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo --reinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 4 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/82.9 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 164670 files and directories currently installed.)
Preparing to replace libva-egl1 1.0.15-4 (using .../libva-egl1_1.0.15-4_amd64.deb) ...
Unpacking replacement libva-egl1 ...
Preparing to replace libva-glx1 1.0.15-4 (using .../libva-glx1_1.0.15-4_amd64.deb) ...
Unpacking replacement libva-glx1 ...
Preparing to replace vainfo 1.0.15-4 (using .../vainfo_1.0.15-4_amd64.deb) ...
Unpacking replacement vainfo ...
Preparing to replace xvba-va-driver 0.7.8-1ubuntu3 (using .../xvba-va-driver_0.7.8-1ubuntu3_amd64.deb) ...
Unpacking replacement xvba-va-driver ...
Processing triggers for man-db ...
Setting up libva-egl1 (1.0.15-4) ...
Setting up libva-glx1 (1.0.15-4) ...
Setting up vainfo (1.0.15-4) ...
Setting up xvba-va-driver (0.7.8-1ubuntu3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


---

### Post by QIII on 2012-07-02
Looks like the symlink to fglrx_drv_video.so is not being properly created.  On cellphone right now and can't look at notes until I get home from work, but I'll get back to this.

Still, 3D should be working even without hardware acceleration.

I need to ruminate on this a bit.

---

### Post by QIII on 2012-07-02
Hmmm.  Duplicate post again.

---

### Post by Hungry Man on 2012-07-02
Thanks. I'd honestly just reinstall Ubuntu if I could but the only LiveCD I have is from 11.04 beta... so it would be a huge pain in the ***.

I've never had this issue.

---

### Post by Hungry Man on 2012-07-02
I reformatted. Same issue with the installer saying it "requires tools."

Tried the alternate CLI method. Same issue with vainfo output - no hardware acceleration, which for whatever means I can't resize the bar and I can't use shortucts like Super + direction or Super + W.

---

### Post by QIII on 2012-07-02
For the vainfo bit, could you see if you have either of these two files:

/usr/lib/dri/fglrx_drv_video.so

 /usr/lib/va/drivers/fglrx_drv_video.so


As for the other bit, I'm a bit stumped.  I'm not convinced it is the fglrx driver, per se.   I'll still do some hunting around.

---

### Post by Hungry Man on 2012-07-02
I tried installing the 12.4 driver and then some dependency **** came up and it was like "oh, try with -f" so I did and now the screen just flashes that classic "wtf is this" fuzz over and over and I'm just gonna give up and use Windows for a while lol

---

### Post by vasa1 on 2012-07-02
> **Hungry Man said:**
> I tried installing the 12.4 driver and then some dependency **** came up and it was like "oh, try with -f" so I did and now the screen just flashes that classic "wtf is this" fuzz over and over and I'm just gonna give up and use Windows for a while lol

Lol indeed :)

---

### Post by QIII on 2012-07-03
Can't blame a guy for getting frustrated.  If Windows works, it works.  Use what works.

---

