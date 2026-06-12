---
title: "cant pull windows from grub after sata cable swap."
date: 2009-09-13
forum: General Help
---

### Post by redonwhite on 2009-09-13
Hello all,
Last night I installed a new graphics card and had to remove my sata cables connecting my two hard drives.  One hard drive has ubuntu on it and the other xp.  When re-connecting them I decided to plug them into different spots.  Sata0 input and Sata1 input.  They had been in sata4 and sata5 inputs.  When rebooting I forgot I needed to get onto windows to "de-authorize" some games by EA before I reinstalled my OSs.   But when I selected xp in grub it could not find xp.  Ubuntu was found no problem.  Is there some way I can access the hard drive with xp on it so I can deauthorize those games?  I was thinking I might just have to dig under the desk and try pop the cables back in their old spots to get xp to boot.  Let me know what you guys and gals would recomend.  Thanks!

---

### Post by NoaHall on 2009-09-13
Why would you want to plug them into different slots? Put them back into their old places , and then try.

---

### Post by Bucky Ball on 2009-09-13
> **noahall said:**
> why would you want to plug them into different slots? Put them back into their old places , and then try.

+1

---

### Post by redonwhite on 2009-09-13
> **NoaHall said:**
> Why would you want to plug them into different slots? Put them back into their old places , and then try.

Because my graphics card is over 10 inchs long and I could not fit them comfortably on the right angle sata inputs on my gigabyte board.

---

### Post by NoaHall on 2009-09-13
Hm. Now that's a tricky problem. Do you only have one port you could put your graphics card on?

Well, you want to make sure it loads the Ubuntu hard drive first, as that one is probably the one with GRUB on.

---

### Post by louieb on 2009-09-13
Quick and dirty. [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/")

or post output of** sudo fdisk -l  **
and the windows entry from /boot/grub/menu.lst 

probably ca figure out how to get win to boot from that.

---

### Post by redonwhite on 2009-09-13
> **NoaHall said:**
> Hm. Now that's a tricky problem. Do you only have one port you could put your graphics card on?

Well, you want to make sure it loads the Ubuntu hard drive first, as that one is probably the one with GRUB on.

I can manage the cables back to the right angle sata slots for the time being I was just wondering/hoping there was another way to get on my xp drive to avoid it.   My rig is getting way to heavy to keep pulling it out from underneath the desk.  Haha =).

---

### Post by NoaHall on 2009-09-13
Well, I'd use super grub as mentioned above, but reinstalling XP won't fix grub - it'll make it break.

---

### Post by redonwhite on 2009-09-13
> **louieb said:**
> Quick and dirty. [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/")

or post output of** sudo fdisk -l  **
and the windows entry from /boot/grub/menu.lst 

probably ca figure out how to get win to boot from that.

Thanks for the reply!  I'm stuck at work now.  Can't access the computer.  =(.  If I don't end up caving in and swaping the inputs ill post this output when I get home.  Thanks.

---

### Post by redonwhite on 2009-09-13
> **NoaHall said:**
> Well, I'd use super grub as mentioned above, but reinstalling XP won't fix grub - it'll make it break.

Thanks.  I was planning on reinstalling both OSs from the get go.  Just gotta de authorize a few games.   EA!!!!!!

---

### Post by NoaHall on 2009-09-13
Oh god, I hate EA with it's nonsense. They cause people to spend money on games, and then find out they can't reinstall them after reinstalling a OS. Scum.

---

### Post by redonwhite on 2009-09-13
> **NoaHall said:**
> Oh god, I hate EA with it's nonsense. They cause people to spend money on games, and then find out they can't reinstall them after reinstalling a OS. Scum.

I know, its such a pain.  Great games but this "de-authorizing" is anoying.  I even kept each de-authorizing tool for each game on my desk top.  Thought it would help me remember those games needed to be de-authorized before any os reinstalls.  Haha guess it didn't help much.  Especially since I was silly with excitement to install my new gpu.  Haha

---

### Post by biebel on 2009-09-13
First do a 
> 
sudo blkid

This will tell you the drives' identifiers in linux

than do a 
> 
cat /boot/grub/device.map

device.map shows the grub identifiers and their corresponding linux identifiers

after that
> 
sudo gedit /boot/grub/menu.lst

and edit the grub entry for windoze accordingly

---

### Post by redonwhite on 2009-09-13
> **biebel said:**
> First do a 

This will tell you the drives' identifiers in linux

than do a 

device.map shows the grub identifiers and their corresponding linux identifiers

after that

and edit the grub entry for windoze accordingly

Thank you very much.  I will do this as soon as I get home and post my success hopefully later.  Thank you again!

---

### Post by redonwhite on 2009-09-13
> **biebel said:**
> First do a 

This will tell you the drives' identifiers in linux

than do a 

device.map shows the grub identifiers and their corresponding linux identifiers

after that

and edit the grub entry for windoze accordingly

Here is the output of what you told me to do...

```
 name@name:~$ sudo blkid
[sudo] password for name: 
/dev/sda1: UUID="8C3027C23027B1DE" TYPE="ntfs" 
/dev/sdb1: UUID="f738977f-62c4-4e11-8ec0-925cc67fb8f7" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="19f14027-1d7f-40f5-aac0-d19a37b1f4d1" 
name@name:~$ cat /boot/grub/device.map
(hd0)	/dev/sda
(hd1)	/dev/sdb
name@name:~$ sudo gedit /boot/grub/menu.lst 
```

Here is what the "windows" is set up as in the menu list....

```
 # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

I changed sdb1 to sda1 but that did nothing.  What am i missing?  =)  Thanks for your help!

---

### Post by louieb on 2009-09-13
> **redonwhite said:**
> I changed sdb1 to sda1 but that did nothing.  What am i missing?  =)  Thanks for your help!
? in which file did you make the change?
```
 
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
makeactive
chainloader    +1

```Looks like you took the drive plugged in sata5 and pugged it in to sata0 reversing there BIOS order. Swap the sata cables or try this grub entry - [B]not both.

note to biebel  : [/B]blkid had a bug where its cache didn't not alway get updated. giving incorrect results don't know if its been fix yet. but to get around use:
```
sudo blkid -c /dev/null
```

---

### Post by redonwhite on 2009-09-13
> **louieb said:**
> ? in which file did you make the change?
```
 
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
makeactive
chainloader    +1

```Looks like you took the drive plugged in sata5 and pugged it in to sata0 reversing there BIOS order. Swap the sata cables or try this grub entry - [B]not both.

note to biebel  : [/B]blkid had a bug where its cache didn't not alway get updated. giving incorrect results don't know if its been fix yet. but to get around use:
```
sudo blkid -c /dev/null
```

You rock my socks.  Thank you so much.  That grub entry worked perfectly.  Thanks again!

---

### Post by biebel on 2009-09-13
> note to biebel : blkid had a bug where its cache didn't not alway get updated. giving incorrect results don't know if its been fix yet. but to get around use:
Thanks for the headsup on that one. Will keep that in mind as I use it just about any time I want to make adjustments to grub or fstab.

Glad you can boot into windows again redonwhite and sorry for not being clear enough.

---

