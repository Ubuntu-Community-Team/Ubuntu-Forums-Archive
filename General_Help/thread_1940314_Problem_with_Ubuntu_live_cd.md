---
title: "Problem with Ubuntu live cd"
date: 2012-03-13
forum: General Help
---

### Post by PhantomTurtle on 2012-03-13
I recently got a new computer. When I try the Ubuntu live cd, my computer would boot on the live cd. First I get a blank purple screen and then my monitor goes into power save mode. And after that nothing. I do have Windows 7 on it right now. So I was wondering if there was a way I could dual-boot with Windows. My system specs are,

Processor: AMD A4-3400 APU with Radeon(tm) HD Graphics 2.70 GHz
RAM: 4GB
Display Adapter: AMD Radeon HD 6410D
Motherboard: Gigabyte GA-A55M-DS2

---

### Post by raja.genupula on 2012-03-13
[http://ubuntuforums.org/archive/index.php/t-1560792.html](http://ubuntuforums.org/archive/index.php/t-1560792.html)

---

### Post by oldfred on 2012-03-13
You probably have a video issue and just need a setting.

To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option. You can also try both Generic or Radeon settings from below.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by PhantomTurtle on 2012-03-13
> **oldfred said:**
> You probably have a video issue and just need a setting.

To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option. You can also try both Generic or Radeon settings from below.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

I tried "radeon.modeset=0" and "nomodeset". With both, it would boot up and give me a command line. What do I do after this?

---

### Post by raja.genupula on 2012-03-13
> **PhantomTurtle said:**
> I tried "radeon.modeset=0" and "nomodeset". With both, it would boot up and give me a command line. What do I do after this?

```
sudo start lightdm
```

---

### Post by oldfred on 2012-03-13
I do not know with Radeon as I have nVidia.

Have you tried updating system, booting from recovery mode (second line) which then semi-automates some of the updates and offers some choices to experiment with.

Have you tried this to see what error graphics gives?
startx

you can run these to make sure it is fully updated (# is comment-do not type comments):

#if not chroot use: 
sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by PhantomTurtle on 2012-03-13
> **raja.genupula said:**
> ```
sudo start lightdm
```

When I type this command I get:
```
ubuntu@ubuntu:~$sudo start lightdm
lightdm start/running, process 2986
```
Thats it after that nothing happens.

> **oldfred said:**
> I do not know with Radeon as I have nVidia.

Have you tried updating system, booting from recovery mode (second line) which then semi-automates some of the updates and offers some choices to experiment with.

Have you tried this to see what error graphics gives?
startx

you can run these to make sure it is fully updated (# is comment-do not type comments):

#if not chroot use: 
sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

This is on a Ubuntu 11.10 live cd, can I still do those other than startx.

---

### Post by PhantomTurtle on 2012-03-14
Does anybody have any other solutions? Ubuntu 11.04 and lower will work, but Ubuntu 11.10 and the Ubuntu 12.04 Beta 1 does not work either.

---

### Post by AlexanderDGreat on 2012-03-21
@PhantomTurtle

It's a litte SADDENING and FRUSTRATING, I have the SAME motherboard with you sir, and Ubuntu 10.04 LTS, booted because I attached a Radeon videocard forgot what model just trying.

You know what? **Ubuntu is running in LOW graphics mode** it says.

**And the LAN is NOT working.**

And maybe tens more the devil knows s^*t, what's not working.

I went to Gigabyte website, _they don't have LINUX_ as Choice of OS.

It's a little sad that I'm using an _AMD _board + APU, and a videocard that's _ATI_.

BOTH of these hardwares are Ubuntu's disease, cancer, or worst nightmare.

_It's very down-heartening, (dunno if it's even a word) - that the only thing PREVENTING me to UPGRADE my computer is because of UBUNTU._

It's so sad, sickening, mixed emotion of love, hate and disgust with Ubuntu.

With Windows XP - it's working 100% fine, I just install CD came with motherboard, download ATI videocard driver.

Zoom, I'm video editing in a matter of seconds.

**_OK let me be honest, Ubuntu sucks._**

**Ubuntu when can you be at par, at least, with Windows XP?**

---

### Post by PhantomTurtle on 2012-03-21
> **AlexanderDGreat said:**
> @PhantomTurtle

It's a litte SADDENING and FRUSTRATING, I have the SAME motherboard with you sir, and Ubuntu 10.04 LTS, booted because I attached a Radeon videocard forgot what model just trying.

You know what? **Ubuntu is running in LOW graphics mode** it says.

**And the LAN is NOT working.**

And maybe tens more the devil knows s^*t, what's not working.

I went to Gigabyte website, _they don't have LINUX_ as Choice of OS.

It's a little sad that I'm using an _AMD _board + APU, and a videocard that's _ATI_.

BOTH of these hardwares are Ubuntu's disease, cancer, or worst nightmare.

_It's very down-heartening, (dunno if it's even a word) - that the only thing PREVENTING me to UPGRADE my computer is because of UBUNTU._

It's so sad, sickening, mixed emotion of love, hate and disgust with Ubuntu.

With Windows XP - it's working 100% fine, I just install CD came with motherboard, download ATI videocard driver.

Zoom, I'm video editing in a matter of seconds.

**_OK let me be honest, Ubuntu sucks._**

**Ubuntu when can you be at par, at least, with Windows XP?**

Maybe I should have posted this a couple of days ago cause I fixed the problem with my computer(sorry about that). How I fixed it? Well I'm not exactly sure but I think its some kind of problem with the splash screen because I pressed the "delete" key a couple of times and the black screen went away and I got the(I'm not sure what to call this) the command line output and then when I pressed delete again and I could see the splash screen. After that it just loaded up and I was on my way. I installed Ubuntu 12.04 beta, which worked better than 11.10, installed additional graphics drivers and I was almost good. There was also a sound problem, but for that you just need to download the linux realtek HD Audio drivers from their website and install them which was really easy. And now compiz effects work, I can do everything I could do with Windows and it just works great.  I'm sorry to hear that you have had problems with Ubuntu on GIGABYTE motherboards. They should really make Linux drivers, since they are pretty big supplier of motherboards and have many users buy their products, the least they can do is make a couple of Linux drivers. So don't hate Ubuntu, hate Gigabyte for not supporting Linux. I hope you continue to use Ubuntu if this can help fix your problem. I'm very sorry for the long post but I hope this solution works for you.

