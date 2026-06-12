---
title: "I did a bad thing!  Please help! ATI removed, now I can't boot past the console."
date: 2009-11-03
forum: General Help
---

### Post by Shekibobo on 2009-11-03
Okay, so this was pretty stupid on my part, I guess.

I was having some issues with my ATI Radeon 4500, so I uninstalled the "proprietary drivers" from Hardware Devices and installed the drivers provided from the website.  It seems that screwed up OpenGL, so I tried to reactivate the drivers under Hardware Devices.  

After doing this, I rebooted, and couldn't get past the console ("Ubuntu 9.10 Human tty1" "Human login:")  And the other problem was that it was blinking radically between light grey and dark grey.  When it was dark, keyboard input didn't register.  So I rebooted again in recovery and used the terminal to run sudo ./fglrx-uninstall.sh (or whatever the command is).  That helped, and I rebooted and fully loaded ubuntu.  However, my graphics drivers weren't installed, so I had to try to reinstall them.  I tried to do this using Hardware Devices.  

For some reason, this didn't work either.  It said there was another version of this active, even though I don't think there actually was.  I tried to uninstall fglrx related items using Synaptic, but that made things worse.  I reinstalled those packages, and then tried to activate the drivers again under Hardware Devices.  I think it pretended to install them, because it happened in the blink of an eye and said I needed to reboot.

So I did.

I got the blinking console again.

So I went back to the recovery console and ran:

sudo apt-get remove --purge xorg-driver-fglrx

It removed 100MB worth of stuff.

Now I don't get the blinking anymore.  But I can't get past the console.
[edit] actually, it blinks for a second, then stabilizes, but still won't load anything beyond the console during boot.

I'm stuck, and I'm out of ideas.  I just seem to be screwing things up more and more every time I try to fix it.  Can anyone help me?

I'm running 64bit karmic on a toshiba satellite L550-5702

---

### Post by Snowyfox12 on 2009-11-03
Hmm... I think you can get support by calling the Company who made your  ATI Raedeon. and how are you writing the post?

---

### Post by Shekibobo on 2009-11-03
I'm on my roommate's computer.  Is there a way to install proprietary drivers from the console?  As if through the Hardware Devices app?

---

### Post by QIII on 2009-11-03
I'm not sure what dependencies you may have taken out with the "--purge" switch.  That can be a tricky one.

I'd like you to wait to do the following until someone else has a chance to get their two cents in.  Where there are many heads, there is wisdom.

But let's see if we can get you going.  Since you were able to get to your desktop using one command, try again.

Run whatever the correct command is.  I'm adding it here as you wrote it in your post.  You really need to find out exactly what the command was FIRST.

```
sudo ./fglrx-uninstall.sh
```Hopefully you least get to your desktop then.

After you have done that and you are at your desktop, open the terminal and do

```
sudo apt-get remove xorg-driver-fglrx
```I hope you don't need the "--purge" switch, but we'll see how this goes.

I suspect you will be told the driver doesn't exist, so don't panic.  The default driver will still be available in memory, so you shouldn't lose your way in the dark.

Now the important part:  DON'T shut down just yet.

Go to Synaptic.  Search for "Catalyst".

You will find the package "fglrx-amdcccle 2:8.660-0ubuntu4", which is Catalyst 9.10 (and driver) that ATI made available specifically for Karmic.  You will notice that it has the Ubuntu "people circle" next to it.

Install it.

Let us know how that turns out.

---

### Post by Shekibobo on 2009-11-03
First off, as I said, though perhaps not clearly, I can't reach the desktop.  Booting stops when it reaches the console and proceeds no further, so I am only able to do terminal commands.

In my attempts, I reinstalled: sudo apt-get install xorg-driver-fglrx
When I did this, it reinstalled those 100mb of stuff I had mentioned previous.  Then I tried running the command you told me to, but it kept saying "couldn't find package 2:8.660-0ubuntu4."  I tried it without that argument, and it said it was already installed.  I uninstalled it, reinstalled it.  No changes.

---

### Post by Shekibobo on 2009-11-03
Here's what is posted when I resume normal boot under recovery boot mode:

```

rc-sysinit stop/waiting
*Starting MySQL database server mysqld
...done.
*Running DKMS auto installation service for kernel 2.6.31-14-generic
*  fglrx(8.660)...
...done
*Not starting jetty - edit /etc/default/jetty and change NO_START to be 0 (or comment it out).
* Starting Postfix Mail Transport Agent postfix
* Speech-dispatcher configured for user sessions
* Starting Network connection manager wicd
* Starting the Winbind daemon winbind
* Starting Common Unix Printing System: cupsd
* PulseAudio configured for per-user sessions
* Enabling additional executable binary formats binfmt-support
* Starting web server apache2
* Checking battery state...
...done.

Ubuntu 8.10 Human tty1

Human login:

```

