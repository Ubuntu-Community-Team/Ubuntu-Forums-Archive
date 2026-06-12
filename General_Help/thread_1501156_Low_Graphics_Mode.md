---
title: "Low Graphics Mode"
date: 2010-06-03
forum: General Help
---

### Post by Uadebisi on 2010-06-03
Hi,

Recently upgraded to 10.04 after countless problems w/ Karmic & already problems with Lucid!

The screen sometimes suddenly goes black, then goes into low graphics mode, if I let it, thereby changing screen rez & unless I reboot, I am stuck in this mode. If I don't choose temporary low graphics mode, I must reboot. 

Many others seem to be experiencing the same problem yet have been offered no solution by the developers. So...I hope a solution comes soon... :)

---

### Post by Uadebisi on 2010-06-05
Anyone?

---

### Post by Uadebisi on 2010-06-06
Well, here's something new... now before the "low graphics mode" prompt, the screen flashed a few times with "low battery mode" or something to that effect.

---

### Post by quequotion on 2010-06-06
I'm also having this issue. It was happening sporadically at first, but now it's nearly every boot.

I found a way around it, but I can't guarantee it will work for you as a lot of things can cause this problem (like your proprietary drivers being deleted during the upgrade without your xorg.conf beign updated...happens every time...) In my case I think it's either a suid or file permissions problem.

1. Choose to exit to terminal login.
2. Login with your usual username & password.
3. Start gdm with sudo:```
sudo gdm
```

Here's an xorg log of the failure I'm having. which I can't make much sense of. Everything seems to go well until loading the Nvidia kernel module, which doesn't work and then xorg just gives up.

