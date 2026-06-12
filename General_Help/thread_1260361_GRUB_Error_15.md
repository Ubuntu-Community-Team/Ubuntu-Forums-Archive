---
title: "GRUB Error 15"
date: 2009-09-07
forum: General Help
---

### Post by callumacrae on 2009-09-07
I was trying to move my /home directory following the instructions at [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) .

It didn't work, and I got GRUB error 15. I assumed this meant that the /home directory hadn't been found, cos I don't really know much about Ubuntu.

I deleted that installation of Ubuntu and installed a new one (With the home directory in a different partition :) ). I still get GRUB error 15.

I looked it up, and I gather that it means one of the grub files is missing. Which doesn't mean a thing to me, really.

Does anyone know how I can fix this problem?

Thanks,
~Callum

---

### Post by drinkpepsi on 2009-09-07
Try this

[http://ubuntuforums.org/showthread.php?t=297261]("http://ubuntuforums.org/showthread.php?t=297261")

---

### Post by callumacrae on 2009-09-07
Nah it doesn't work. I just get error 15.

~Callum

---

### Post by callumacrae on 2009-09-08
[https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB)

These methods all failed.

~Callum

---

### Post by callumacrae on 2009-09-08
Also, reinstalling everything does NOT work. Should I get a new live CD?

---

### Post by egalvan on 2009-09-08
> **callumacrae said:**
> Also, reinstalling everything does NOT work. Should I get a new live CD?

The LiveCD is probalbly OK, especially if you already used it succesfully.
But in any case, there is a boot-time option on the LiveCD menu,
 called "Check media for errors"  (or something worded like this)
run it, and it will check the LiveCD for you.

Did you wipe the drive before re-installing?
An error 15 that survives a re-install sounds like something wrong in the FAT or MBR.

Or do you need to preserve partitions/information on the drive?

herman has some excellent GRUB stuff

This is a link to the specific error you cite...

[http://members.iinet.net.au/~herman546/p15.html#15](http://members.iinet.net.au/~herman546/p15.html#15)

---

### Post by callumacrae on 2009-09-08
It said 1 error found. Should it have done anything about it? It didn't.

It doesn't matter if anything gets deleted, I've reformatted and reinstalled everything at least 5 times now :)

I think I've found something though. My GRUB menu alwayed looked something like this:

> 
Ubuntu 9.04, kernel 2.6.28-11-generic
Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
Ubuntu 9.04, kernel 2.6.27-11-generic
Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
Ubuntu 9.04, kernel 2.6.26-11-generic
Ubuntu 9.04, kernel 2.6.26-11-generic (recovery mode)
Ubuntu 9.04, memtest86+


(That's not actually what it looked like, thats just what I remember.)

This is the contents of my menu.lst: (extract)

> ## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        a1a12b4d-5007-4ecc-b4e1-5841b862b882
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a1a12b4d-5007-4ecc-b4e1-5841b862b882 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        a1a12b4d-5007-4ecc-b4e1-5841b862b882
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a1a12b4d-5007-4ecc-b4e1-5841b862b882 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        a1a12b4d-5007-4ecc-b4e1-5841b862b882
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Is this just because I reformatted it?

~Callum

---

### Post by egalvan on 2009-09-09
> **callumacrae said:**
> It said 1 error found. Should it have done anything about it? It didn't.

Are you refering to the "check media" test option?
if so, chunk the cd and burn another.
And before you burn it, i suggest checking the md5 on the iso.


> 
It doesn't matter if anything gets deleted, I've reformatted and reinstalled everything at least 5 times now :)

Builds character, you know... :)


I think I've found something though. My GRUB menu alwayed looked something like this:
...

This is the contents of my menu.lst: (extract)
...

Is this just because I reformatted it?

~Callum[/QUOTE]

The longer list of kernel options comes about because the kernel is updated on occasion.
if you have not changed the menu.lst option, GRUB keeps seven kernels.

The lone kernel option is what you will see on a clean install, before any kernel updates are installed.

I have mine set to two, so if a kernel update is borked, I can always re-boot to the previous good one.

And these changes can be done by editing menu.lst

```
sudo gedit /boot/grub/menu.lst
```

or installing StartUpManager for the latest GUI-fied interface.

---

### Post by callumacrae on 2009-09-09
I can't even get into the menu though.

Getting a new disk didn't work, and I redownloaded Ubuntu.

~Callum

---

### Post by fela on 2009-09-09
> **callumacrae said:**
> I can't even get into the menu though.

Getting a new disk didn't work, and I redownloaded Ubuntu.

~Callum

To edit the GRUB menu from a livecd you have to boot the livecd and then mount the partition that Ubuntu is installed on.

Also, please run the livecd and run these commands in a terminal:

```
sudo grub
find /boot/grub/stage1
```

It **should** output something like (hdx,x) where x is a number. If it outputs nothing or 'file not found' or similar, don't continue.

Now run, where (hdx,x) is (hd0,0) - change the numbers if necessary:

```
root (hd0,0)
setup (hd0)
quit
sudo reboot
```

Now it'll reboot your computer and see if this has worked.

---

### Post by callumacrae on 2009-09-09
I've tried this already. IT didn't display any error messages. If fact it didn't display any messages at all. It just didn't do anything. Still, I'm bored I'll try again :)

---

### Post by callumacrae on 2009-09-09
I said something this time:

>  Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 17 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

Rebooting now.

~Callum

---

### Post by callumacrae on 2009-09-09
> GRUB Loading stage1.5.

GRUB loading, please wait...
Error 15
_

Gah :(

~Callum

---

### Post by egalvan on 2009-09-09
OK, at this point I HIGHLY recommend wiping the drive clean.

Download Darik's Boot And Nuke 

[www.dban.org](www.dban.org)

burn the iso to CD

ASSUMING THAT YOU ONLY HAVE ONE DRIVE ATTACHED
ASSUMING THAT YOU DO NOT HAVE ANY DATA YOU WISH TO SAVE

boot the dban CD
accept the defaults
wait for the drive to be wiped

If after this you are still getting the error,
 then it is not the software, it is hardware.

Check jumpers on the hard drive ( if it is PATA )
Check BIOS settings for the boot drive
Check BIOS settings for boot drive order

I'm off to work, will be back in 24 hours.

ErnestG

---

### Post by callumacrae on 2009-09-09
Which reminds me. I changed the boot order, because I was trying to get it to boot off the 30 gb hard drive, not the 7 gb.

*Hits himself*

Fixed :)

Thanks for all your help :)

~Callum

---

### Post by fela on 2009-09-09
> **callumacrae said:**
> Which reminds me. I changed the boot order, because I was trying to get it to boot off the 30 gb hard drive, not the 7 gb.

*Hits himself*

Fixed :)

Thanks for all your help :)

~Callum

Gah, user error AGAIN! At least it's fixed :)

---

