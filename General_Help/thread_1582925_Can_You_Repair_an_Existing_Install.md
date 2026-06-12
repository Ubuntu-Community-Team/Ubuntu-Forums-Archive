---
title: "Can You Repair an Existing Install"
date: 2010-09-27
forum: General Help
---

### Post by Netorca on 2010-09-27
Hi Can someone please tell me , Can you repair an existing install with a distro CD, IE Run the install with a switch to just repair rather than "install"...

I have messed up a Ubuntu 10.4 Netbook install by playing with the Mount Utility trying to mount a SD card, and now my netbook will not boot....

Netorca

---

### Post by philinux on 2010-09-27
> **Netorca said:**
> Hi Can someone please tell me , Can you repair an existing install with a distro CD, IE Run the install with a switch to just repair rather than "install"...

I have messed up a Ubuntu 10.4 Netbook install by playing with the Mount Utility trying to mount a SD card, and now my netbook will not boot....

Netorca

Can you boot into recovery mode?

When you say playing, what did you do Exactly?

---

### Post by Netorca on 2010-09-27
Hi Phil
I was using the Mount utility and while not realy loking at all of the settings, I think I set the SD Card to mount at Root...

I am a Wintel, Router and Netware Guy, and was being hassled by my Wife to Create some images for her to sell items on Ebay so I thought I would use My Linux NetBook and I think I have stuffed it up..

Since then I have tried to reinstall Grub Using the CHROOT option on the Ubuntu Site but whist re installing without errors, still will not boot..

Have run the sudo fdisk -l comparing it to other installs but that "seems OK " but I think i have stuffed up another file somewhere...

I can access the hard drive with a distro CD and read the files, So I was going to copy them off to a USB Hard Drive and then re install but I am sure there is an easier option ...

Netorka

---

### Post by Netorca on 2010-09-27
Sorry Phil I was Rambling, 
I can boot so I can see the recovery mode options, I have 8 lines with various Kernels
I tried the top three (recovery ) in brackets , Nothing the bottom one runs a script and ends with the output on screen below........

PS it will not always boot into recovery mode somtimes it just tries and  ends with a Black screen no cursor... Thanks again.. 

Begin: Running /scripts/local-bottom  ..
Done.
Done.
Begin: Running /scripts.init-bottom ...
Begin: Startin AppArmor profiles ...
chroot: cannot execute /etc/apparmor/initramfs: no such file or directory
Failure: AppArmor profiles failed to Load
Done.
[       19.646612] ath5k phy0: cant register ieee80211 hw

---

### Post by Crazedpsyc on 2010-09-27
Ok, the problem is since you set the SD card to root, it wants to boot from there, and that is very bad. If the SD card is big enough try installing ubuntu on it from another computer, if not, you need to get into recovery mode and enter some commands to make it switch back.
```

sudo mount / /

```might do it unless you accidentally overwrote your root directory.
to see if you did this try:
```

ls /

```and if nothing comes up, sorry it's empty.
Hope this helps

Oops, make sure you use sudo up there

---

### Post by Crazedpsyc on 2010-09-27
Ok, after some more looking I have found that you should actually type the following if possible:
```

mount

```then look through the results for something that looks like your HDD (mine is /dev/sda5) (It should say "type ext4")
and then run
```

mount *(thatdevice)* /

```where *(thatdevice) *is the /dev/whatever for the device

---

### Post by Netorca on 2010-09-28
Thank you for all your advice, I tried mounting the drive but without any luck..
I decided to make a clean break of it as all I was doing was repeatedly turning the unit off with the power button when things froze up......Worried about damaging the hardware...

Anyway I made the back up of the drive by booting to a CD distro and copied everything over to a USB Hard Drive then reinstalled Ubuntu 10.4 Netbook.....

Took a while but Now "Ime Back" Wont be messing with the Mount utility again. 

Ubuntu forever......

Netorca

---