```
[    21.904] 
X.Org X Server 1.8.1.901 (1.8.2 RC 1)
Release Date: 2010-05-11
[    21.904] X Protocol Version 11, Revision 0
[    21.904] Build Operating System: Linux 2.6.24-27-xen x86_64 Ubuntu
[    21.904] Current Operating System: Linux ProliantMK2 2.6.34-5-generic #14-Ubuntu SMP Fri Jun 4 02:19:33 UTC 2010 x86_64
[    21.904] Kernel command line: root=/dev/mapper/nvidia_dgcgcffh1 ro quiet splash 
[    21.904] Build Date: 02 June 2010  10:41:20PM
[    21.904] xorg-server 2:1.8.1.901+git20100602+server-1.8-branch.b65c5be1-0ubuntu0sarvatt4~lucid (Robert Hooker <sarvatt@ubuntu.com>) 
[    21.904] Current version of pixman: 0.19.1
[    21.904] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    21.904] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.904] (==) Log file: "/var/log/Xorg.5.log", Time: Mon Jun  7 01:03:31 2010
[    21.905] (==) Using config file: "/etc/X11/xorg.conf"
[    21.905] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.905] (==) No Layout section.  Using the first Screen section.
[    21.905] (**) |-->Screen "Default Screen" (0)
[    21.905] (**) |   |-->Monitor "Configured Monitor"
[    21.905] (**) |   |-->Device "Configured Video Device"
[    21.905] (**) Option "DontZap" "False"
[    21.905] (==) Automatically adding devices
[    21.905] (==) Automatically enabling devices
[    21.905] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.905] 	Entry deleted from font path.
[    21.905] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    21.905] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.905] (**) Extension "Composite" is enabled
[    21.905] (**) Extension "RENDER" is enabled
[    21.905] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.905] (II) Loader magic: 0x7cf8c0
[    21.905] (II) Module ABI versions:
[    21.905] 	X.Org ANSI C Emulation: 0.4
[    21.905] 	X.Org Video Driver: 7.0
[    21.905] 	X.Org XInput driver : 9.0
[    21.905] 	X.Org Server Extension : 3.0
[    21.941] (--) PCI: (0:1:9:0) 4444:0016:10fc:d01e Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder rev 1, Mem @ 0xc8000000/67108864
[    21.967] (--) PCI:*(0:7:0:0) 10de:0a20:107d:2715 nVidia Corporation GT216 [GeForce GT 220] rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/524288
[    21.967] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.967] (II) "extmod" will be loaded by default.
[    21.967] (II) "dbe" will be loaded by default.
[    21.967] (II) "glx" will be loaded by default.
[    21.967] (II) "record" will be loaded by default.
[    21.967] (II) "dri" will be loaded by default.
[    21.967] (II) "dri2" will be loaded by default.
[    21.967] (II) LoadModule: "extmod"
[    21.967] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.968] (II) Module extmod: vendor="X.Org Foundation"
[    21.968] 	compiled for 1.8.1.901, module version = 1.0.0
[    21.968] 	Module class: X.Org Server Extension
[    21.968] 	ABI class: X.Org Server Extension, version 3.0
[    21.968] (II) Loading extension MIT-SCREEN-SAVER
[    21.968] (II) Loading extension XFree86-VidModeExtension
[    21.968] (II) Loading extension XFree86-DGA
[    21.968] (II) Loading extension DPMS
[    21.968] (II) Loading extension XVideo
[    21.968] (II) Loading extension XVideo-MotionCompensation
[    21.968] (II) Loading extension X-Resource
[    21.968] (II) LoadModule: "dbe"
[    21.968] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.968] (II) Module dbe: vendor="X.Org Foundation"
[    21.968] 	compiled for 1.8.1.901, module version = 1.0.0
[    21.968] 	Module class: X.Org Server Extension
[    21.968] 	ABI class: X.Org Server Extension, version 3.0
[    21.968] (II) Loading extension DOUBLE-BUFFER
[    21.968] (II) LoadModule: "glx"
[    21.968] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    21.978] (II) Module glx: vendor="NVIDIA Corporation"
[    21.978] 	compiled for 4.0.2, module version = 1.0.0
[    21.978] 	Module class: X.Org Server Extension
[    21.978] (II) NVIDIA GLX Module  256.29  Thu May 27 17:48:26 PDT 2010
[    21.978] (II) Loading extension GLX
[    21.978] (II) LoadModule: "record"
[    21.979] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.979] (II) Module record: vendor="X.Org Foundation"
[    21.979] 	compiled for 1.8.1.901, module version = 1.13.0
[    21.979] 	Module class: X.Org Server Extension
[    21.979] 	ABI class: X.Org Server Extension, version 3.0
[    21.979] (II) Loading extension RECORD
[    21.979] (II) LoadModule: "dri"
[    21.979] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.979] (II) Module dri: vendor="X.Org Foundation"
[    21.979] 	compiled for 1.8.1.901, module version = 1.0.0
[    21.979] 	ABI class: X.Org Server Extension, version 3.0
[    21.979] (II) Loading extension XFree86-DRI
[    21.979] (II) LoadModule: "dri2"
[    21.980] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.980] (II) Module dri2: vendor="X.Org Foundation"
[    21.980] 	compiled for 1.8.1.901, module version = 1.2.0
[    21.980] 	ABI class: X.Org Server Extension, version 3.0
[    21.980] (II) Loading extension DRI2
[    21.980] (II) LoadModule: "nvidia"
[    21.980] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    21.980] (II) Module nvidia: vendor="NVIDIA Corporation"
[    21.980] 	compiled for 4.0.2, module version = 1.0.0
[    21.980] 	Module class: X.Org Video Driver
[    21.981] (II) NVIDIA dlloader X Driver  256.29  Thu May 27 17:28:03 PDT 2010
[    21.981] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    21.981] (--) using VT number 8

[    21.986] (II) Primary Device is: PCI 07@00:00:0
[    21.986] (II) Loading sub module "fb"
[    21.986] (II) LoadModule: "fb"
[    21.986] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.987] (II) Module fb: vendor="X.Org Foundation"
[    21.987] 	compiled for 1.8.1.901, module version = 1.0.0
[    21.987] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.987] (II) Loading sub module "wfb"
[    21.987] (II) LoadModule: "wfb"
[    21.987] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.987] (II) Module wfb: vendor="X.Org Foundation"
[    21.987] 	compiled for 1.8.1.901, module version = 1.0.0
[    21.987] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.987] (II) Loading sub module "ramdac"
[    21.987] (II) LoadModule: "ramdac"
[    21.987] (II) Module "ramdac" already built-in
[    21.987] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    21.987] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    21.987] (==) NVIDIA(0): RGB weight 888
[    21.987] (==) NVIDIA(0): Default visual is TrueColor
[    21.987] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.987] (**) NVIDIA(0): Option "NoLogo" "true"
[    21.987] (**) NVIDIA(0): Option "MultisampleCompatibility" "true"
[    21.987] (**) NVIDIA(0): Option "RandRRotation" "true"
[    21.987] (**) NVIDIA(0): Option "Coolbits" "1"
[    21.987] (**) NVIDIA(0): Option "TripleBuffer" "true"
[    21.987] (**) NVIDIA(0): Multisample Compatibility enabled
[    21.987] (**) NVIDIA(0): Enabling RENDER acceleration
[    21.987] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    21.987] (II) NVIDIA(0):     enabled.
[    22.000] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[    22.000] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[    22.000] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[    22.000] (EE) NVIDIA(0):  *** Aborting ***
[    22.000] (II) UnloadModule: "nvidia"
[    22.000] (II) UnloadModule: "wfb"
[    22.000] (II) UnloadModule: "fb"
[    22.000] (EE) Screen(s) found, but none have a usable configuration.
[    22.000] 
Fatal server error:
[    22.000] no screens found
[    22.000] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    22.000] Please also check the log file at "/var/log/Xorg.5.log" for additional information.
[    22.000] 
```

