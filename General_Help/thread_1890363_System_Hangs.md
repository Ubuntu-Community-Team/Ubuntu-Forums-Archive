---
title: "System Hangs"
date: 2011-12-03
forum: General Help
---

### Post by dsa42 on 2011-12-03
My  system has been randomly hanging, so I left top running (and nothing  else).  When the system hung, it showed "multiload-apple" using 24% of  the CPU  (if I recall correctly) on a two core machine, so that would be  about 50% of one of the cores.  I'm assuming "multiload-apple" is how  top displays "multiload-applet-2"    I didn't see anything else unusual in the 3 top processes (the only ones using over 0% of the CPU).

When I rebooted, there was nothing in the syslog for an hour preceding the hang.

I'm running 11.04 on a Compaq Presario desktop

What can I do in order to get enough information to either solve it or report it to ubuntu-bugs (or both)?

---

### Post by 2F4U on 2011-12-03
Look into the log files:
- /var/log/syslog
- /var/log/Xorg.0.log
- .xsession-errors in your home directory

Is the machine getting hot?
Maybe it is worth running memtest to verify that the RAM is not the problem.

---

### Post by dsa42 on 2011-12-03
> **2F4U said:**
> Look into the log files:
- /var/log/syslog

As I said above, there is nothing in this.


> **2F4U said:**
> - /var/log/Xorg.0.log

OK, thanks.

> **2F4U said:**
> - .xsession-errors in your home directory

OK, I can look, but it hangs even if no one is logged in.  If no one is logged in, then it certainly wouldn't put anything in *MY* home directory, right?

> **2F4U said:**
>  Is the machine getting hot?
Maybe it is worth running memtest to verify that the RAM is not the problem.

No, the machine is not getting hot.  I will run memtest, thanks.

---

### Post by dsa42 on 2011-12-03
> **2F4U said:**
> Look into the log files:
- /var/log/Xorg.0.log

The tail end of the log file before the hang has this.  Note that the  logitecc USB mouse device seems to keep getting removed and re-added.   Why would this be?

