---
title: "Getting rid of windows, please help"
date: 2006-04-09
forum: General Help
---

### Post by PriceChild on 2006-04-09
Right... i'm using wine, vmware player and cedega and are very happy with linux right now, so happy that my dualboot windows has to got to go!!!

I've currently got several partitions; a s/c of gparted is attached.

I think that grub is installed onto the windows ntfs partition as that's what my pc's booting off.

I'm wondering how to remove the rest of the partitions, can i access gparted in the live cd to remove the windows partitions? use the install cd to reinstall the grub menu onto the linux partition?

A step by step guide would be very handy if anyone could spare the time. Not completely up to speed with rescuing things in linux atm :)

Thanks for any time,
                              Pricey

-edit-
from my /boot/grub/menu.lst :

```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)
```

---

### Post by ubernoob on 2006-04-09
you can use fdisk to set boot flags on partitions. For changing where grub is, try this guide: [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

### Post by PriceChild on 2006-04-09
I'm just confused now :)

---

### Post by Ramses de Norre on 2006-04-09
Removing the windows partition can be done without live cd, just unmount it and delete it with gparted.
And isn't the MBR a seperate block of 512bytes at the beginning of a hard disk? If so: you don't have to reinstall grub. Otherwise: follow the link ubernoob gave  you.

---

### Post by nazish on 2006-04-09
i think ramses is right and what u want to b done can b done quite easily,  
first run gparted unmount the selected partitions after unmounting delete the windows partition which you want to delete.then format it and mount it in whatever way u want.

**[COLOR=DarkOrange]And mind u doing this in no way effects ur grub configuration.[/COLOR]** 

After this step run the following comand

[B]sudo gedit /boot/grub/menu.lst
locate a line which has something related to windows and commne the lines with a '#' symbol.
[/B] 
restart u pc to just boot automatically into linux.

And its always gr8 to see ppl who have faith in linux that they r ready to dump windows keep up [COLOR=White]the spirit buddy.
[/COLOR] [COLOR=Black][/COLOR][COLOR=Black]**--naz--**[/COLOR]

---

### Post by Ramses de Norre on 2006-04-09
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

```
Find these lines in /boot/grub/menu.lst and uncomment the last one of them to boot without the grub menu (which you probably wont need anymore).

---

### Post by PriceChild on 2006-04-09
[quote=Ramses de Norre]Removing the windows partition can be done without live cd, just unmount it and delete it with gparted.
And isn't the MBR a seperate block of 512bytes at the beginning of a hard disk? If so: you don't have to reinstall grub. Otherwise: follow the link ubernoob gave  you.[/quote]

Ah, that sounds very good about the grub... hope you're right ;)

I put an exrtact from my grub list in my first post... what does that mean? just that it's on the mbr of the drive, and stays there even if i format the drive?

What i really want to do is delete the windows partition though, and just make my ext drive fill the rest of the space. You're saying i can remove all the partitions i don't want just fine.... but how do i make my ext drive larger? gparted won't do anything while any of the drives are mounted.

---

### Post by Ramses de Norre on 2006-04-09
The first grub stage is always installed in the MBR, just because that's the only part of the hard disk read by the BIOS when it's searching after an OS.
I think '# groot=(hd0,2)' refers to the partition where the second grub stage is storaged, the one used to boot Linux (the second stage is not used when booting windows).

Would you like to delete the fat partition too? If so do the same as with the windows. To enlarge the ext partition you'll need to boot with a live cd and first move the existing ext partition to the front of the drive and then enlarge it with the unallocated space behind it. (if the fat remains: move both the fat and the ext to the front so that the unallocated space is right after the ext).

What I think of now: you'll need to change some things in your menu.lst: ```
root            (hd1,0)

```
Find a similar line in each kernel section and make it correct, the first number after hd is the number of the harddrive (stays the same) the second the number of the partition, starting from 0 (so you'll get hd0,0 or hd0,1).

You'll also like to make a new swap partition on the end of your harddisk.

EDIT: make a backup before messing with partitions!

---

### Post by PriceChild on 2006-04-09
Ok seems pretty straightforward. But will deleting the widows and fat partitions actually change the number of the linux partition? :O

Booting into the livecd to move the partitions around, is gparted part of the live cd? or does it mean commandline funniness?

And finally... you tell me i have to remove the swap partition and make a new one, is this to get it out of the extended bit? Is this needed, couldn't it just live their happily to avoid making more changes to fstab etc.

Pricey

---

### Post by Ramses de Norre on 2006-04-09
Removing partitions will change partitionnumbers (that's why you need to change menu.lst) and you will also need to change /etc/fstab.

I don't know whether gparted in included in the live disc, if not: download and burn knoppix, a live linux distro built for purposes like this (and it boots lots and lots faster!).

I don't know about the swap, maybe you can just leave it and shrink the extended. You can try to ;)

---

### Post by PriceChild on 2006-04-09
Ok... knoppix torrent downloading :)

That'll be a couple of hours though so plenty of time to pester you about other things i'm wondering about if you can spare more time :)

If i do delete the swap and recerate one outside of the extended, i will have to change etc/fstab to point to it won't I.

Also, can I use Knoppix to change all the files on my hard drive? to let me change /etc/fstab etc. ?

---

### Post by Ramses de Norre on 2006-04-09
You will need to change your fstab, and Knoppix can do that ;)

---

### Post by PriceChild on 2006-04-09
EDIT

whoops sorry i basically posted the same thing, very tired and thought i lost the first one before posting it.

---

### Post by Ramses de Norre on 2006-04-09
Knoppix can edit everything as well as ubuntu, just mount the drives.

---

### Post by PriceChild on 2006-04-10
ok so knoppix works fine after disabling dhcp...

But how can i edit files? I've tried the little hint in it's readme about remounting them using its line of code but no joy there.

In the root terminal i can't manage to loads up a single text editor :(

pricey

---

### Post by Ramses de Norre on 2006-04-10
The drives should be one your desktop where you can just do right click mount.
Otherwise: look at your fstab from ubuntu for working parameters.
The text editor in kde is kate I think, but you can always use vi or nano.

---

### Post by PriceChild on 2006-04-10
Knoppix wasn't really any help, neither was my ubuntu LIVE cd.

I ended up loading up the install cd to change my partitions.... then messed up my grub, spent about an hour trying to get it all back... and now i'm happy! :)

Except... i think ubuntu thinks i've got more on my hard disk than i actually do... by about 10 Gb.

Is there some way i can force a disk check on boot next time round? How about getting it to recalculate the space used etc. ? ty for help :)

Pricey

---

### Post by Ramses de Norre on 2006-04-10
forcing fsck: use shutdown with the -F flag.
Shutdown: ```
sudo shutdown -Fh now
```
Reboot: ```
sudo shutdown -Fr now
```

I don't now whether this will recalculate your disk space.

---

### Post by PriceChild on 2006-04-10
Thankyou very much Ramses :)

Everything sorted,
                            Pricey

---

