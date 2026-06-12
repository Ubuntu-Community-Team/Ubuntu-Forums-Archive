---
title: "Karmic (9.10) Nvidia Suspend/Resume Problem"
date: 2009-11-11
forum: General Help
---

### Post by chris_v on 2009-11-11
I recently did a fresh install of Ubuntu 9.10 and have not been able to get my laptop to resume from a suspend while the proprietary Nvidia drivers have been installed.  The driver is the legacy 96.46.13 version since this is an older laptop.  If I disable the driver and use the open driver that Ubuntu installs by default the laptop resumes just fine.  

I have had this problem in every other Ubuntu release I have tried.  In the past I was able to change options in the Grub menu.lst and the acpi-support files (among a few others) and get resume to work, but these files either do not exist now or do not seem to function the same as they did in the past as far as I can tell.  

I don't remember all the details of what I did previously, but I think it had to do with disabling the Nvidia driver before a suspend and restarting it after resume.  Does anybody have any suggestions on how to do this or what else I can try?

---

### Post by laceration on 2009-11-11
I got hibernate to work on my old laptop for the first time ever in 9.10 with Tuxonice.  You need a specially compiled kernel, but Tuxonice has a ppa for a kernel so that is the easy part.  There is a good amount of configuration work to do, I followed a howto at [http://www.ubuntugeek.com/how-to-install-tuxonice-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-tuxonice-in-ubuntu.html).

---

### Post by chris_v on 2009-11-12
I was hoping for an easier solution, but I might give it a try if I can't figure anything else out.  Thanks for the info.

---

### Post by DavidFourer on 2009-11-13
> **chris_v said:**
> I recently did a fresh install of Ubuntu 9.10 and have not been able to get my laptop to resume from a suspend while the proprietary Nvidia drivers have been installed.  The driver is the legacy 96.46.13 version since this is an older laptop.  If I disable the driver and use the open driver that Ubuntu installs by default the laptop resumes just fine.  
I want to try using the open driver if that will give me suspend.  Currently I have a new install of Karmic with
nVidia Graphics Processor Geforce 6150SE nForce 430
nVidia driver V.185
new HP Pavilion p6100z
There are a lot of bug reports on launchpad.net for suspend and nVidia.  Here is the report that apport created when my computer crashed on suspend:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/480765](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/480765)

Can I just go into System > Admin > Hardware Drivers -- and select remove driver?  Are there other steps I have to take to get an open source driver installed?  

DVD video playback on VLC media player looks buggy too.  I'm hoping this solves both problems.

Thanks for your help.

---

### Post by frank_acies on 2009-11-13
check your bios under PCIpnp -> pciexpress and see if you have active state management enabled that seemed to fix my problem with suspend.

---

### Post by DavidFourer on 2009-11-13
> **frank_acies said:**
> check your bios under PCIpnp -> pciexpress and see if you have active state management enabled that seemed to fix my problem with suspend.
Thanks for the suggestion. I went into bios setup (F10) and found nothing about PCIpnp.  The menu is very short.  My older Dell notebook had a lot more options in the bios setup.

---

### Post by laceration on 2009-11-14
An alternative way to see if you have active state is to use the dmesg command.
```
$ dmesg | grep activestate
```
not sure if it is one word -- you might try dmesg | grep active, just to be sure.

---