And then I can only login to the console and use terminal commands.

No desktop, nothing.

---

### Post by QIII on 2009-11-03
Ah.  I thought you said at one point that it would start and run.
 
 OK.  But remember, I also recommended waiting a while to see if others would chime in, so wait for other possible solutions this time...

When you log in, try 

```
startx
```May or may not work.  I suspect it won't.

It looks like fglrx(8.660) is starting.  If you accidentally got rid of the gnome desktop, you can try

```
sudo apt-get install ubuntu-desktop
```

Try rebooting then.

If you haven't gotten anywhere by then, it may get a little more dicey.

```
sudo apt-get update
``````
sudo apt-get upgrade
```... to get you up to date.

Then, in case there is anything new ...

```
sudo apt-get dist-upgrade
```Then...

```
sudo apt-get install fglrx-amdcccle
```... which will probably tell you that you have the most recent one installed.

---

### Post by Shekibobo on 2009-11-03
Tried all that.  startx gave some interesting errors: fatal server error: no screens found.  It output several pages of failed load attempts.  Nothing worked, though.  But thanks for all your help so far.

I also tried to use my ubuntu cd to see if their was a "repair installation" option, but no such luck.

---

### Post by QIII on 2009-11-03
I'm out of ideas, unfortunately.  Give it some time.  Somebody much smarter than I is cruising the forums waiting to strike like a shark from the depths and make us both feel very sheepish.  So don't panic.  And wait a while.  The guy with just the answer may be sleeping off a bender or just waking up in Australia.

The absolute worst case scenario is not really all that bad, if you have some way to do it.

Save your entire /home folder to some other location:  a network drive or removable media (it would probably have to be pretty large).

Reinstall.  This time, however, create a separate /home** partition** instead of having the installation process create a /home folder.

Drag all of your /home junk back into the /home partition after the installation.  You may have to rebuild some of your profiles and reinstall some of your applications, but having a separate /home partition makes it easy to do a "fresh install" next time -- and avoid losing all of your important files.

---

### Post by Shekibobo on 2009-11-04
Now whenever I boot, it gets to the console login screen, then prints some errors, though they come few and far between:

[         37.714225] Intel AES-NI instructions are not detected.
[       219.819765] sd 6:0:0:0: [sdb] Assuming drive cache: write through
..(this repeates several times with a different number in the brackets)
* Reloading Common Unix Printing System: cupsd


I can still do all my terminal commands and everything.  But now it's giving me a new error.  Not sure if it's related or not.  I found a thread that talks about having screwed up the Xorg/gdm, [http://ubuntuforums.org/showthread.php?t=1158205&highlight=boot+halts+console+login](http://ubuntuforums.org/showthread.php?t=1158205&highlight=boot+halts+console+login), but where they talk about changing the /etc/gdm/gdm.conf, I don't have that file.  I do have one called /etc/gdm/custom.conf and one called gdm.schemas.  Neither of these seem to contain the information in the form of the change they are suggesting in that form, though.

I'm reluctant to make any more changes, as everything I've done has just screwed things up worse.  This seems like the closest thing to what I'm experiencing, though.  

My Xorg log file is as follows:

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-26-server x86_64 Ubuntu
...
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section. Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |    |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
          Using the first device section listed.
(**) |    |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
          Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
                Entry deleted from font path.
(==) FontPath set to:
           /usr/share/fonts/X11/misc,
           /usr/share/fonts/X11/100dpi/:unscaled,
           /usr/share/fonts/X11/75dpi/:unscaled,
           /usr/share/fonts/X11/Type1,
           /usr/share/fonts/X11/100dpi,
           /usr/share/fonts/X11/75dpi,
           /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
           built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
        If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 5.0
        X.Org XInput driver : 4.0
        X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:1:0:0) 1002:9553:1179:ffa0 ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series] rev 0, Mem @ 0xd0000000/268435456, 0xf2100000/65536, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
                  ...<a set of 6 addresses>
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
**(II) Loading /usr/lib/xorg/modules/extensions//libglx.so**
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: file too short
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
         compiled for 1.6.4, module version 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
         compiled for 1.6.4, module version 1.13.0
         Module class: X.Org Server Extension
         ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