The sound drivers are here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=24&Level=4&Conn=3&DownTypeID=3]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=24&Level=4&Conn=3&DownTypeID=3")

LAN works fine for me, I would suggest you try the Ubuntu 12.04 beta or wait till April 26th for the release and do a clean install since upgrading can cause some problems. 
I Hope that helps you:)

EDIT - If you need any more help post on this thread or send me a PM.

---

### Post by AlexanderDGreat on 2012-03-21
My hardware:

Processor: AMD A6-3500 APU with Radeon(tm) HD Graphics 2.70 GHz
RAM: 4GB
Display Adapter: AMD Radeon HD 5450
Motherboard: Gigabyte GA-A55M-DS2

*********
> So don't hate Ubuntu, hate Gigabyte for not supporting Linux. I hope you continue to use Ubuntu if this can help fix your problem. I'm very sorry for the long post but I hope this solution works for you.

I guess, you showed me. I stand corrected.

THANK YOU.

I will try to DO everything you TOLD me sir and I will POST BACK what will happen. I will wait up to April 26 2012, Ubuntu Release, if I can.

I guess I needed to CLOSE MY MOUTH and THINK before OPENING IT QUICKLY. :)

Thank you sir.

---

### Post by PhantomTurtle on 2012-04-26
For all the Ubuntu users that have this problem, it has been fixed in Ubuntu 12.04. The Ubuntu 12.04 LTS live CD booted extremely well. No problems at all. I am posting this from Firefox on the live CD. Sound works and it got the correct resolution for my monitor which did not happen last time. It is also worth noting that I am using the 64-bit version. Additionally I have attached a screenshot from the live CD.

td:lr version: It works.

---