---

### Post by Uadebisi on 2010-06-09
Come Ubuntu support...please offer all of us a solution to this problem...other than Windows! ;)

---

### Post by Frogs Hair on 2010-06-09
What kind of computer and graphics card do you have ?

---

### Post by Uadebisi on 2010-06-09
Thanks!

2003-2004 Gateway, Pentium 4
Dual boot w/ Windows XP
Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

---

### Post by clhsharky on 2010-06-09
Uadebisi

> Come Ubuntu support...please offer all of us a solution to this problem
Intel writes the graphic drivers for your card, not Ubuntu, your grip is with Intel.

Jaunty was last release with intel drivers that worked well with i915 chips and older. All the newer drivers are aimed more towards KMS and the newer chips.

Even though Intel drivers are open source they have never released documents on drivers, so only Intel write or contract out the writing of drivers for there chips.

I recommend Hardy or Jaunty until Intel can get you some drivers that work on older chips.

There should be some workarounds for Lucid, but that is not what users wants to deal with on a regular basis.


Sharky

---

### Post by Uadebisi on 2010-06-09
Thanks for the input but I disagree w/ your view. My problem is in fact w/ Ubuntu. I have been trying to use Ubuntu for about 9 months, from Jaunty to Karmic to Lucid & ALL of them have been problematic, unstable OS's with too many problems to list. 

Funny, I have been using this old dog of a pc for many years & have NEVER had a problem w/ Intel w/ Windows. The problem is with Ubuntu. There are many others who are experiencing the same problem as I am, some with Intel & some using NVIDIA graphics cards. I suppose the problem is with NVIDIA too? Come on...Intel products are in an incredibly high percentage of computers, including both my pc's & my Mac, all of which run just fine...when not booted to Ubuntu that is. 

I use Ubuntu as needed....which is dependent on my level of patience that day to deal w/ its glitches. All I am looking for, along with many others, is a fix, if there is one.

---

### Post by quequotion on 2010-08-10
I don't think this is a graphics card or driver problem.

I solved (temporarily worked around?) this issue on my system by fixing an init configuration file.

Something was wrong with gdm-binary's exec call in **/etc/init/gdm.conf**

it was being called with a variable for $CONFIG_FILE but as far as i can tell there's either no definition for that variable or it is mis-defined outside of this file.

I fixed it by commenting out the variable (near the last line):

```
# gdm - GNOME Display Manager
#
# The display manager service manages the X servers running on the
# system, providing login and auto-login services

description	"GNOME Display Manager"
author		"William Jon McCann <mccann@jhu.edu>"

start on (filesystem
          and started dbus
          and (graphics-device-added fb0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or stopped udevtrigger))
stop on runlevel [016]

emits starting-dm

env XORGCONFIG=/etc/X11/xorg.conf

script
    if [ -n "$UPSTART_EVENTS" ]
    then
	[ ! -f /etc/X11/default-display-manager -o "$(cat /etc/X11/default-display-manager 2>/dev/null)" = "/usr/sbin/gdm" ] || { stop; exit 0; }

	# Check kernel command-line for inhibitors
	for ARG in $(cat /proc/cmdline)
	do
	    case "${ARG}" in
		text|-s|s|S|single)
		    plymouth quit || :  # We have the ball here
		    exit 0
		    ;;
	    esac
	done
    fi

    if [ -r /etc/default/locale ]; then
	. /etc/default/locale
	export LANG LANGUAGE
    elif [ -r /etc/environment ]; then
	. /etc/environment
	export LANG LANGUAGE
    fi
    export XORGCONFIG

    exec gdm-binary #$CONFIG_FILE
end script
```

18/08/10 - This workaround allowed me to boot flawlessly for about a week. As of yesterday, ubuntu began booting directly to text login. I think it is the same issue as I have the same (useless) output in my xorg and kernel logs once again.

---

### Post by Zarckon on 2010-08-11
Thank you Quequotion. Commenting the line in gdm.conf worked for me as well. But, what the heck is happening here? Is the variable corrupted? Missing? And at least for me why now after months of everything working perfectly?

---

