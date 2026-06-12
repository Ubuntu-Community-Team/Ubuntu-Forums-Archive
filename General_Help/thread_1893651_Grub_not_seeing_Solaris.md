---
title: "Grub not seeing Solaris"
date: 2011-12-10
forum: General Help
---

### Post by stans on 2011-12-10
I've had triple boot running using three hard drives - primary boot is Ubuntu 10.04, then openSUSE on second drive and Fedora on third drive. 

Grub worked just fine. 

Replaced Fedora with openSolaris (11) - it boots by interrupting the bios - but when I booted Ubuntu and ran update-grub grub never saw the openSolaris loader on the third drive. I recall having a difficulty getting Fedora recognized - but have forgotten the details. 

How can I get grub to 'see' openSolaris ?

---

### Post by oldfred on 2011-12-10
Solaris is not Linux, so I would be surprised if grub2's os-prober found it.

Someone posted this before. It is just a chainloader like booting into Windows. You can add an entry like this to 40_custom, with your drive & partition info for the set root command.

[http://ubuntuforums.org/showthread.php?t=1529658](http://ubuntuforums.org/showthread.php?t=1529658)
menuentry "OpenSolaris 2010.03 snv_134 64bit" {
    set root='(hd1,2)'
    chainloader +1
}

---

### Post by stans on 2011-12-10
Unix is not Linux, but then again neither is Windows 7 and I have Grub seeing it from Ubuntu on another system.

Thanks for the pointer to the other thread.

fdisk tells me that Solaris is on /dev/sdc1 - the sample shows

# Chainload OpenSolaris GRUB.
menuentry "Chainload OpenSolaris GRUB" {
    set root=(hd0,2)
    chainloader +1

so would I replace hd0,2 with hd2,1 ?

Yes - I'm a newbie...

---

### Post by idoitprone on 2011-12-10
> **stans said:**
> Unix is not Linux, but then again neither is Windows 7 and I have Grub seeing it from Ubuntu on another system.

Thanks for the pointer to the other thread.

fdisk tells me that Solaris is on /dev/sdc1 - the sample shows

# Chainload OpenSolaris GRUB.
menuentry "Chainload OpenSolaris GRUB" {
    set root=(hd0,2)
    chainloader +1

so would I replace hd0,2 with hd2,1 ?

Yes - I'm a newbie...
dont beat urself up. this type of thing is where you have to read docs
Nobody like reading docs
[https://help.ubuntu.com/community/Grub2#Creating_the_Custom_Menu](https://help.ubuntu.com/community/Grub2#Creating_the_Custom_Menu)

I believe
```
/dev/sdc1 =(hd2,1)

(hd0,2) is /dev/sda2
```

---

### Post by stans on 2011-12-10
Thank you for the encouraging words... and I don't have a problem reading docs when I can find them. That can be an all day job sometimes. My other problem is too many different directions... you can only spread peanut butter so thin then it just doesn't work.

While I am here asking questions, will I risk 'shooting myself in the foot' whilst monkeying around with 40_custom ?

I'm a firm believer in cya backout procedures...

OK - took the plunge and made the change to 40_custom but update-grub didn't show it nor does grub show it at boot time. It's grub 1.98 btw.

Here's my file:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
# Chainload OpenSolaris GRUB.
 menuentry "Chainload OpenSolaris GRUB" {
     set root=(hd2,1)
     chainloader +1



I'll search the forum...

---

### Post by idoitprone on 2011-12-11
> **stans said:**
> Thank you for the encouraging words... and I don't have a problem reading docs when I can find them. That can be an all day job sometimes. My other problem is too many different directions... you can only spread peanut butter so thin then it just doesn't work.

While I am here asking questions, will I risk 'shooting myself in the foot' whilst monkeying around with 40_custom ?

I'm a firm believer in cya backout procedures...

OK - took the plunge and made the change to 40_custom but update-grub didn't show it nor does grub show it at boot time. It's grub 1.98 btw.

Here's my file:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
# Chainload OpenSolaris GRUB.
 menuentry "Chainload OpenSolaris GRUB" {
     set root=(hd2,1)
     chainloader +1
[SIZE=2]**}**[/SIZE]


You forgot the closing brace and dont forget to  to add executable permissions
```
sudo chmod u+x /etc/grub.d/40_custom
```
that should be the correct file I presume

---

### Post by oldfred on 2011-12-11
My fault, the initial post with the example was missing the closing }. I corrected it just in case some looks at this and does not read rest of thread.

The latest grub2 update is very particular about typos. I had a typo in my 40_custom since the beginning, thru several versions and it worked. But it was missing one entry that I did not notice as it was for an old install. Then with grub 1.99 it would not load and created a error file, so the new version does more error checking.

---

### Post by stans on 2011-12-11
Thank you oldfred and idoitprone. 

I should have seen that the closing bracket was missing.

OK - most excellent - I am seeing the chainloader entry at boot - HOWEVER - am getting the 'invalid signature' when selecting it. Searched quite a bit but find that all references are regarding Windows as the problem, not Solaris.

---

### Post by oldfred on 2011-12-11
With Windows it is the NTFS partition is missing info in the NTFS partition boot sector.

Or it may be, if you have a Intel motherboard, you have to have a boot flag on a primary partition. Grub does not use one, Windows & Lilo use boot flags, but for whatever reason some BIOS require a boot flag or the BIOS does not let you start to boot.

---

### Post by stans on 2011-12-11
MoBo is a Gigabyte. I'm wondering if the entry in 40_custom is missing something.

Solaris boots just fine when I use the bios boot menu (pf12).

---

### Post by oldfred on 2011-12-11
Have you used e on the grub menu and experimented with the drive number?
 I find the drive I normally boot from (sdc) is always hd0 and then sda is hd1. But if I boot from sda then it is hd0. So When I copy my chainload entries from one install to another I either have to adjust the hdX entry or know when booting to try different ones.

---

### Post by stans on 2011-12-17
"Have you used e on the grub menu" - not sure what that means... time to do some more reading I guess.

output from fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00084ba2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      176584  1418407936   83  Linux
/dev/sda2          176584      182402    46728193    5  Extended
/dev/sda5          176584      182402    46728192   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00017836

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         262     2103296   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sdb2   *         262        2873    20972544   83  Linux
/dev/sdb3            2873      121602   953684992   83  Linux

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c96b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           4      182400  1465103902+  bf  Solaris


Primary boot is Ubuntu on A, then openSUSE on B, then would like to chainload Solaris on C

I've seen the script to display boot info but it doesn't identify which hd number. I was under the assumption that hd2 was sdc.

Here is my grub entry -

 menuentry "Chainload OpenSolaris GRUB" {
     set root='(hd2,1)'
     chainloader +1
}

This gets me the 'invalid signature' error message.

Thanks again for your assistance.

---

### Post by oldfred on 2011-12-17
It depends on which drive you boot as that will always be hd0, then the other drives are numbered but sometimes you have to experiment to find the right number or the order BIOS or grub see drives.

When the grub menu comes up, you can scroll to an entry and press e to edit it (one time change). That way you can easily test different drive numbers without having to edit 40_custom for each. Or you can just add several entries into 40_custom to test which works.

---

### Post by stans on 2011-12-17
That editing the grub entry would be handy if I could figure out how to save the change.

---

### Post by oldfred on 2011-12-17
You have to remember what you did and copy that into 40_custom.:)

---

### Post by stans on 2011-12-17
You misunderstood. No matter what I keyed into the grub statements (after interrupting with the 'e') I could not make them 'stick'. Could not discover how to 'save'.


Of course now it doesn't matter because I am enjoying success - your clue about what order the drives are in the boot priority in bios was my answer.

The Ubuntu drive is first, then the Solaris, then the openSUSE. My chainload was directed therefore to hd1.

Thank you very much for your patience and assistance.

---

