---
title: "Mounting ISOs, Just Not Working"
date: 2005-03-07
forum: General Help
---

### Post by thorN on 2005-03-07
Hi, I've got an .ISO image on my hard drive that I want to grab files off.
I thought I'd mount to a virtual CD drive, and copy the files from there.

However, following the ubuntuguide.org tutorial (modprobe loop, mount) doesn't work, I get a "bad fs, bad everything" error.

Following instructions on this forum, the next thing I did was try using the "losetup" command, to make a loop-device which I can mount (I think this is how it works?) - but this didn't work either.

I also saw mentioned a CDemu, which I got working but doesn't work with .ISOs, as far as I can tell.

Is there anything I can do except burn it to a precious, valuble CD?

---

### Post by Juergen on 2005-03-07
> However, following the ubuntuguide.org tutorial (modprobe loop, mount) doesn't work, I get a "bad fs, bad everything" error.Works for me. 
Did you verify the checksum for the iso?
> Is there anything I can do except burn it to a precious, valuble CD?
:-) Try a CD/RW

---

### Post by alastair on 2005-03-07
"... a precious, valuble CD?"

You mean the really expensive $1 ones?

Try :

sudo mount -o loop -t iso9660 /home/data/cddata.iso /mnt/cdrom

Replace the paths with the correct ones.

---

### Post by thorN on 2005-03-07
[QUOTE=alastair]"... a precious, valuble CD?"

You mean the really expensive $1 ones?

Try :

sudo mount -o loop -t iso9660 /home/data/cddata.iso /mnt/cdrom

Replace the paths with the correct ones.[/QUOTE]
 I mean the really expensive 10p ones.

Yeah, that's the command I used (correct paths of course).

I'm at home now, so here's the error I get:

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       or too many mounted file systems
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)

---

### Post by alastair on 2005-03-07
Is it an iso9660 filesystem?

Perhaps something's wrong with it? How was it made?

---

### Post by thorN on 2005-03-08
[QUOTE=alastair]Is it an iso9660 filesystem?

Perhaps something's wrong with it? How was it made?[/QUOTE]
 What I'll do is: When I get home, I'll try a different ISO (Don't know why I didn't think of this earlier) and get back to you.

I'm guessing it's iso9660. But what other ones are there?

It was made in Nero on Windows I think.

---

### Post by earobinson on 2005-03-14
Im having problems to

mount -o loop -t iso9660 EMPEROR1.iso /mnt/iso
mount: could not find any device /dev/loop#

---

### Post by fdoving on 2005-03-15
[QUOTE=earobinson]Im having problems to

mount -o loop -t iso9660 EMPEROR1.iso /mnt/iso
mount: could not find any device /dev/loop#[/QUOTE]
 You don't have support for loop devices. Try 'sudo modprobe loop'
If it works 'sudo echo loop >> /etc/modules' to load the module during boot.

---

### Post by thorN on 2005-04-22
I found the cause of the problem.

(Or to be more precise, the Gnome Archive Manager did.)

Turns out the .ISO file was corrupt.

D'oh.

---

### Post by Volfied on 2007-06-11
Same happened to me, too. Instead of Archive Manager, it was the Burn CD option that made me aware of the actual problem.

So yeah, check your MD5sums ^^

---

