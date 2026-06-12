---
title: "Understanding assigned letters/numbers for hard disks"
date: 2006-04-14
forum: General Help
---

### Post by Mishal on 2006-04-14
In GRUB, hard disks are referred to as hd0 or hd1 whereas in ubuntu, they are known as hda, hdb, hdc etc. 

So when I attach a friend's hard disk to my PC, GRUB completely messes up the numbering system and fails to boot any OS until I edit the boot options. The only problem is that when I am editing, I am shooting in the dark. I have no idea whether my friend's HD is hd0 or my Maxtor 80GB is hd1 or my Seagate 200GB hd2. It's completely on a trial-and-error basis. Still I managed to get ubuntu to load, but I simply COULD NOT load Windows when I have my friend's HD attached.

So is there a systematic way of understanding how GRUB assigns numbers to hard disks and how can I make it 'dynamic' so that it always boots to whichever OS I want it to, without going through a lot of guesswork?

Thanks:)

---

### Post by Ocxic on 2006-04-14
I would say that the best way to findout the hard drive ordering, is to look in your bios, and see in which order there detected, and/or what order the are assigned in the boot options, then you'll know what disk is what, first being hd0 second hd1 etc...  i don't think there is a way to make it dynamic

---

### Post by aysiu on 2006-04-14
I don't know about the automatic part, but I can tell you how you can avoid the guesswork.

If you type ```
sudo fdisk -l
``` it'll list all your partitions and their names: /dev/hda1
/dev/hda2
/dev/hda5
/dev/hda6

/dev/hdb1
/dev/hdb2

etc.

The preceding, in Grub would be:
(hd0,0)
(hd0,1)
(hd0,4)
(hd0,5)

(hd1,0)
(hd1,1)

Does that make sense? Grub is basically A = 0, B = 1, C = 2 and 1 = 0, 2 = 1, 3 = 2.

---

### Post by Mishal on 2006-04-14
Thank you but the problem with your solution, aysiu, is that you have to log in to ubuntu first to have a look at fdisk. But I get stuck the first time I attach a HD and I have to use guesswork to log on to ubuntu that first time.

And Ocxic, I will try out your idea. Maybe it will be something like this:
Primary Master: hd0,
Primary Slave: hd1
Secondary Master: hd2
Secondary Slave: hd3

But if it doesn't correspond in that order, guesswork has to step in again :(

---

### Post by dcstar on 2006-04-14
[QUOTE=Mishal]Thank you but the problem with your solution, aysiu, is that you have to log in to ubuntu first to have a look at fdisk. But I get stuck the first time I attach a HD and I have to use guesswork to log on to ubuntu that first time.

And Ocxic, I will try out your idea. Maybe it will be something like this:
Primary Master: hd0,
Primary Slave: hd1
Secondary Master: hd2
Secondary Slave: hd3

But if it doesn't correspond in that order, guesswork has to step in again :([/QUOTE]
No no no..... for IDE devices:

hda - First active IDE channel (detected by Ubuntu) Master device
hdb - First active IDE channel (detected by Ubuntu) Slave device
hdc - Second active IDE channel (detected by Ubuntu) Master device
hdd - Second active IDE channel (detected by Ubuntu) Slave device

The numbers refer to the partitions on the particular hd? device.

---

### Post by Mishal on 2006-04-14
dcstar, I think you are talking about the lettering sytem in ubuntu, not GRUB.

In GRUB, its like hd (0,0) or hd (1,0) where the number before the comma refers to a particular IDE device and the number after the comma refers to a particular partition of that IDE device.

Please correct me if I am wrong.

---

### Post by timfrost on 2006-04-14
IDE identifies disk devices by the IDE controller, and whether the device is master or slave on that controller. grub will assign disk numbers to hard disks in order.
If you have:
Primary master (HDA) = hard disk
Primary slave (HDB) has no device attached
Secondary master (HDC) = CD/DVD
Secondary slave (HDD) = hard disk

Then grub will assign the following labels:
    HDA = hd(0)
    HDD = hd(1)

If you have the CD drive as slave (HDB or HDD) and the second hard disk as master on the second controller (HDC), grub will still identify the second hard disk as hd(1).

---

### Post by Sutekh on 2006-04-14
You can also try this from the GRUB menu, go the GRUB command line (press 'c')

Then use the TAB button to help you auto-complete the options.

Try cat (hd<TAB> or cat (sd<TAB> and see what options you are presented with.  

I'm going to have to try this to clarify further, but this is roughly how I'd find Ubuntu from the GRUB prompt

I would type 
```
cat (hd<TAB>
```
 - options are hd0, hd1
```
cat (hd0,<TAB>
```
- options are partition 1 - filesystem type 83 (linux), and so on
```
cat (hd0,1)/<TAB>
```
 - options are bin boot cdrom debootstrap etc

So I now know that (hd0,1) is the Ubuntu root filesystem.

Then to boot it, I'd use the commands just like in the GRUB menu and TAB to help out.
```

root (hd0,1)
kernel (hd0,1)/boot/vmlinuz-<TAB>
initrd (hd0,1)/boot/initrd-<TAB>
boot
```

---

### Post by Mait on 2006-04-14
[QUOTE=Mishal]dcstar, I think you are talking about the lettering sytem in ubuntu, not GRUB.

In GRUB, its like hd (0,0) or hd (1,0) where the number before the comma refers to a particular IDE device and the number after the comma refers to a particular partition of that IDE device.

Please correct me if I am wrong.[/QUOTE]

Hi, Mishal

As I know, GRUB's disk naming convention depens on your BIOS(boot sequence), not your OS.

When I'm confusing with numbers in grub shell, Auto completion helps me via Tab., my favorite key in linux(grub shell, bash, vim, lftp... or whatever with readline library support :)  


[GRUB Manual - Naming convention]("http://www.gnu.org/software/grub/manual/grub.html#Naming-convention")

[QUOTE=in GRUB manual]Of course, to actually access the disks or partitions with GRUB, you need to use the device specification in a command, like `root (fd0)' or `unhide (hd0,2)'. To help you find out which number specifies a partition you want, the GRUB command-line (see Command-line interface) options have argument completion. This means that, for example, you only need to type

     root (

followed by a <TAB>, and GRUB will display the list of drives, partitions, or file names. So it should be quite easy to determine the name of your target partition, even with minimal knowledge of the syntax.

Note that GRUB does not distinguish IDE from SCSI - it simply counts the drive numbers from zero, regardless of their type. Normally, any IDE drive number is less than any SCSI drive number, although that is not true if you change the boot sequence by swapping IDE and SCSI drives in your BIOS. [/QUOTE]

Regards, Mishal

---

### Post by Mishal on 2006-04-14
Thanks a lot, people :) Very helpful indeed :)

---