> [ 29405.776] (**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 29405.776] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input10/event2"
[ 29405.776] (II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
[ 29405.776] (II) Logitech Optical USB Mouse: initialized for relative axes.
[ 29405.777] (**) Logitech Optical USB Mouse: (accel) keeping acceleration scheme 1
[ 29405.777] (**) Logitech Optical USB Mouse: (accel) acceleration profile 0
[ 29405.777] (**) Logitech Optical USB Mouse: (accel) acceleration factor: 2.000
[ 29405.777] (**) Logitech Optical USB Mouse: (accel) acceleration threshold: 4
[ 29405.778] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/mouse0)
[ 29405.778] (II) No input driver/identifier specified (ignoring)
[ 30636.004] (II) config/udev: removing device Logitech Optical USB Mouse
[ 30636.005] (II) Logitech Optical USB Mouse: Close
[ 30636.005] (II) UnloadModule: "evdev"
[ 30636.005] (II) Unloading evdev
[ 30637.058] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/event2)
[ 30637.058] (**) Logitech Optical USB Mouse: Applying InputClass "evdev pointer catchall"
[ 30637.058] (II) Using input driver 'evdev' for 'Logitech Optical USB Mouse'
[ 30637.058] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 30637.058] (**) Logitech Optical USB Mouse: always reports core events
[ 30637.059] (**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
[ 30637.080] (--) Logitech Optical USB Mouse: Found 3 mouse buttons
[ 30637.080] (--) Logitech Optical USB Mouse: Found scroll wheel(s)
[ 30637.080] (--) Logitech Optical USB Mouse: Found relative axes
[ 30637.080] (--) Logitech Optical USB Mouse: Found x and y relative axes
[ 30637.080] (II) Logitech Optical USB Mouse: Configuring as mouse
[ 30637.080] (II) Logitech Optical USB Mouse: Adding scrollwheel support
[ 30637.080] (**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
[ 30637.080] (**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 30637.080] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input11/event2"
[ 30637.081] (II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
[ 30637.081] (II) Logitech Optical USB Mouse: initialized for relative axes.
[ 30637.081] (**) Logitech Optical USB Mouse: (accel) keeping acceleration scheme 1
[ 30637.081] (**) Logitech Optical USB Mouse: (accel) acceleration profile 0
[ 30637.081] (**) Logitech Optical USB Mouse: (accel) acceleration factor: 2.000
[ 30637.081] (**) Logitech Optical USB Mouse: (accel) acceleration threshold: 4
[ 30637.082] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/mouse0)
[ 30637.082] (II) No input driver/identifier specified (ignoring)


---

### Post by dsa42 on 2011-12-03
> **2F4U said:**
> Maybe it is worth running memtest to verify that the RAM is not the problem.

No errors

---

### Post by dsa42 on 2011-12-03
I saw this at bookup, and saw it in the syslog.  Could this be the problem?

```
Dec  3 15:45:48 ubuntu-desktop kernel: [   18.435886] SP5100 TCO timer: mmio address 0xfec000f0 already in use

```I found this thread which claims that it is **NOT** a problem

```
https://bbs.archlinux.org/viewtopic.php?id=125482
```

---

### Post by oldtimer7777 on 2011-12-03
> **dsa42 said:**
> No errors

I'm running 11.04 too. I had this exact problem on my Intel dual core system.  It would hang after 12 hours of being on and being on stand-by.  The last round of updates seem to resolve this issue for me however.  That was about a week ago using the new Kernel. 

What Ubuntu repos do you currently have enabled?  What does your source.list file look like?

---

### Post by dsa42 on 2011-12-03
> **oldtimer7777 said:**
>  The last round of updates seem to resolve this issue for me however.  That was about a week ago using the new Kernel. 


This has been going on for me for some time, through a couple of Ubuntu versions (maybe since 10.04 ? ).  I am up to date with all updates.

> **oldtimer7777 said:**
>  What Ubuntu repos do you currently have enabled?  What does your source.list file look like?

Here it is without comments:

```

deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe

deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse


deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-proposed restricted main multiverse universe
deb http://extras.ubuntu.com/ubuntu natty main #Third party developers repository

```

---

### Post by oldtimer7777 on 2011-12-03
You can update your repos with the ones listed below and do a sudo apt-get update && sudo apt-get upgrade

Here is how I got mine to look that fixed the freezing up with the latest round of kernel updates (that you can try):

```

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu natty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu natty universe
deb-src http://archive.ubuntu.com/ubuntu natty universe
deb http://archive.ubuntu.com/ubuntu natty-updates universe
deb-src http://archive.ubuntu.com/ubuntu natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu natty multiverse
deb-src http://archive.ubuntu.com/ubuntu natty multiverse
deb http://archive.ubuntu.com/ubuntu natty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu natty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-security main restricted
deb http://archive.ubuntu.com/ubuntu natty-security universe
deb-src http://archive.ubuntu.com/ubuntu natty-security universe
deb http://archive.ubuntu.com/ubuntu natty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
```> **dsa42 said:**
> This has been going on for me for some time, through a couple of Ubuntu versions (maybe since 10.04 ? ).  I am up to date with all updates.



Here it is without comments:

```

deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe

deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse


deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-proposed restricted main multiverse universe
deb http://extras.ubuntu.com/ubuntu natty main #Third party developers repository

```

---

### Post by dsa42 on 2011-12-03
> **oldtimer7777 said:**
> You can update your repos with the ones listed below 


I can't follow that.  What lines in mine need to be replaced, and with what (and why)?


And, thanks for the suggestion!

---

### Post by dsa42 on 2011-12-05
> **dsa42 said:**
> [QUOTE=oldtimer7777;11510455]You can update your repos with the ones listed below I can't follow that.  What lines in mine need to be replaced, and with what (and why)?


And, thanks for the suggestion![/QUOTE]

I have looked very closely at the differences in the two sources.list, but I can not determine what is wrong with mine, nor can I determine what I need to change.  Can anyone help, please?

---

### Post by dsa42 on 2011-12-07
My system is still hanging about once every 24 hours on average.  If anyone has any ideas, or if anyone can help me determine how to take the above suggestion and change my sources.list file, I would appreciate it!

---

### Post by dsa42 on 2011-12-12
> **oldtimer7777 said:**
> You can update your repos with the ones listed below 

I'm still trying to determine if there is anything wrong with my sources.list file, and if so, what it is.  

If not, anyone have any ideas on why my system continues to hang?

---

### Post by oldtimer7777 on 2011-12-12
> **dsa42 said:**
> I'm still trying to determine if there is anything wrong with my sources.list file, and if so, what it is.  

If not, anyone have any ideas on why my system continues to hang?

Rebuild a fresh source.list with the source list generator:

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Then copy completely over your old source.list and click save..

```
sudo *gedit* /etc/apt/*sources*.*list* 
```Then do:

```
sudo apt-get update && sudo apt-get upgrade
```If you recieve PGP key errors, then you will need to add whatever PGP keys are missing. Repeat the previous update upgrade command until their are no more errors and no more updates for your system.

Clean your system out when you are done:

[https://debianhelp.wordpress.com/2011/08/02/how-to-maximize-system-performance-in-ubuntu/](https://debianhelp.wordpress.com/2011/08/02/how-to-maximize-system-performance-in-ubuntu/)

What are your results after you clean out your system?

You can sit there with Htop running on your screen for a while to test your performance.

sudo apt-get install htop

and review your logs if you receive any more issues.

Leave it on until you can replicate the the issue, and track it back with your logs until we have more specific information.

---

### Post by dsa42 on 2011-12-20
Thanks, Oldtimer, for the info.  I have added some repositories for some programs I've loaded.  The web page at

```
 http://repogen.simplylinux.ch/ 
```

doesn't have any information on my system, so I assume it will it wipe my added repositories out.  Also, I don't understand the options in "Ubuntu Branches" nor in "Ubuntu Updates."  I've been using Unix/linux for 20 years, but I don't ever really do anything with the kernel nor with the repositories.


I had four system hangs today, but the system logs don't say anything at the time of the hang.

---

