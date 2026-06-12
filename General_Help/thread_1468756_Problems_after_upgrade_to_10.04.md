---
title: "Problems after upgrade to 10.04"
date: 2010-05-01
forum: General Help
---

### Post by Majorflam on 2010-05-01
Hi, I've just upgraded to 10.04. Now I have some problems. I can't resize or move any windows. Some windows don't even have the options on the top right.

Also, if I try to "show desktop" I get an error message: "Your window manager doesn't support the show desktop button"

Any help appreciated.

---

### Post by BrokeMahPC on 2010-05-01
I have read a similar post - can't remember exact details - I think it's a graphics/video driver issue.
Can you list what hardware you have and someone will be able to help.
To determine your video card manufacturer, execute  the following in the console or a terminal window: [FONT=monospace]
[/FONT]```
lspci | grep VGA
```

Have a look here to see if there is any advice for your card.
[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)
not much help for intel - there is a separate section - search for it in the help pages.

Upgrade or fresh install? Please also say how you upgraded or installed.

---

### Post by Majorflam on 2010-05-01
> 01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9200M GS] (rev a1)

Thanks for the reply.

---

### Post by Majorflam on 2010-05-01
Oh, and it was an upgrade from previous release via update manager.

---

### Post by BrokeMahPC on 2010-05-01
I'm an ATI man so can't help with Nvidia - sorry.
try:
glxinfo | grep direct
should give: direct rendering: Yes
(If glxinfo is not installed - sudo apt-get install mesa-utils)

