---
title: "Resolution Package Issues or?"
date: 2010-03-11
forum: General Help
---

### Post by killwin7 on 2010-03-11
Hi all,

I'm new to linux, but can usually find my way around. I've come up on a block, I would very much appreciate your patience and any help. So here it goes:   

                 ** Scenario:** New hp laptop with toshiba HD (never would have bought it had I known it was toshiba), I think starts to fail.  Running Win7.  Before things went really south I got a external HD and dual WUBI boot with kubuntu karmic or whatever the latest version. 

then one morning the thing just rebooted by itself i guess after a crash and it would not boot into windows at all, something about cannot find bootable device or NTFS not found,  I tried all modes, safe, with without prompt , nothing, it would try to boot then I would get that dreaded blue screen with the yellow/white type, but it would flash by too fast to read it, and then it would reboot again after crashing, thankfully due to the dual boot install of kubuntu i had the option of starting that desktop , so only windows would not start, under  linux, kubuntu would now load and i could operate the desktop environment no problem, but i did notice at start up it wasn't the normal start up, it did some additional steps but i have no clue what those were/are. 

thats the back round, sorry for the length but I thought full disclosure is best in this case.

**the error message i get now : 'dependency resolution failed, a package dependency could not be found'.**

 more details : 
  p, li { white-space: pre-wrap; }  '**There are broken dependecies on your system. Please use an advanced package manage e.g. Synaptic or aptitude to resolve this situation."**


so i tried command lines to install/uninstall synaptic and then adept and this is what i get:


 [SIZE=3]after synaptic command line install attempt: [/SIZE]



                                  You might want to run `apt-get -f install' to correct these:
 The following packages have unmet dependencies:
   antlr: Depends: default-jre-headless but it is not going to be installed or
                   java1-runtime-headless or
                   java2-runtime-headless
   libjogl-java: Depends: java-gcj-compat or
                          java1-runtime or
                          java2-runtime
   libworldwind-java: Depends: sun-java5-jre but it is not installable or
                               sun-java6-jre but it is not going to be installed or
                               openjdk-6-jre but it is not going to be installed
   sun-java6-bin: Depends: sun-java6-jre (= 6-15-1) but it is not going to be installed
   wine: Depends: binfmt-support (>= 1.1.2) but it is not going to be installed
         Recommends: ttf-liberation but it is not going to be installed
         Recommends: winbind but it is not going to be installed
         Recommends: wine-gecko
         Recommends: ttf-mscorefonts-installer but it is not going to be installed
 E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
  
[SIZE=4]**after following above:**[/SIZE]

 E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
 E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


[SIZE=4]and here is my sources list:[/SIZE]


deb cdrom:[Kubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to                  
# newer versions of the distribution.                                                      

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

Any help would be greatly appreciated and  thank you in advance for your patience.

---

### Post by alfplayer on 2010-03-11
"apt-get -f install" should be run as root. Did you run that command as root? The windows blue screen issue may be a different issue.

---

### Post by killwin7 on 2010-03-12
ok issue resolved, sort of, did a bunch of steps in root, could not repeat them, something with java,  then rebooted, nothing would load, thought that was it then, time for a new drive (i could not restore to fac orig condition the option was not lit no matter what i tried),  anyway then I crt-alt-delt - ed a couple of times and tried to load win7 which failed repeating the same pattern, and i crossed my fingers and on the next reboot dialled kubuntu and this time it loaded AND the error messages in the previous post is now gone.  I still cant find adept, synaptic or wine nor can i browse java applets, i tried all the fixes, I dont care though, i thing the main issue was the error messages and that is now fixed via if i remember correctly a  sudo update command. 

I am sorry if this thread is not specifically helpful to anyone else, but your advice re root  install is what i believed was the key, thank you!

---

### Post by killwin7 on 2010-03-12
just wanted to add that i was able to root update, which seems to have resolved the package issues, was able to install adept, synaptic package (via command line) manager and then via synaptic i was able to get wine (the regular kde package manager would identify but not load), but i was able to get wine via synaptic and now i am able to use the exe program I wanted to use, which was what this whole thing started with.  I was unable to do any of that because of package issues which resulted in the resolution error message which suggested the fix via adept or synaptic which were missing or not accessible due to the original kde manager being unable to get them for me, so the sudo root update command worked and after that the rest.

as of now the kubuntu desktop runs fine, wine runs perfectly, still no java, got some packages from synaptic , but i dont really care about that, java is annoying anyway, no error messages, the only reason i wanted java to work was because the win exe file i wanted would not open in the absence of wine but now that is no longer a concern.  does linux have a self correcting methodology or protocol? i mean i did a couple of things but i think that update largely fixed itself.

I gotta say, this is what i love about linux, i learned a lot, did it it with a little direction and on my own, and more importantly, linux is working on what i believe to be a failing drive or like a processor running with a failed core, win7 will not even load, im so stoked i wubi installed kubuntu.  finally out of the abusive microsoft relationship, woohoo! now if i could only learn python, c++ and mandarin...that'd be cool.

---

