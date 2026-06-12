---
title: "Big ATI graphics trouble after 9.10 update"
date: 2009-10-30
forum: General Help
---

### Post by Mekzholan on 2009-10-30
After updating my ATI Radeon Mobility 9000 based laptop from Kubuntu 9.04 to 9.10 I have severe problems with the system. It seems to boot correctly and even to switch to the native resolution (1400x1050) - but it shows the error message
> Ubuntu is running in low-graphics mode
Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.Using different xorg.conf files (none, a version with "vesa", a version with "ati" or a version with "ati" and lots of detailed information) did't help :(
All that I can do is to select the option to go to the text console. Running "startx" there starts an KDE session just as I'd expect it to (compiz is unusable slow and has some big artefacts; disabling it, I can at least work with the system although it's feeling sluggish)

A hint for helping might be this parts of the /var/log/kdm.log:
```
X.Org X Server 1.6.4
Release Date: 2009-9-27
[...]
(II) [KMS] drm report modesetting isn't supported.
[...]
error setting MTRR (base = 0xd8000000, size = 0x04000000, type = 1) Invalid argument (22)
 ddxSigGiveUp: Closing log
frontend: cannot connect to X server
debconf: unable to initialize frontend: Kde
debconf: (DISPLAY problem?)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe -- /usr/bin/X  -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux yoda 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: root=UUID=2f7a1c63-c3e9-4e88-a42c-3cb97715bb6a ro quiet splash locale=de_DE
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@)
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Fri Oct 30 18:56:58 2009
(++) Using config file: "/etc/X11/xorg.conf.failsafe"

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.

 ddxSigGiveUp: Closing log
Warning:  Failsafe mode was already attempted within 30 seconds.
Warning:  Falling back to gdm to report the issue.
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.

 ddxSigGiveUp: Closing log
^M
waiting for X server to shut down
Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133d6b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7d35]
2: [0xe45400]
3: /usr/lib/xorg/modules//libshadow.so(shadowRemove+0x4e) [0x87ff2e]
4: /usr/lib/xorg/modules//libshadow.so [0x8803e4]
5: /usr/bin/X [0x80c6b3e]
6: /usr/bin/X [0x8111bac]
7: /usr/bin/X [0x811de9c]
8: /usr/bin/X [0x812439c]
9: /usr/bin/X [0x80cf6ce]
10: /usr/lib/xorg/modules/drivers//vesa_drv.so [0x5babb8]
11: /usr/bin/X [0x80c784c]
12: /usr/bin/X [0x816143e]
13: /usr/bin/X [0x80e17f5]
14: /usr/bin/X [0x80cc192]
15: /usr/bin/X [0x814a890]
16: /usr/bin/X [0x817bf49]
17: /usr/bin/X [0x8144516]
18: /usr/lib/xorg/modules/extensions//libglx.so [0x49ed0a]
19: /usr/bin/X(main+0x428) [0x80725a8]
20: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x1a6b56]
21: /usr/bin/X [0x80719c1]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 11

```

Thanks for any help!

---

### Post by QIII on 2009-10-30
What I would try (your mileage may vary) is installing Catalyst using Synaptic.

ATI rushed to get Catalyst 9.10 out for inclusion in Karmic.  They were tired of looking at nVidia's back side from the back of the Linux pack.

That is what I am using on my ATI graphics machine.

But you might want to check out ATI's website and see if your card is supported.

---

### Post by Mekzholan on 2009-10-30
> **QIII said:**
>  But you might want to check out ATI's website and see if your card is supported.
No, my Mobility Radeon 9000 isn't supported by the new Catalyst - I'd have to use an ancient 8.28.8 of August 2006...

I won't try that, my system is already quite broken (and my last attempt to use the fglrx 1-2 years ago went bad enough so that I'm not eager to hurt myself again)

---

### Post by QIII on 2009-10-30
Despite my Catalyst 9.10 praise, I think ATI diddled the pooch by dropping support for the "legacy" cards.

---

### Post by erpan on 2009-11-01
> **QIII said:**
> Despite my Catalyst 9.10 praise, I think ATI diddled the pooch by dropping support for the "legacy" cards.

I have ubuntu 9.10 and lenovo t500 with hd3650 and when enabling desktop effects  it gets really slow, if minimizing firefox and opening it again takes over 5 sec. If i disable desktop graphics it opens directly when clicking it. So i will go for none effects otherwise it feels as slow as VISTA. 

At least my 11n network seems to work with 9.10 , later i will try to send files to my NAS if it works it means 9.10 is the first distro that has 11n support. As with previous ubuntu the computer made freezes when sending large or many files thrue the network. Even when installing INTELS own driver on 9.04 i got 1mb-10mb  at 2.4ghz (mostly 1mb)  and 18-24mb at most  at 5ghz.

---

### Post by Kaneda187 on 2009-11-01
I have a mobility radeon x1400 how can find out if its supported?

---

### Post by Mekzholan on 2009-11-02
On the ATI page. Have a look what driver version it's telling you you are gonna need.
If it's 9.10 you are fine and you can use the current driver. If it's another one (e.g. 8.28.8 like mine, you are out of luck)

---