### Post by Uadebisi on 2010-08-12
[B]quequotion,

[/B]Hi & thanks!

Just one thing...how the heck do I "comment out the variable (near the last line)"?

I am not terribly versed in Linux. Thanks!!

---

### Post by earthpigg on 2010-08-12
> **Uadebisi said:**
> [B]quequotion,

[/B]Hi & thanks!

Just one thing...how the heck do I "comment out the variable (near the last line)"?

I am not terribly versed in Linux. Thanks!!

he is talking about this line, towards the end:

```
    exec gdm-binary #$CONFIG_FILE
```

to comment it out means to add the #.

so, i am assuming that line used to look like this:

```
    exec gdm-binary $CONFIG_FILE
```
and he made it look like this:
```
    exec gdm-binary #$CONFIG_FILE
```

the # is used to 'comment out' something, meaning "tell the computer that this part isn't meant to be executed, it's just there for a human to read if s/he wants to."

deleting everything after # would do the same thing, but then it would be harder to undo. commenting it out leaves it there as a note for you, the human, but tells the computer "don't actually do this."

see all the stuff at the beginning of the file he has, with the # in front of it? that indicates stuff that is there for the human reading it, not the computer executing it.

---

### Post by Uadebisi on 2010-08-12
Thanks! Just 1 more thing...

I realized that I have no idea how to locate the code to which **quequotion **is referring.:confused:

Again, I am unfamiliar w/ Linux.

---

### Post by Zarckon on 2010-08-13
> **Zarckon said:**
> Thank you Quequotion. Commenting the line in gdm.conf worked for me as well. But, what the heck is happening here? Is the variable corrupted? Missing? And at least for me why now after months of everything working perfectly?

Turns out I spoke too soon. The fix only worked for the one boot and it was back to crashing. I did find a sort of solution from another thread

