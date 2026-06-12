---
title: "How to change user from livecd"
date: 2010-05-25
forum: General Help
---

### Post by alejandro.mc on 2010-05-25
I-m running the livecd, I open a terminal, it appears as user

ubuntu@ubuntu

I want to change to my Ubuntu user

me@me-desktop

so that i can upgrade a package that i broke via dpkg..

how can I switch to my user??????

Thx

---

### Post by inso_741 on 2010-05-25
are you trying to repair packages within your os installed on your hdd through a live session?
as far as I know you cant login to your user account via a live cd

---

### Post by jerome1232 on 2010-05-25
sure

```
sudo adduser me
su me
```

I don't think you could graphically login as me though.

although that won't work for your purpose.

You will need to mount your partitions and chroot into your environment.

---

### Post by Ozymandias_117 on 2010-05-25
What was broken that you can't log in to your normal boot to fix it that way?

---

### Post by alejandro.mc on 2010-05-25
I did

dpkg -i


to downgrade three libraries:

udev-1.0-0_151-12 to udev-1.0-0_151-1
libudev0-1.0-0_151-12 to libudev0-1.0-0_151-1
libgudev-1.0-0_151-12 to libgudev-1.0-0_151-1

and now I cannot start Ubuntu..how can I upgrade them again from the livecd ????? or somehow to boot to the terminal, recovery mode doesn-t work either..

Thanks very much in advance!!!

---

### Post by inso_741 on 2010-05-25
don't start multiple threads for the same problem
I found this one [here]("http://ubuntuforums.org/showthread.php?t=1493147")!!!


try [this]("http://ubuntuforums.org/showpost.php?p=8628383") and you should be fine...;)

---

### Post by jocko on 2010-05-25
What you want is possible, but a little bit more complicated than simply switching to another user.

[This post]("http://ubuntuforums.org/showpost.php?p=8576910&postcount=4") explains how to do it.

---

### Post by Ozymandias_117 on 2010-05-25
I have no idea if this will work or not, I've never actually tried it. I'm just inferring from what has been posted already and what all I know :P.

Try booting to a liveCD and mounting your Linux partition use ```
sudo fdisk -l
``` to find out the /dev/sd* name for it and use ```
sudo chroot /dev/sd*
``` (Whatever you had found) then try ```
sudo aptitude install udev-1.0-0_151-12 libudev0-1.0-0_151-12 libgudev-1.0-0_151-12
``` if it says they are already there, change install to reinstall.

Like I said, I have no idea if this will work, but it's all I can offer.

Edit: Well, apparently I had the general idea... Didn't think about /dev and /proc needing to be moved And I didn't know synaptic would need to have something done with it first.

---

### Post by Bobhuber on 2010-05-25
> **alejandro.mc said:**
> I did

dpkg -i


to downgrade three libraries:

udev-1.0-0_151-12 to udev-1.0-0_151-1
libudev0-1.0-0_151-12 to libudev0-1.0-0_151-1
libgudev-1.0-0_151-12 to libgudev-1.0-0_151-1

and now I cannot start Ubuntu..how can I upgrade them again from the livecd ????? or somehow to boot to the terminal, recovery mode doesn-t work either..

Thanks very much in advance!!!
Is this the same fellow that told me last night (and I quote) I KNOW when I gave my suggestion for your DVD/RW problem. Now you know why you should not _downgrade _as you put it a major operating system file unless you absolutely know how it will affect your system. As many posts have stated DO NOT BELIEVE everything you read.
 Good Luck with your problem.

---

### Post by alejandro.mc on 2010-05-25
Hey I wasn't trying to disturb anyone, sometimes my english is not great and people understand a bit different what I'm trying to say, sorry about that!! No harm intended!!

Thanks to everyone for helping out!

I followed this from a thread by AlexenderReez from 2007:



"



firstly....the originally howto can be found in tips and tutorials threat....i just forward this guide as i realized that this kind of guide doesn't exist in this section but it is really important . . .
especially to those cases..
if you are running an upgrade and you forgot to connect your laptop to power supply then when synaptic doesn't finish install software yet to your system...(after finished download)

or

your install software with command dpkg -i and that particular software doesn't have enough dependency then for sudden there will be broken software noticed by update manager ...for almost the time you can remove or reinstall it again using synaptic but how about when that particular broken installation broke your system and freeze your system

or

you shutdown your system and forgot that your software installation still running...

***for those all kind of situation or other situation that make you can't log on after restart even using 'safemode' ....so you need livecd to repair it...

put you livecd in and restart...then just lo on to livecd....

then open terminal

type

sudo mkdir /mnt/repair

sudo mount /dev/?d?? /mnt/repair

*noted that ?d? mean part of your ubuntu root partition....it might be sda1...or hdb1 or sdb or whatever...depend where you install your ubuntu....

sudo chroot /mnt/repair su

sudo apt-get update
sudo apt-get upgrade
sudo aptitude upgrade
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get upgrade


exit
sudo reboot

take out your livecd...you should can run your ubuntu as usual .....:KS





"





And TARAN!!!

Thanks everyone for your patience!!

---

