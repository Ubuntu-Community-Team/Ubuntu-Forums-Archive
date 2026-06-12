---
title: "Is this a method to restore GRUB?"
date: 2011-09-19
forum: General Help
---

### Post by mitk0o0o0 on 2011-09-19
Well I had to re-install Win7 cause it was going crap and now I've lost the boot menu upon startup and I tried whatnot and just can't get it back...

And same with my Ubuntu 10.10, it was also kinda going crap getting filled with software and whatnot and started to become buggy and since I still have the live CD I was wondering if i put it in, can i choose to upgrade to 11.04 from there and when upgrade is done, will i have the GRUB menu back that way? Or i'll have to boot to Ubuntu to use the Upgrade function, which i can't do.

Or here's another way:
If i buy a CD and burn 11.04 and run it, and then choose to install Ubuntu on the partition where 10.10 was I will have it with no probs?

Sorry for my confusing english.

---

### Post by Bodsda on 2011-09-19
> **mitk0o0o0 said:**
> Well I had to re-install Win7 cause it was going crap and now I've lost the boot menu upon startup and I tried whatnot and just can't get it back...

And same with my Ubuntu 10.10, it was also kinda going crap getting filled with software and whatnot and started to become buggy and since I still have the live CD I was wondering if i put it in, can i choose to upgrade to 11.04 from there and when upgrade is done, will i have the GRUB menu back that way? Or i'll have to boot to Ubuntu to use the Upgrade function, which i can't do.

Or here's another way:
If i buy a CD and burn 11.04 and run it, and then choose to install Ubuntu on the partition where 10.10 was I will have it with no probs?

Sorry for my confusing english.

See if this wiki entry helps
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Bodsda

---

### Post by mahmoodkamal on 2011-09-19
> **mitk0o0o0 said:**
> Well I had to re-install Win7 cause it was going crap and now I've lost the boot menu upon startup and I tried whatnot and just can't get it back...

And same with my Ubuntu 10.10, it was also kinda going crap getting filled with software and whatnot and started to become buggy and since I still have the live CD I was wondering if i put it in, can i choose to upgrade to 11.04 from there and when upgrade is done, will i have the GRUB menu back that way? Or i'll have to boot to Ubuntu to use the Upgrade function, which i can't do.

Or here's another way:
If i buy a CD and burn 11.04 and run it, and then choose to install Ubuntu on the partition where 10.10 was I will have it with no probs?

Sorry for my confusing english.

I guess you can update grub by:

sudo update-grub

then reinstalling in MBR by:

grub-install /dev/sdaXXX (whatever is the device name)

---

### Post by mitk0o0o0 on 2011-09-19
Those are the problems guys, i get some kind of errors when typing in those stuff. Sometimes it can't find stuff.

And I have no idea what the device's name is.

---

### Post by Bodsda on 2011-09-19
> **mitk0o0o0 said:**
> Those are the problems guys, i get some kind of errors when typing in those stuff. Sometimes it can't find stuff.

And I have no idea what the device's name is.

Can you paste the output of
```

sudo fdisk -l

```
And the output of each step you are attempting. Then we can see where it is going wrong, and advise

Thanks,
Bodsda

---

### Post by mitk0o0o0 on 2011-09-19
> **Bodsda said:**
> Can you paste the output of
```

sudo fdisk -l

```And the output of each step you are attempting. Then we can see where it is going wrong, and advise

Thanks,
BodsdaSo when i open up terminal that's the first thing i should enter?

---

### Post by Bodsda on 2011-09-19
> **mitk0o0o0 said:**
> So when i open up terminal that's the first thing i should enter?

Yep, and then run through the recovery procedure which you said was giving you errors.

Paste all output here

Thanks,
Bodsda

---

### Post by mitk0o0o0 on 2011-09-19
Am I doing it right?

> ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x60abe5c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11503    92390705    7  HPFS/NTFS
/dev/sda2           11503       60802   395994113    f  W95 Ext'd (LBA)
/dev/sda5           13055       56540   349296283    7  HPFS/NTFS
/dev/sda6           11503       12983    11889664   83  Linux
/dev/sda7           12983       13054      573440   82  Linux swap / Solaris
/dev/sda8           56540       60621    32778240   83  Linux
/dev/sda9           60621       60802     1453056   82  Linux swap / Solaris

Partition table entries are not in disk order


ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ grub-install /dev/sda6
cp: cannot create regular file `/boot/grub/915resolution.mod': Permission denied
ubuntu@ubuntu:~$ 


---

### Post by dino99 on 2011-09-19
boot on a livecd, open a terminal and run:

sudo grub-install /dev/sda

then:

sudo update-grub

---

### Post by mitk0o0o0 on 2011-09-19
> **dino99 said:**
> boot on a livecd, open a terminal and run:

sudo grub-install /dev/sda

then:

sudo update-grub
It gives me this:

> ubuntu@ubuntu:~$ sudo grub-install /dev/sda6
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).



I tried mounting and even doing "sudo mount /dev/sda6" and it says it's already mounted.

---

### Post by oldfred on 2011-09-19
Which is really your install - sda6 or sda8? You have two Linux and two swaps as if you installed twice. The newest may then be sda8?

Post this to see all the details from a liveCD:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by mitk0o0o0 on 2011-09-19
> **oldfred said:**
> Which is really your install - sda6 or sda8? You have two Linux and two swaps as if you installed twice. The newest may then be sda8?

Post this to see all the details from a liveCD:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.Wow I just remembered I had an older version of Ubuntu which got lost after installing Windows again and I never really tried to recover it.

Hmm so I should try sda8? Also the link you gave me, I should burn that to a CD and boot it?

---

### Post by cryptotheslow on 2011-09-19
You don't need to specify the partition number - just the disk  /dev/sda   no number :)

---

### Post by mitk0o0o0 on 2011-09-19
> **cryptotheslow said:**
> You don't need to specify the partition number - just the disk  /dev/sda   no number :)I think I remember trying that and again, some kind of error. :/

---

### Post by cryptotheslow on 2011-09-19
Then paste up the error you get :)


Also suggested reading re: various ways to reinstall GRUB2:
[https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2#Methods_of_Reinstalling](https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2#Methods_of_Reinstalling)


Yes, somewhat oddly Grub v1.98 up is referred to as GRUB2 - worth remembering when trawling for answers online.

---

### Post by Quackers on 2011-09-19
What system is in /dev/sda6 and what system is in /dev/sda8?
You will need to mount one of those first then install grub to the mbr of the drive (/dev/sda - NOT /dev/sda6)

---

### Post by mahmoodkamal on 2011-09-20
> **mitk0o0o0 said:**
> It gives me this:



I tried mounting and even doing "sudo mount /dev/sda6" and it says it's already mounted.

grub-install /dev/sda not sda6.

sda is a device while sda6 is a partition on this device

---

### Post by mitk0o0o0 on 2011-09-20
Thanks alot guys, i now have it back. :D

After that I upgraded to 11.04 and got a few errors in the procedure. It appears to be a little buggy.

---