[http://ubuntuforums.org/showthread.php?t=1466150&highlight=low+graphics+mode&page=4]("http://ubuntuforums.org/showthread.php?t=1466150&highlight=low+graphics+mode&page=4")

but I have to repeat the fix every time I boot. At this point I have to conclude that the problem lies in the linux kernal and not in the nvidia driver as all I actually have to do is restart x each time. If it was the nvidia driver that should not work (at least that's the way I see it). I'd like a permanent solution and hope that someone finds one soon as the problem seems to be expanding rather than reducing.

---

### Post by Uadebisi on 2010-08-13
> the problem seems to be expanding rather than reducing. 	

Welcome to the Wonderful Unstable World of Linux!

I have NEVER had Ubuntu function w/o a glitch or more.

Anyway, I would like to give **quequotion **fix a try. Can someone tell me more specifically how to access the code to which he or she was referring? 

Oh, & BTW** Zarckon, **I don't even have an Nvidia graphics card & I am still having the problem. Someone earlier in the thread blamed the problem on my Intel card. But I am with you, although I am not versed in Linux, I assume the problem is within the Linux OS & not with my pc, considering that it runs fine with Windows, although the fact that mine & most other computers are built to run w/ Windows & not Linux, may also contribute!

---

### Post by Uadebisi on 2010-08-16
Anyway, I would like to give **quequotion **fix a try. Can someone tell me more specifically how to access the code to which he or she was referring?

Thanks!

---

### Post by earthpigg on 2010-08-18
> **Uadebisi said:**
> Anyway, I would like to give **quequotion **fix a try. Can someone tell me more specifically how to access the code to which he or she was referring?

Thanks!

he made a typo. he meant to say:

```
/etc/ini_***t***_/gdm.conf
```

you can edit the file thusly:

```
sudo gedit /etc/init/gdm.conf
```

---

### Post by quequotion on 2010-08-18
> **earthpigg said:**
> he made a typo.

indeed! thank you for pointing that out!

---

### Post by quequotion on 2010-08-18
> **Zarckon said:**
> Turns out I spoke too soon. The fix only worked for the one boot and it was back to crashing. I did find a sort of solution from another thread

[http://ubuntuforums.org/showthread.php?t=1466150&highlight=low+graphics+mode&page=4]("http://ubuntuforums.org/showthread.php?t=1466150&highlight=low+graphics+mode&page=4")

but I have to repeat the fix every time I boot. At this point I have to conclude that the problem lies in the linux kernal and not in the nvidia driver as all I actually have to do is restart x each time. If it was the nvidia driver that should not work (at least that's the way I see it). I'd like a permanent solution and hope that someone finds one soon as the problem seems to be expanding rather than reducing.

I've also had a recurrence of this issue, after my suggestion worked for the last week or so. It's changed a little: instead of getting a list of options, ubuntu boots directly to text login. The Xorg log errors are just the same, containing no helpful information at all. nvidia just stops loading it's modules, exits, and unloads with a suggestion to "read the xorg log" and "check the manual".

which of the fixes in that thread did you try? the module blacklist looks like a good idea..

by the way, are there any current bug reports in launchpad for this? i've looked through a few, but i can't quite find the exact issue.

---

### Post by Uadebisi on 2010-08-18
**earthpigg**,

Thanks.
[B]
quequotion,

[/B]> I've also had a recurrence of this issue

So, it would seem as though commenting out the suggested variable is not the answer, correct?

Also, I do not have an Nvidia card, rather an Intel...& just in case this was lost, I also receive the following message when the OS fails:

> before the "low graphics mode" prompt, the screen flashed a few times with "low battery mode" or something to that effect.

Any more thought? Thanks!

---

### Post by quequotion on 2010-08-19
> **Uadebisi said:**
> 
So, it would seem as though commenting out the suggested variable is not the answer, correct?

Indeed. It seemed to get around the issue for a little while, but in the end the same problem returned.

I get the impression that something in gdm's default configuration is the problem.

I read a discussion earlier about how gdm can only be started by root, as login needs to be a secure process, and I think somehow ubuntu is failing to initialize gdm as root.
user/group permissions can be a two-edged sword--great for security but a nightmare for configuration.

> Also, I do not have an Nvidia card, rather an Intel...& just in case this was lost, I also receive the following message when the OS fails:

Hmm.. perhaps our problems are not as similar as I thought. Are you using a laptop or a desktop? I haven't seen this message, but I am using a desktop without the laptop-mode tools, so I don't think I can get this message.
This could also be proof that it isn't a driver issue.

If you choose to go to a terminal (text login) from the list of options, can you start gdm with```
sudo service gdm start
```This is how I am getting into my desktop for the time being. There are other commands that do the same thing.

---

### Post by quequotion on 2010-08-19
Possibly related bug reports:

[532436](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/532436) - failure possibly related to nvidia

[573455](https://bugs.launchpad.net/ubuntu/+bug/573455) - i marked this as a duplicate of 532436

[ 581302](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/581302) - the description contains different details (more like Uadebisi's troubles) and is not connected to the nvidia driver, unfortunately it was allowed to expire

[498315](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/498315) - similar problem as I am having now, but I haven't looked into this yet. I also use ureadahead and this report proposes a connection

[ 587607](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/587607) - probably a duplicate of 581302, but not yet expired

[ 496796](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/496796) - probably unrelated, but worth a look

[ 447226](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/447226) - probably unrelated, but worth a look

The developers might be upset with me saying this but - Make sure to post your grievances in any or all of these if they look like what's happening to you. More posts = more attention = faster solution.

---

### Post by Uadebisi on 2010-08-19
**quequotion**,

> Are you using a laptop or a desktop? I haven't seen this message, but I  am using a desktop without the laptop-mode tools, so I don't think I can  get this message.
This could also be proof that it isn't a driver issue.

I am using an older desktop. You mention not using laptop-mode tools. Is there a setting I can alter so I can try w/o such tools?

I will have a look at your links. Thank you!

---

### Post by quequotion on 2010-08-20
> **Uadebisi said:**
> **quequotion**,
I am using an older desktop. You mention not using laptop-mode tools. Is there a setting I can alter so I can try w/o such tools?

It's a package you can install or remove from Synaptic, "laptop-mode-tools", but it might not be installed on your system. I think this package was replaced in Lucid (with "pm-utils-powersave-policy"), but I had to replace it manually since I didn't upgrade the usual way (from Karmic).

I don't know how either package works in detail :(

---

### Post by quequotion on 2010-08-21
So following the trend in bug reports that this could be a race condition, I tried another way around this.

Remember where I suggested to add a '#' before?
I took my '#' out and, one line above that, inserted a new line with ```
sleep 2
``` Ubuntu is starting normally again for me (five sucessful tries so far). 

I don't know if this will stick. I do know there has got to be a better way.

If one could devise a loop that waits until the graphics driver module can be confirmed loaded before calling gdm-binary then I'd consider the issue resolved.

__________________________________
Now that I'm home again (last post from phone) here's the full code to see what I've done.

**/etc/init/gdm.conf**```
# gdm - GNOME Display Manager
#
# The display manager service manages the X servers running on the
# system, providing login and auto-login services

description	"GNOME Display Manager"
author		"William Jon McCann <mccann@jhu.edu>"

start on (filesystem
          and started dbus
          and (graphics-device-added fb0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or stopped udevtrigger))
stop on runlevel [016]

emits starting-dm

env XORGCONFIG=/etc/X11/xorg.conf

script
    if [ -n "$UPSTART_EVENTS" ]
    then
	[ ! -f /etc/X11/default-display-manager -o "$(cat /etc/X11/default-display-manager 2>/dev/null)" = "/usr/sbin/gdm" ] || { stop; exit 0; }

	# Check kernel command-line for inhibitors
	for ARG in $(cat /proc/cmdline)
	do
	    case "${ARG}" in
		text|-s|s|S|single)
		    plymouth quit || :  # We have the ball here
		    exit 0
		    ;;
	    esac
	done
    fi

    if [ -r /etc/default/locale ]; then
	. /etc/default/locale
	export LANG LANGUAGE
    elif [ -r /etc/environment ]; then
	. /etc/environment
	export LANG LANGUAGE
    fi
    export XORGCONFIG

    sleep 2 # this is ugly but it seems to work.
    exec gdm-binary $CONFIG_FILE
end script
```

---

### Post by Uadebisi on 2010-08-21
[B]quequotion,
[/B]
> I don't know if this will stick. I do know there has got to be a better way.

Please do keep me a apprised! You are obviously far more Linux competent than I so I will wait & see how you do!

Does the problem that I am having sound comparable to your problem?

Thanks.

---

### Post by quequotion on 2010-08-22
> **Uadebisi said:**
> [B]quequotion,
[/B]


Please do keep me a apprised! You are obviously far more Linux competent than I so I will wait & see how you do!

Does the problem that I am having sound comparable to your problem?

Thanks.

Haha, I appreciate the complement but to be honest I just google a lot and poke and prod at things ;)

Give the "sleep 2" a try. I do think our issues have the same root, which is either poor init timing or broken permissions. I'm leaning more toward poor init timing at the moment.

---

### Post by Uadebisi on 2010-08-22
[B]quequotion,

[/B]Just 1 more thing**...**on restart I often get the following message, which disappears after a few seconds:

> power management not responding

Still sound like your fix may work?

---

### Post by Uadebisi on 2010-08-22
**quequotion,**

In regards to my last comment...either way, I tried your fix, although I have no idea what I just did ;)

> Give the "sleep 2" a try. I do think our issues have the same root,  which is either poor init timing or broken permissions. I'm leaning more  toward poor init timing at the moment. 	

Time will tell...thanks & stay tuned!:popcorn:

---

### Post by Uadebisi on 2010-08-23
Well...I rebooted this morning after adding "Sleep 2" as a fix & I did still receive the prompt while logging in to Ubuntu: 

> power management not responding 			 		

So, if the power management is related to my intermittent shut-downs, then I suppose the OS will again fail. We'll see...

I have no concrete proof of this but it seemed as though the Ad Block Plus add-on for FF caused the Low Graphics Mode shut down problem to be more predominant ](*,)

---

### Post by quequotion on 2010-08-24
Hmm... Did Ubuntu at least start booting to the usual graphical login screen?
My suggestion should not fix problems with power management. It's just a pause to make the login manager (gdm) wait.
Do you have either of the power management packages I mentioned before?

---

### Post by Uadebisi on 2010-08-24
> **quequotion said:**
> Hmm... Did Ubuntu at least start booting to the usual graphical login screen?
My suggestion should not fix problems with power management. It's just a pause to make the login manager (gdm) wait.
Do you have either of the power management packages I mentioned before?

Yes, always starts booting & continues booting despite the "power management" warning. The prompt eventually goes away..in about 5-10 seconds.

How do I know what power manage. pkgs I have?

Thanks!

---

### Post by quequotion on 2010-08-25
> **Uadebisi said:**
> How do I know what power manage. pkgs I have?

You can see alli installed and available software packages in Synaptic.

From the top-left menu: System-> Administration-> Synaptic

Use the search box to check for the two I mentioned earlier in the thread. Most likely, and hopefully, you have pm-utils-powersave-policy installed.

---

### Post by Uadebisi on 2010-08-25
Well, I searched for "laptop-mode-tools" & "pm-utils-powersave-policy" & both came up but the first doesn't actually seem to be installed.

So, why is this good that "pm-utils-powersave-policy" is installed? I assume so that I can delete it & cross my fingers in hopes that it is somehow the source of my problems.

Also, if I should delete it, should I also remove the "Sleep 2" command?

Thanks!

---

### Post by quequotion on 2010-08-26
> **Uadebisi said:**
> So, why is this good that "pm-utils-powersave-policy" is installed? I assume so that I can delete it & cross my fingers in hopes that it is somehow the source of my problems.

Also, if I should delete it, should I also remove the "Sleep 2" command?

laptop-mode-tools has been depricated by pm-utils-powersave-policy in Lucid. It seems Ubuntu's developers are in the process of finding simpler, better ways of managing power consumption.

[here's a thread about that](http://ubuntuforums.org/showthread.php?t=1450501)

[also, it seems pm-utils-powersave-policy will be depricated in Maverick](http://ubuntuforums.org/showthread.php?t=1534700)

First, try reconfiguring the package (this can only be done in a terminal):```
sudo dpkg-reconfigure pm-utils-powersave-policy
``` Then reboot.

If you still get the error, try reinstalling the package (this can be done in Synaptic):```
sudo aptitude reinstall pm-utils-powersave-policy
```
Then reboot.

If you still get the same error, all that's left is to remove the package (this can be done in Synaptic).```
sudo aptitude remove pm-utils-powersave-policy
```
Then reboot.

If you remove the package, you will lose some power-saving functions--but they aren't essential.

If booting is successful, try removing the "sleep 2" and reboot again.
If anything does go wrong, don't panic.

I found some bug reports about "power managment not responding"; unfortunately neither has gotten much attention or made much progress.

[528359](https://bugs.launchpad.net/ubuntu/+bug/528359) - sounds like several issues in one bug report and may be related to problems in init/gdm, but the reporter has been having this problem since Karmic.
[587986](https://bugs.launchpad.net/pm-utils/+bug/587986) - "power management not responding" when a disk is in the optical drive

---

### Post by Uadebisi on 2010-08-28
Well...nothing has worked... 

1- Sleep2 caused additional problems....seemingly same Low Graphics Mode error but screen was now gray so I couldn't see any screen activity. I think I vaguely saw the Low Graphics Mode error in the background.

2-Removed Sleep2
3-Reconfigured Power Manager- still noticed Power Man. error on start-up
4-Re-installed Power Manager- still noticed Power Man. error on start-up
5-Removed Power Manager- still noticed Power Man. error on start-up

I presently have no power management utility installed...what now?:(

I do not know if the Low Graphics Mode Error will still occur without the Power Management Utility nor if the 2 issues are even connected. I do know that the Low Graphics Mode occurred  after I reconfigured the Power Manager.

---

### Post by Uadebisi on 2010-08-29
UPDATE:

Well, still shutting down w/ low graphics mode error. 

Still power management warning on start-up

And now, when shutting down & booting up, there are other things happening, although flashing a bit too quickly to see much.

So, how do I re-install my power management?

And, any other suggestions? :(

---

### Post by quequotion on 2010-08-30
> **Uadebisi said:**
> UPDATE:

Well, still shutting down w/ low graphics mode error. 

Still power management warning on start-up

And now, when shutting down & booting up, there are other things happening, although flashing a bit too quickly to see much.

So, how do I re-install my power management?

And, any other suggestions? :(

You can reinstall from Synaptic or, in a terminal:```
sudo aptitude install pm-utils-powersave-policy
```

Wow... are you sure you added "sleep 2" and not "**S**leep 2"?

---

### Post by Uadebisi on 2010-08-30
No, not 100% sure about **S vs s**

I will try again...thanks

---

### Post by markMDW on 2010-08-30
> **Uadebisi said:**
> Yes, always starts booting & continues booting despite the "power management" warning. The prompt eventually goes away..in about 5-10 seconds.

How do I know what power manage. pkgs I have?

Thanks!

Hi, I've got Ubuntu 10.04 installed on brand new hardware with nvidia card and restricted drivers.  Everything works well but I DO also have the power management warning on bootup.  It usually lasts less than 5 seconds then disappears without any other related problems that I can see.  

I only have beginner experience with Linux, but I would offer some advice.  I have noticed that Xubuntu seems more stable and less prone to glitches that Ubuntu.  I've installed it on a couple of machines with Great Experiences.  With my brand new computer equipment I figured I needed more Bells, Whistles, and Wow... Ubuntu.  Anyhow, even with all that, I still think Xubuntu is Better for a general purpose computer used mainly for Internet, Email,  Word Processing and Spreadsheets.  It's seems much less prone to annoyances.  Also, I had glitches on my system from Upgrade.  I recommend backing up your data and installing FRESH, then Installing Restricted Drivers, and then the Ubuntu Restricted Extras (or Xubuntu Restricted Extras).   If it's possible to backup your XP and Ubuntu Data, I'd do that, then reinstall everything.  Note:  my systems that work perfectly only have Xubuntu on it, and on old hardware.  My system that has a few minor glitches has Ubuntu 10.04 on it, as well as Windows 7.  

As a last resort for Linux salvation you should skip Ubuntu and all other distributions and go directly to Debian Stable, and install the Stable verion, the most tested Linux Distribution out there.. but without any of the latest and greatest Linux software advancements of the last couple of years.   And I'd install it on a clean system without Windows.

That being said, I'm new to Linux, so others with more Experience please add to (or subtract from) my advice.  Good Luck with Linux, stick with it please!

---

### Post by quequotion on 2010-08-31
> **Uadebisi said:**
> No, not 100% sure about **S vs s**

I will try again...thanks

Good luck! I'm just about out of ideas, so hopefully this thread will get some attention from someone better :)

---

### Post by quequotion on 2010-09-01
> **markMDW said:**
> Hi, I've got Ubuntu 10.04 installed on brand new hardware with nvidia card and restricted drivers.  Everything works well but I DO also have the power management warning on bootup.  It usually lasts less than 5 seconds then disappears without any other related problems that I can see.  Do you have a Lauchpad account? If not, go ahead and make one. It's worth the time because it benefits you (at least) three ways: 
1. you can make and participate in bug reports related to your problems, which are generally much faster and more effective than forum support.
2. through participation, you will learn more.
3. you will help make the next ubuntu better.

> As a last resort for Linux salvation you should skip Ubuntu and all other distributions and go directly to Debian Stable, and install the Stable verion, the most tested Linux Distribution out there.. but without any of the latest and greatest Linux software advancements of the last couple of years.   And I'd install it on a clean system without Windows.

Using debian stable is a great idea, like drinking zero-calorie, alcohol-free beer at a party.. Neither are much fun :(

---

### Post by markMDW on 2010-09-01
Thanks for the Tip.  I'm going to setup a launchpad account and add my little puff of wind to the Linux / Ubuntu sails.   ...onward to destiny FSM / FOSS

---

### Post by Uadebisi on 2010-09-10
> **quequotion said:**
> Good luck! I'm just about out of ideas, so hopefully this thread will get some attention from someone better :)

Well...same problem. Just entered the dreaded "Low Graphics Mode" again!

markMDW suggested Xbuntu as a more stable system for basic needs. What do you think?

Thanks for trying quequotion.

---

### Post by Uadebisi on 2010-09-10
Well, one more symptom that I forgot to mention...

Once in a while, when idle, the system just acts as though it shuts down. Meaning that the machine is still on, but the monitor will show the "self-check" window that usually appears after the machine is shut down, & the monitor light indicator will go yellow, from green. This happens to the monitor in sleep mode too, as it should, but in this case when the mouse is moved, the monitor does not come back on.

F2, Shift, alt, delete, etc. have no affect. I need to shut down hard & restart.

---

### Post by clhsharky on 2010-09-10
Uadebisi

Some good reads on Intel 8xx chipset woes, and proposed fixes.
[http://www.phoronix.com/forums/forumdisplay.php?f=44](http://www.phoronix.com/forums/forumdisplay.php?f=44)

Sharky

---

### Post by Uadebisi on 2010-09-10
Thanks Sharky....was there somewhere in particular in that forum that you saw a possible fix? I'd rather cut my lawn with a nail clipper than read thru that forum so any help with specifics would be appreciated.

Although I have an Intel card, others with this problem have Nvidia, so...not sure what that means.  

I don't much care for spending time fixing my computers. Call me crazy, but I just like them to work ;) And that's something I have never seen Ubuntu do. I have a Mac & 2 Windows pcs(one of which is dual-booted with Ubuntu) & have never experienced anything like what I have with Ubuntu. I have a friend who is far more capable than I, who also designs systems for IBM for a living & he struggles with Linux, so I don't feel so bad!

I do like to use Ubuntu for security reasons though, which is why I persist.

---

### Post by Uadebisi on 2010-09-16
Anyone have another opinion in regards to what markMDW said?:

 > Anyhow, even with all that, I still think Xubuntu is Better for a  general purpose computer used mainly for Internet, Email,  Word  Processing and Spreadsheets.  It's seems much less prone to annoyances. 

---

### Post by clhsharky on 2010-09-21
Uadebisi

You may or may not be interested, but others may be. 
Here are instructions on using I8xx legacy driver with Lucid or Maverick.

[http://ubuntuforums.org/showthread.php?t=1543787&highlight=Intel+8xx](http://ubuntuforums.org/showthread.php?t=1543787&highlight=Intel+8xx)


Sharky

---