### Post by P4man on 2009-11-02
> **QIII said:**
> Despite my Catalyst 9.10 praise, I think ATI diddled the pooch by dropping support for the "legacy" cards.

I actually think they did the right thing. As I understand it they disclosed all the specifications for those older cards allowing the oss community to build and maintain those drivers. 

I dont know how good they are at this point, perhaps ati dropped support a bit too early before the oss drivers were mature enough, I cant judge that, but problems with oss drivers can (and eventually will) be solved, problems with binary drivers can not and keep us hostage to the software support of the ATIs, nVidia's, Creative labs ([remember the X-Fi?]("http://www.phoronix.com/scan.php?page=article&item=creative_xfi_gift&num=1")), Broadcoms (wifi, network) and Adobe's (flash) of this world.

If legacy support for ATI cards isnt good, I wouldnt blame ati for it.

---

### Post by Kaneda187 on 2009-11-02
I downloaded the driver from the ati site but it wont install. ant the terminal closes befor i can read the error.....:(

---

### Post by Kaneda187 on 2009-11-02
I got the out put from the terminal:

```
kaneda@facon-core:~$ cd /home/kaneda/Desktop
kaneda@facon-core:~/Desktop$ chmod +x ati.run
kaneda@facon-core:~/Desktop$ sudo ./ati.run
[sudo] password for kaneda: 
Created directory fglrx-install.lbVAbj
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-14-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.lbVAbj
kaneda@facon-core:~/Desktop$ 

```

Any ideas?

---

### Post by Kaneda187 on 2009-11-02
bump

---

### Post by ssri on 2009-11-02
> **Kaneda187 said:**
> I got the out put from the terminal:


Any ideas?


Catalyst 9.3 is installable only on linux setups that have at most xserver 1.5.x and kernel 2.6.28.  It is possible to install it in Jaunty by downgrading its xserver from 1.6->1.5.2.  However, Karmic ships kernel 2.6.31, and the only patch I've seen for Catalyst 9.3 is for kernel 2.6.29.  If you want to stay on Karmic, short of downgrading both the kernel and xserver, you have to have stick with the opensource drivers.

---

### Post by godspiral on 2009-11-03
> **ssri said:**
> Catalyst 9.3 is installable only on linux setups that have at most xserver 1.5.x and kernel 2.6.28.  It is possible to install it in Jaunty by downgrading its xserver from 1.6->1.5.2.  However, Karmic ships kernel 2.6.31, and the only patch I've seen for Catalyst 9.3 is for kernel 2.6.29.  If you want to stay on Karmic, short of downgrading both the kernel and xserver, you have to have stick with the opensource drivers.

thank you... found this searching for which driver to use.  basic things seemed to work fine with OSS one (9600pro), but had to mess it all up hoping other drivers were better.

---

### Post by Another Monkey on 2009-11-03
Kinda glad to see I am not the only one suffering.  My Mobility Radeon 9000 was running fine under Jaunty (Compiz, the whole shooting match).

I'm considering dropping back to Jaunty at the moment.

---

### Post by ssri on 2009-11-03
> **Another Monkey said:**
> Kinda glad to see I am not the only one suffering.  My Mobility Radeon 9000 was running fine under Jaunty (Compiz, the whole shooting match).

I'm considering dropping back to Jaunty at the moment.

Here is the guide to get Catalyst 9.3 to work in Jaunty:

[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)


It worked for me like a charm.  However, I would recommend this only to people who are comfortable with working in the terminal, as if this gets screwed up, you will have to use the commandline to revert your setup back to its original state.

---

### Post by Kaneda187 on 2009-11-07
where do I get the open source drivers?

---

### Post by P4man on 2009-11-07
You already have them, they are included.

---

### Post by Kaneda187 on 2009-11-10
they dont work....:(

---

### Post by albyone on 2009-11-15
After upgrading from my existing Ubuntu 9.04 installation to the latest 9.10, my graphics switched to the default - slow - mode. None of the advanced graphics functions worked anymore.

The fix that worked for me was to install the new Catalyst driver:

[http://www2.ati.com/drivers/linux/ati-driver-installer-9-10-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-9-10-x86.x86_64.run)

After downloading the file, do a chmod 777 ati-driver-installer-9-10-x86.x86_64.run on the file and then run:

sudo ./ati-driver-installer-9-10-x86.x86_64.run

After it finished the installation, I shutdown my laptop, and switched it back on and all was working.

Hopefully someone will find this useful.

---

### Post by Kaneda187 on 2009-11-16
> **albyone said:**
> After upgrading from my existing Ubuntu 9.04 installation to the latest 9.10, my graphics switched to the default - slow - mode. None of the advanced graphics functions worked anymore.

The fix that worked for me was to install the new Catalyst driver:

[http://www2.ati.com/drivers/linux/ati-driver-installer-9-10-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-9-10-x86.x86_64.run)

After downloading the file, do a chmod 777 ati-driver-installer-9-10-x86.x86_64.run on the file and then run:

sudo ./ati-driver-installer-9-10-x86.x86_64.run

After it finished the installation, I shutdown my laptop, and switched it back on and all was working.

Hopefully someone will find this useful.


What card do you have?

---

