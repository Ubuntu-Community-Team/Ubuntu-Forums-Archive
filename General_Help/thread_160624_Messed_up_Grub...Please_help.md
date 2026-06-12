---
title: "Messed up Grub...Please help"
date: 2006-04-15
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-04-15
Well, I deleted my dapper partition so I get grub error 22. Is there a way I can restore grub/update it to see my breezy partition ?

---

### Post by PriceChild on 2006-04-15
Whenever this happens to me, i but in the breezy cd, press escape and skip to installing the grub loader on the mbr, then use the live cd to change /boot/grub/menu.lst

Pricey

---

### Post by johso on 2006-04-15
Yea, always done the same thing, except for the Live CD? I can't see why that's necessary? Otherwise you could just pop in the Live CD and find the backup of the menu.lst, which is usually created when you change it. (The one called menu.lst~)

---

### Post by PriceChild on 2006-04-15
[quote=johso]except for the Live CD[/quote]

Well if you don't need it then good :)

I think i've always had to use it because of having several partitions.

---

### Post by johso on 2006-04-15
[QUOTE=PriceChild]Well if you don't need it then good :)

I think i've always had to use it because of having several partitions.[/QUOTE]

Well, it's just that as far as I know, Grub can find the bootable partitions automatically. I might be wrong though, but I'm quite sure I never used the Live CD for the purposes! :-D

---

### Post by PriceChild on 2006-04-15
I definately had to when i removed my windows partition.
It kept thinking that my...

ah, i remember now :P

To enlarge my ubuntu drive, i had to copy it to the start of the disk because you can't enlarge backwards. So the files on my disk still thought they were on one partition, even though it wasn't. This is probably why the install cd kept making grub try to boot from the wrong partition.

I've formatted since though so probs won't have the same problem again :)

Pricey

---

### Post by xXx 0wn3d xXx on 2006-04-15
When I'm starting the install, and press esc, I then select "Install Grub Boot Loader." But it takes me to partitioning...

---

### Post by PriceChild on 2006-04-15
[quote=MasterChief1234]When I'm starting the install, and press esc, I then select "Install Grub Boot Loader." But it takes me to partitioning...[/quote]

You have to be picky :P

Erm... i'm not completely sure, but i think if you don't change any partitioning settings, it will let you through this stage. Just ensure your root is still mounted as "/" and its bootflag is on.

Make sure none of the partitions options say that they'll be formatted before continuing!

I accept no responsibility for any suggestions :P I've always backed up all my data from the live CD before doing anything like this.

---

### Post by xXx 0wn3d xXx on 2006-04-15
[QUOTE=PriceChild]You have to be picky :P

Erm... i'm not completely sure, but i think if you don't change any partitioning settings, it will let you through this stage. Just ensure your root is still mounted as "/" and its bootflag is on.

Make sure none of the partitions options say that they'll be formatted before continuing!

I accept no responsibility for any suggestions :P I've always backed up all my data from the live CD before doing anything like this.[/QUOTE]
It's mounted as /media/hd3. Can I change it to / and continue without formatting ?

---

### Post by xXx 0wn3d xXx on 2006-04-15
What else can I do ?

---

### Post by xXx 0wn3d xXx on 2006-04-15
Anyone ?

---

### Post by johso on 2006-04-15
[QUOTE=MasterChief1234]Anyone ?[/QUOTE]

Easy now! ;-)

I think this would work out for you:
[http://www.shahidhussain.com/wordpress/index.php?p=33](http://www.shahidhussain.com/wordpress/index.php?p=33)

---

### Post by xXx 0wn3d xXx on 2006-04-15
> **johso]Easy now!  said:**
> http://www.shahidhussain.com/wordpress/index.php?p=33[/url]
Nope, it didn't work :( I am just going to re-install. Thank you for trying to help though.

---

### Post by r4ik on 2006-04-15
Not so fast maybe this one,

 Default  GNOME - HOWTO: Restore GRUB (if your MBR is messed up)
Written by vnbuddy2002

Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Good luck!.

---

### Post by PriceChild on 2006-04-15
Lol that's what i meant :)

Sorry i didn't explain it very well and didn't show much confidence :P

Pricey

---

### Post by xXx 0wn3d xXx on 2006-04-15
I just reinstalled, this is kinda nice for two reasons:

1. I wanted to switch to reiserfs (sp?) for a faster filesystem.

2. When I tried to compile the new 2.16.5 kernel, it was broken and caused problems on my system.

---

### Post by r4ik on 2006-04-15
[QUOTE=PriceChild]Lol that's what i meant :)

I know,
Sometime's it helps when it is writtin just different.
But it doesnt matter now does it :)

---

### Post by ububaba on 2006-04-20
[QUOTE=r4ik]Not so fast maybe this one,

 Default  GNOME - HOWTO: Restore GRUB (if your MBR is messed up)
Written by vnbuddy2002

Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Good luck!.[/QUOTE]

Are you trying to say by this method one is able to save all old configurations
etc. None of the files like mp3 or mail etc will get wiped out at all

---

### Post by johso on 2006-04-21
Well, yea, since it'll just boot the Ubuntu you have installed. Nothings changed, GRUB is just reinstalled.
But be careful to do it the right way, because if you don't, then you'll be likely to end up with a wiped partition.

---

### Post by cotcot on 2006-04-21
This is my suggestion.

Pop in a live CD and go to terminal. As root : Make a directory /mnt/breezy (mkdir /mnt/breezy). Mount your breezy partition on this directory (mount /dev/hda? /mnt/breezy). Change root to the root partition of breezy (chroot /mnt/breezy /bin/bash) and do a grub-install (grub-install /dev/hda).

Hda? is the partition where you have you breezy on.

---

