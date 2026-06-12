---
title: "I have lost the boot loader"
date: 2006-06-11
forum: General Help
---

### Post by kloshar on 2006-06-11
Well, I have the problem here (sory if the forum is not right ). I wanted to install Windows Xp, so during the installation, I deleted C: partition and previous installated windows 98 se without touching the linux partitions!!! and tried to install winxp. Well, something went wrong with CD but it does not metter. The point is that I lost boot loader (probably it was lilo). So I cannot load linux now. I am very upset because I spent a lot of time with ubuntu and I do not want to lose everything. What shall I do to load my ubuntu (windows does not metter now, I will repair and install it later) ? Maybe change something in c:/boot.ini ?? Please, help me. 

Thank you and best regards to all!

edit ... as I can see in my linux boot folder, the boot loader is Grub.

---

### Post by kloshar on 2006-06-11
Oh, right now I am using knoppix. :mad:

---

### Post by mumushi on 2006-06-11
[QUOTE=kloshar]Oh, right now I am using knoppix. :mad:[/QUOTE]

I know this will help you [http://ubuntuos.com/2006/03/howto-restore-grub]("http://ubuntuos.com/2006/03/howto-restore-grub")

---

### Post by elamericano on 2006-06-11
Doesn't the Dapper install CD have a "Restore GRUB" option now?

---

### Post by kloshar on 2006-06-11
I have Breezy. 

Before I read the mumushis post, I deleted the windows partition. And when I want to boot the system, it says: Error loading operating system. I hope I didnt do anything wrong with that? Can I still do what is written in the link?

thank you!

---

### Post by kloshar on 2006-06-11
I dont really understand that advice:

> Mount your appropriate linux partions
 /
 /boot
 swap etc.

How to mount them?
I have:
Free space
/etc/hda2 ext2
/swap

And thats it. I havent found any function to mount them.

Sory for newbie question. =; 

tnx

---

### Post by djsroknrol on 2006-06-11
I believe if you boot from the breezy CD, when you get to the partitioning part, you hit "Esc" and zgo to a menu that will let you reinstall(install?) GRUB....scroll down to it and it will build(rebuild?) what you need...

I would also reinstall MS before you do GRUB.....

---

### Post by kloshar on 2006-06-12
[QUOTE=djsroknrol]I believe if you boot from the breezy CD, when you get to the partitioning part, you hit "Esc" and zgo to a menu that will let you reinstall(install?) GRUB....scroll down to it and it will build(rebuild?) what you need...
[/QUOTE]

I am afraid that doesnt change anything. :confused: :(

---

### Post by kloshar on 2006-06-12
Is there maybe anything in grub folder that should be needed to change?

---

### Post by Rui Pais on 2006-06-12
hi,
if i understand you do not deleted you boot partition, right?
So the olny thing that happended was that win installation give you its customary gift... deleting grub starter from MBR. :(

Try to boot from the install cd,
open then a terminal and do
```
sudo grub-install /dev/hda
```

if that fails then you need to tell grub-install where /boot is
```
sudo grub-install --root-directory=/boot /dev/hda
```

hth

---

### Post by anaconda on 2006-06-12
Yep.
Rui Pais is right. 
Just wanted to sy, that if you dont have the install-cd, you can do the same with knoppix-cd.

Mount your linux-partition (it is propably automounted), and run the grub-install from there. (it is in /sbin)

---

### Post by kloshar on 2006-06-12
If only I saw the answer before ...:( 

I played with the partitions with partition program on Mandrake and I guess it formated my Linux partition (knoppix does not show any data on it). But I dont know how is it possible, coz I strictly told the program not to format the partition. Would it be waste of time to try to recover the partition?

---

### Post by Rui Pais on 2006-06-12
hi, sorry to hear it...

by "formated my Linux partition" do you mean the ***ALL*** linux partition or a separated /boot partition?

Anyway, if you just delete a partition you can usually recover by simply redo thei partition entry without format, but if you really format it will be more easier to reinstall (dapper is far better then breezy anyway) then try some recover tool...

But double check it. The few things that Mandrake do it that work and work well was that partition program (i used a lot before ubuntu lifecd+gparted appeared and never failed once). Check if knoppix is really show the partitions mounted or just the mount points (naturally empty).

---

### Post by kloshar on 2006-06-12
I think the program formated ext2 partition. Not sure. 

But I really dont know what kind of partition it is because linux doesnt want to install on it. It is bootable and /etc/hda2

---

### Post by Rui Pais on 2006-06-12
hi,
thats something wrong. 
You have said before but i thought it was a typo.
There is no /etc/hda2 or at least that don't make much sense in this contest (do you mean /dev/hda2 ?)

Do you mind to post the outputs of the following:
From your knoppix or from the installcd type in a console:
```
df -h
```
what it lists?

if no /dev/hda appears on the list do:
```
mkdir hda1 hda2
sudo mount /dev/hda1 hda1
sudo mount /dev/hda2 hda2

```
and then check what is in there:
```
ls hda1 hda2
```

---

### Post by kloshar on 2006-06-12
I had nothing else to do as make new partitions on free space and install fresh copy of Ubuntu. And now I'm asking you for help how to recover files on my old linux ext3 partition?

---

### Post by kloshar on 2006-06-13
Anybody? How to recover formated linux partitions? :confused:

---