dlopen: /usr/lib/xorg/modules/extensions//libdri.so: file too short
(EE) Failed to load /usr/lib/xorg/modules/extensions//libdri.so
(II) UnloadModule: "dri"
(EE) Failed to load module "dri" (loader failed, 7)
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.6.4, module version 1.1.0
          ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRIZ
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
dlopen: /usr/lib/xorg/modules/drivers/fglrx.so: file too short
(EE) Failed to load /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) UnloadModule: "fglrx"
(EE) Failed to load module "fglrx" (loader failed, 7)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
                    at http://wiki.x.org
           for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
         

```That's the content of the /var/log/Xorg.0.log file which is identical to the output when I try to run:
```
 $ startx 
```

---

### Post by Shekibobo on 2009-11-04
I attempted to restore a previous version of my xorg.conf file.  It's now been replaced with the following:

```

Section "ServerLayout"
    Identifier        "aticonfig Layout"
    Screen        0    "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier        "aticonfig-Monitor[0]-0"
    Option            "VendorName" "ATI Proprietary Driver"
    Option            "ModelName" "Generic Autodetecting Monitor"
    Option            "DPMS" "true"
EndSection

Section "Device"
    Identifier        "aticonfig-Device[0]-0"
    Driver            "fglrx"
    BusID            "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier        "aticonfig-Screen[0]-0"
    Device             "aticonfig-Device[0]-0"
    Monitor            "aticonfig-Monitor[0]-0"
    DefaultDepth    24
    SubSection    "Display"
        Viewport    0 0
        Depth        24
    EndSubSection
EndSection


```And now, when I run $startx, I get the following:

```

dlopen: /usr/lib/xorg/modules/extensions//libglx.so: file too short
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(EE) Failed to load module "glx" (loader failed, 7)
dlopen: /usr/lib/xorg/modules/extensions//libdri.so: file too short
(EE) Failed to load /usr/lib/xorg/modules/extensions//libdri.so
(EE) Failed to load module "dri" (loader failed, 7)
dlopen: /usr/lib/xorg/modules/drivers//fglrx_drv.so: file too short
(EE) Failed to load /usr/lib/xorg/modules/drivers//fglrx_drv.so
(EE) Failed to load module "fglrx" (loader failed, 7)
(EE) No drivers available.

Fatal server error:
no screens found

<insignificant stuff>

ddxSigGiveUp: Closing log
giving up.
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error."
xauth: error in locking authority file /home/user/.Xauthority

```I feel like no matter what I do, nothing helps.  Please someone help me.  All my project files are on this partition, and I can't get to it through windows.

---

### Post by bouncer5 on 2009-11-04
Couldn't you use a livecd to access the partition?

---

### Post by Shekibobo on 2009-11-04
> **bouncer5 said:**
> Couldn't you use a livecd to access the partition?

I actually tried that but it kept telling me authentication failed.

---

### Post by Shekibobo on 2009-11-04
Can anyone please help me?

Is there maybe a way I can reset the xorg settings to a 'first time startup' configuration?  We know there are three files that aren't working for some reason.  Please, someone help.

---

### Post by Shekibobo on 2009-11-04
In the words of my xorg log file:

giving up.

I finally gave up and am reinstalling the whole system.  Beats not knowing when I'm going to find a solution.

---

### Post by jonathank89 on 2009-11-05
I'm hoping you haven't given up quite yet, I had a similar problem, what worked for me was firstly backing up the xorg.conf file:

sudo cp /etc/X11/xorg.conf /etc/X11/backup-xorg.conf

Then just deleting the xorg.conf:

sudo rm /etc/X11/xorg.conf

Once you've deleted it run:

startx

And it should start up your desktop.

---

### Post by Shekibobo on 2009-11-05
Well, I wish I'd thought of that.  But I just started over.  Wasn't too painful.  I was able to back up everything that I needed, and was pretty much prepared for something like this since I had to transfer everything from my broken hp laptop about two weeks ago.

---

### Post by jonathank89 on 2009-11-05
> **Shekibobo said:**
> Well, I wish I'd thought of that.  But I just started over.  Wasn't too painful.  I was able to back up everything that I needed, and was pretty much prepared for something like this since I had to transfer everything from my broken hp laptop about two weeks ago.

Ah well at least the only thing you lost was a little time, no damage done. I just removed the xorg.conf and it seemed to let me log in finally. Then to reinstall the propietry driver again, which just activating on it didn't seem to work, I went into synaptic made sure I installed or reinstalled fglrx-kernel-source, xorg-driver-fglrx, fglrx-amdcccle and fglrx-modaliase. Simply logged out, logged back in and went into hardware drivers and activated the driver and it asked me to restart, I did so and it worked :D

Just a little tip for the future...Although I can't verify that this will work all the time, I could have just gotten lucky...

---