### Post by DavidFourer on 2009-11-14
> **laceration said:**
> An alternative way to see if you have active state is to use the dmesg command.
```
$ dmesg | grep activestate
```
dmesg found "PCI express" but not Actvie State Power Management, ASPM, or any version of that.
> [    0.321061] pciehp: PCI Express Hot Plug Controller Driver version: 0.4I did a little reading to see where this is going.  This is what I found:
[http://www.lesswatts.org/projects/devices-power-management/pcie.php](http://www.lesswatts.org/projects/devices-power-management/pcie.php)

This machine sleeps (suspend to ram) when running Windows.  Nice feature!
Does it matter that I have an AMD Athlon LE-1660 processor and not an Intel processor?

However, the article says that ASPM (Active State) is often turned off in desktop models to improve performance, and that it might be possible to turn it on.  This is over my head, but it looks like you might be on the right track.

In any case, I really want my desktop computer to suspend.  The other options are leaving it on all day, or booting up for a minute or two at a time.

---

### Post by laceration on 2009-11-14
I think I remember this correctly, Activestate was replaced years ago by acpi, hence the conflict the previous poster had.  You gotta have a pretty old laptop to have Activestate. and maybe 
```
dmesg | grep ASPM
```
is what I was after before.

> In any case, I really want my desktop computer to suspend. The other options are leaving it on all day, or booting up for a minute or two at a time.
It's not worth the grief, with laptops there are important wear issues, but many, incl. myself, just leave our desktops on and just turn off our monitors.  Computers do not use massive energy. If you want to save the planet there are many more effective things to do.

---

### Post by DavidFourer on 2009-11-14
> **laceration said:**
> I think I remember this correctly, Activestate was replaced years ago by acpi, hence the conflict the previous poster had.Thanks for clarifying that.  acpi moved power management from firmware to the operating system, according to wikipedia.  More likely it's the Nvidia.  I won't stress out over it, but if a fix turns up I'll use it.

---

### Post by laceration on 2009-11-14
ACPI was created by a consortium of computer manufacturers, dell, hp, toshiba,etc.  It is just about universal.  I wouldn't blame Nvidia, I'd blame the very mediocre Linux implementation of it.  A better implementation, that should be part of the kernel, is Tuxonice(see my 1st post in this thread).

---

### Post by kryptic_mind on 2009-11-30
I too would like to follow the how-to at [http://www.ubuntugeek.com/how-to-install-tuxonice-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-tuxonice-in-ubuntu.html), however I cannot add the key using these commands from terminal:

```

gpg --keyserver keyserver.ubuntu.com &#8211;recv DEC8FAAC
gpg --export --armor DEC8FAAC | sudo apt-key add &#8211; && sudo apt-get update

```

I get:
usage: gpg [options] [filename]
for the first line.

I also tried this:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DEC8FAAC
```
from: [http://launchpad.net/~tuxonice/+archive/ppa]("http://launchpad.net/~tuxonice/+archive/ppa") with no luck.
I get:

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys DEC8FAAC
gpg: requesting key DEC8FAAC from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

So I'm pretty much stuck here.

Any help would be greatly appreciated!

---

### Post by laceration on 2009-11-30
You are not doing anything wrong.  The keyservers just do not function sometimes.  Keep trying and it will work.

In Karmic there is a new add-apt-repository command. The whole process--adding the repositories and the key-- is as simple as this:
```
$ sudo add-apt-repository ppa:tuxonice
```

---

### Post by kryptic_mind on 2009-11-30
Excellent, worked first time:

```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv CB62975AF7A2FA557F9E83A2DAC45EC9DEC8FAAC
gpg: requesting key DEC8FAAC from hkp server keyserver.ubuntu.com
gpg: key DEC8FAAC: public key "Launchpad PPA for TuxOnIce" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

```

Thank you for the info!

However still unable to install tuxonice, as only the tuxonice-userui package is available.
Can't imagine why.

Suspend at this moment works only with suspend to ram, while hibernate doesn't work at all, Suspend to ram only works once though, have to shutdown next time, which is managable, but a real pain! Would like to get tuxonice working as soon as possible.

---

### Post by walt.smith1960 on 2009-12-02
One was upgraded from 9.04 and one was a fresh install. I replaced a Radion 9550 w/ 256 Mb. RAM card. The Radeon worked great regarding standby/resume but graphics performance was poor and effects could not be enabled.   I just installed an AGP  card from BFG running an Nvidia 6200OC GPU. This is when the resume problems surfaced. The system would suspend fine and would appear to resume-lights & fans on, keyboard lights on, WiFi adapter lights on but the screen was totally dark. The light on the monitor inidicated there was a video signal but nothing was displayed. This solution is not time tested and I will revise this post if my results change. The system is  a desktop with a Gigabyte MB 2004 vintage Athlon XP processor with AGP graphics & 1 Gb. RAM I had to edit 2 files. 


[LIST]
[*]Enable the latest open Nvidia drivers <system> <administration> <hardware drivers> Version 185
[*]Open a Terminal and type gksu gedit /etc/default/acpi-support. I found this file to be a lot different in the fresh install than in the upgrade so this line location will vary.  Look for a line which says
[*]MODULES=" ". Between the " " put the word nvidia (or fglrx if you're having this problem with ATI). Save the file.
[*]In gedit open /etc/x11/xorg.conf and add this line to the "devices" section:  Option     "NvAGP"      "1" and save.
[*]Exit terminal and reboot.
[/LIST]
I did see mention of blacklisting Intel AGP but didn't do that and so far after 6 or 8 suspend/resume cycles all is well. *Keeps fingers crossed.*
This information was harvested from various posts found via searches. I'm a Newb and  have no real idea WHY it works, it just seems to:D.

UPDATE:
This hasn't gotten better:sad:. I've kept Karmic updated and this may have been a mistake. When I wrote the above the resume function was pretty reliable. The only time it would sometime fail is if it was on resume for several hours. The time my system can be in suspend and still resume seems to have gotten shorter. I was wondering about a progressive hardware failure but suspend and resume function correctly in WinXP so that seems to eliminate hardware issues. I'm going to persevere on this.

---

### Post by laceration on 2009-12-02
kryptic_mind,

if this is not enough of a bitch already, the reason tuxonice is not coming up for you is because of the kernel update in the last few days.

Open synaptic and do a search on "linux".
Scroll down and find

linux-headers-2.6.31-15
linux-headers-2.6.31-15-generic
linux-image-2.6.31-15
linux-libc-dev

For each of them from the menu select package->force version, in the drop down box select the version that has tuxonice in it.  Apply the changes and reboot.  Since this is a downgrade You will forever have a "you have 4 updates", be sure not to install them.

PPA creators are supposed to avoid this type of thing by versioning properly, which it seems like tuxonice did...until the update.

---

### Post by kryptic_mind on 2009-12-05
thank you for the info.
will proceed once i have some time on my hands.

---

### Post by matt06 on 2009-12-06
> **walt.smith1960 said:**
> 
[LIST]
[*]Enable the latest open Nvidia drivers <system> <administration> <hardware drivers> Version 185
[*]Open a Terminal and type gksu gedit /etc/default/acpi-support. I found this file to be a lot different in the fresh install than in the upgrade so this line location will vary.  Look for a line which says
[*]MODULES=" ". Between the " " put the word nvidia (or fglrx if you're having this problem with ATI). Save the file.
[*]In gedit open /etc/x11/xorg.conf and add this line to the "devices" section:  Option     "NvAGP"      "1" and save.
[*]Exit terminal and reboot.
[/LIST]
I did see mention of blacklisting Intel AGP but didn't do that and so far after 6 or 8 suspend/resume cycles all is well. *Keeps fingers crossed.*
This information was harvested from various posts found via searches. I'm a Newb and  have no real idea WHY it works, it just seems to:D.

I've tried all of this and more with a GeForce4 MX 4000 AGP and the 96.43.13 drivers.  If I add the option "NvAGP" "1" the system will suspend and resume correctly, but the video performance suffers after resume.  The poor performance is noted [over at Launchpad]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/34043") for the 173 drivers, but I couldn't find any bug reports in nvidia-glx-96.

Tuxonice looks spectacular for hibernation, but I need suspend/resume for my CF card system.

---

