---
title: "Windows7 Boot Try(H0,0) NTFS5: No Wbildr"
date: 2010-02-05
forum: General Help
---

### Post by 0diz on 2010-02-05
No I have seen another thread like this but it did not help or I was still lost on how to fix the problem...

Here is what I can say and can tell you about my problem. I have windows 7 ultimate, I just installed a fresh new copy to make sure everything was clean and clear. I downloaded the Ubuntu 9.10 iso and the windows installer. I clicked the installer and it finished without issues, then on bootup when I select Ubuntu it drops the, "Try (h0,0) NTFS5: no wbildr" error. 

Here is the bcdedit listing of what its currently set up as, I hope it helps...

C:\Windows\system32>bcdedit

Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=\Device\HarddiskVolume1
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
resumeobject            {99f0214c-1233-11df-b035-a45078d90a36}
displayorder            {current}
                        {99f02150-1233-11df-b035-a45078d90a36}
toolsdisplayorder       {memdiag}
timeout                 10

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 7
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {99f0214e-1233-11df-b035-a45078d90a36}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {99f0214c-1233-11df-b035-a45078d90a36}
nx                      OptIn

Real-mode Boot Sector
---------------------
identifier              {99f02150-1233-11df-b035-a45078d90a36}
device                  partition=C:
path                    \ubuntu\winboot\wubildr.mbr
description             Ubuntu

C:\Windows\system32>


I don't get why its not working this time around, Ive had the same ubuntu install before and it worked like a charm....

---

### Post by Yogotiss on 2010-02-05
I personally think that windows installer program is a piece of crap... You'd turn out a lot better by burn the ISO to a CD-R and boot from CD to install.

---

### Post by 0diz on 2010-02-05
> **Yogotiss said:**
> I personally think that windows installer program is a piece of crap... You'd turn out a lot better by burn the ISO to a CD-R and boot from CD to install.

I tried that yesterday, I burned the iso, installed it side by side like the installer likes, and when it installed it worked, but the catch now is that when it boots up and you get the Grub menu and you select windows 7, it restarts the machine and goes right to the Grub menu like nothing ever happened... its the weirdest thing I have ever seen...

I used systemrescuecd, and used GAG to load the boot manager back so I can get back into windows7 but then it still does not accept ubuntu as a valid booting option...

---

### Post by CaKiwi on 2010-02-05
> **0diz said:**
> I tried that yesterday, I burned the iso, installed it side by side like the installer likes, and when it installed it worked, but the catch now is that when it boots up and you get the Grub menu and you select windows 7, it restarts the machine and goes right to the Grub menu like nothing ever happened... its the weirdest thing I have ever seen...

I used systemrescuecd, and used GAG to load the boot manager back so I can get back into windows7 but then it still does not accept ubuntu as a valid booting option...

I had the same problem doing a regular install. It only seemed to happen after I did a Windows 7 update and it was trying to complete the update after rebooting. I've got around it in the mean time by doing a wubi install. When booting into the wubi install I also get the message "Try (h0,0) NTFS5:" but without the "no wbildr" part and it continues into the Grub menu and successfully boots from there

[http://ubuntuforums.org/showthread.php?t=1376746](http://ubuntuforums.org/showthread.php?t=1376746)

---

### Post by Yogotiss on 2010-02-05
Yeah that is another issue I've noticed myself with Vista/Windows 7's boot loader. It has a issue with the Ubuntu side-by-side dual boot and with Linux taking over the boot loader. In that situation the best thing  you can do is just partition the drive and give a swap partition separately that way no boot-loader battle brawl involved.

---

### Post by 0diz on 2010-02-05
> **Yogotiss said:**
> Yeah that is another issue I've noticed myself with Vista/Windows 7's boot loader. It has a issue with the Ubuntu side-by-side dual boot and with Linux taking over the boot loader. In that situation the best thing  you can do is just partition the drive and give a swap partition separately that way no boot-loader battle brawl involved.

LoL yeah that's what I though would fix it as well, I had windows as primary then partitioned it to had a X partition. I added /boot of 200mb /of 30gb and a swap of 3gb and for whatever reason it just will not work. I don't get it. I also formatted the whole HD and started from scratch thinking something was still lingering but nope it still wont work for whatever reason it is... just soooooo odd

---

### Post by Yogotiss on 2010-02-05
When you partitioned the drive, was this during a clean install of Windows 7 or after?

---

### Post by 0diz on 2010-02-05
> **Yogotiss said:**
> Yeah that is another issue I've noticed myself with Vista/Windows 7's boot loader. It has a issue with the Ubuntu side-by-side dual boot and with Linux taking over the boot loader. In that situation the best thing  you can do is just partition the drive and give a swap partition separately that way no boot-loader battle brawl involved.

I used some partitioning software to re-size my partition and I labeled the new partition X, then when I booted from the CD I set it up on that X partition.

---

### Post by Yogotiss on 2010-02-06
You may want to try partitioning it while doing a fresh install of Win7 or run Ubuntu in Virtual Box.

---