Did you enable any proprietary drivers?
Did you try to revert to the default driver without properly un-installing the proprietary?
[https://wiki.ubuntu.com/X/Troubleshooting/NvidiaDriverSwitching](https://wiki.ubuntu.com/X/Troubleshooting/NvidiaDriverSwitching)
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

Would it be possible to do a clean install - it's often the best option?
Are you absolutely sure your driver supports your video card? read the release notes.

In the ATI world, similar problems to your were solved with answers to the above. I had a window decoration failure similar to yours because of conflicting drivers.

Good luck!

---

### Post by BrokeMahPC on 2010-05-01
see this - files in /home directory cause window decs failure:
[http://ubuntuforums.org/showthread.php?t=983544&highlight=window+decoration+nvidia&page=2](http://ubuntuforums.org/showthread.php?t=983544&highlight=window+decoration+nvidia&page=2)

running 2 window managers at the same time?
[http://ubuntuforums.org/showthread.php?t=1461293&highlight=window+decoration+nvidia](http://ubuntuforums.org/showthread.php?t=1461293&highlight=window+decoration+nvidia)

---

### Post by Majorflam on 2010-05-02
I've disabled the Nvidia driver, but the problem persists.

I'd be happy to do a fresh install. I'm dual booting with windows, so I'm assuming if I download and boot Lucid from CD it won't affect the dual boot or the Windows install?

Hopefully someone could give a fix for the current setup, but if I need to re-install I will.

Thanks for all your help so far.

---

### Post by dino99 on 2010-05-02
clean your system:

- check your sources.list: you only might have Lucid genuine repo, no exotic one or ppa
- update
sudo apt-get install -f

install gconf-cleaner and use it (yes to all)

sudo dpkg --configure -a

---

### Post by Majorflam on 2010-05-02
> **dino99 said:**
> clean your system:

- check your sources.list: you only might have Lucid genuine repo, no exotic one or ppa
- update
sudo apt-get install -f

install gconf-cleaner and use it (yes to all)

sudo dpkg --configure -a

Hi,

How do I do the above? What are the commands?

TIA

---

### Post by dino99 on 2010-05-02
> **Majorflam said:**
> Hi,

How do I do the above? What are the commands?

TIA

Join Date: Apr 2007
Beans: 118            :confused:

goto synaptic, check the repo tab and edit repos

---

### Post by Majorflam on 2010-05-02
I've checked synaptic and don't know which sources to check. Just because I've used Ubuntu for a while doesn't mean I'm fully versed in all this. Usually it just works, which is why I use it.

OK, I ran the cleaner and rebooted but the problem persists.

** Edit **

I've noticed that F11 isn't expanding the Google Chrome window either.

---

### Post by BrokeMahPC on 2010-05-02
_Clean Install_
If you do a clean install and you have dual boot you need to choose "Specify partitions manually (advanced)" in the install options.
Choose (click to select it) the partition where you have Ubuntu installed and tick the box to format it and mount it as /
If you have a separate home partition and want to keep it - mount it as /Home but DON'T format it.
Have a quick search and read some guides on "Ubuntu Specify partitions manually"
Look at the bottom of this page:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Reinstalling will wipe the data on the ubuntu partition so back it up
Back up your windows data - if you make a mistake you could lose that too.

---

### Post by BrokeMahPC on 2010-05-02
Check the software sources by:
```
gedit /etc/apt/sources.list
```You type this in a terminal - applications-accessories-terminal
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

It should look like this and it should all be about lucid - you may have skype or medibuntu in there too. If it mentions karmic or jaunty or some other weird source it need fixing. Also sheck System - Admin - software sources - Other software tab

```
#deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype
```

---

### Post by BrokeMahPC on 2010-05-02
Did you run these commands?
sudo apt-get install -f
sudo dpkg --configure -a

suggested by Dino? Good idea - they fix broken packages.

---

### Post by dino99 on 2010-05-02
> **BrokeMahPC said:**
> Did you run these commands?
sudo apt-get install -f
sudo dpkg --configure -a

suggested by Dino? Good idea - they fix broken packages.

Feeding on Sunday is like spoon feeding , to much babies around  :(

---

### Post by BrokeMahPC on 2010-05-02
If all that is ok - you may need to redo all the drivers:
(Be nice Dino! :))
**Problem:  Need to fully remove -nvidia  and installing or reinstall -nouveau from scratch**

 Here is a recipe which removes  all old video drivers, and reinstalls nouveau: 

  sudo nvidia-settings --uninstall
  sudo apt-get remove --purge nvidia*
  sudo apt-get remove --purge xserver-xorg-video-nv xserver-xorg-video-nouveau
  sudo apt-get install nvidia-common
  sudo apt-get install xserver-xorg-video-nouveau
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
Then _reboot_ your system and when it comes up it will be  running with nouveau.
I'm not an Nvidia expert at all but do you need the Nvidia drivers? Might be best to stick with nouveau for now? ATI have not caught up with Lucid yet and I am sticking to the default Radeon driver.

---

### Post by Majorflam on 2010-05-02
Guys, thanks for all the help... I'll go for the clean install because I had problems with the other advice.

Dino, This is a help forum. There is nothing in the rules to state that you can't ask for help if you have surpassed a certain amount of posts, or been registered for any length of time. If you don't enjoy helping people, then why are you even posting?

---

### Post by earthlingform on 2010-05-02
A New User to Umbutu I am dual booting a Dell 1525 with XP Home Media Edition & Lucid Lynx 10.04, very cool & fairly smooth up to
wireless access. 

Need to import files to machine or update drivers but don't have a 
Hard Line available. Any idea's would be appreciated.

---

### Post by Majorflam on 2010-05-02
> **BrokeMahPC said:**
> _Clean Install_
If you do a clean install and you have dual boot you need to choose "Specify partitions manually (advanced)" in the install options.
Choose (click to select it) the partition where you have Ubuntu installed and tick the box to format it and mount it as /
If you have a separate home partition and want to keep it - mount it as /Home but DON'T format it.
Have a quick search and read some guides on "Ubuntu Specify partitions manually"
Look at the bottom of this page:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Reinstalling will wipe the data on the ubuntu partition so back it up
Back up your windows data - if you make a mistake you could lose that too.

I'm at the screen for specify partitions manually, but I don't have the choice to format a partition.

My choices are: Change, Delete, Revert.

---

### Post by earthlingform on 2010-05-02
Seems a Hard Connection (read Network Cable) cured my ills by downloading and installing 2 driver files to cover the wireless card. 
Nothing more at this time. 

AM POSTING IN LINUX FROM THE MACHINE DISCUSSED!!!

Feel a bit like a kid, doing a little work to make this functional
is almost fun...
Of course, this is an old machine I am experimenting with so total fail would not be absolute.

---

### Post by Majorflam on 2010-05-02
I've done the re-install and now the problem is gone.

Thanks for all the help.

---

