---
title: "Mount an encrypted/password protected drive from a terminal?"
date: 2010-06-01
forum: General Help
---

### Post by dillandriskell on 2010-06-01
Hey!

Ok, so I'm trying to mount my USB external hard drive that's encrypted and
password protected. Normally that's no problem, a window pops up asking me for
the password, I enter as such and I can access my files. Here's the kicker
though, I'm not using a graphical interface right now (No X-session). It's a
long and probably uninteresting story, and I won't be using one for a while. 

So my question is how can I mount this USB external hard drive that's 
encrypted and password protected from a terminal? I've found plenty of guides 
on how to mount USB drives from a terminal, but none in my situation.

I can see the drive from "sudo fdisk -l", and I've mounted it to this computer
before from the graphical interface.

Any help with this question would be so appreciated.

---

### Post by new_tolinux on 2010-06-01
What is it encrypted with?

---

### Post by dillandriskell on 2010-06-01
> **new_tolinux said:**
> What is it encrypted with?

Hmm, I'm not sure if there's a name defining this that I should know. I used Ubuntu's default encrypting though if that helps. When I first formatted the drive it gave me a number of options, and the last was to encrypt and password protect it (which is what I chose).

---

### Post by new_tolinux on 2010-06-01
That's probably enough info. Ubuntu uses ecryptfs by default.

I don't know the command-lines to use it, but I'll guess you can find them the same way as I would (through any search-engine, for example google).
Edit: Another option is LVM with encryption, but I really don't know much about LVM, not to speak of how that's encrypted.

---

### Post by dillandriskell on 2010-06-01
> **new_tolinux said:**
> That's probably enough info. Ubuntu uses ecryptfs by default.

I don't know the command-lines to use it, but I'll guess you can find them the same way as I would (through any search-engine, for example google).
Edit: Another option is LVM with encryption, but I really don't know much about LVM, not to speak of how that's encrypted.

Alright thanks. You've given me some good research terms and enough to get me
going. If I figure it out I'll post it for completeness and for anyone else 
who comes across this thread with a similar question.

---

### Post by guffer on 2010-09-22
Here's what I do to mount my LUKS encrypted Seagate USB drive from a terminal...

To determine the device name (as I have >1):

[FONT=Courier New]sudo fdisk -l[/FONT]

Then mount it:

[FONT=Courier New]sudo cryptsetup luksOpen /dev/sdb2 external[/FONT]
[FONT=Courier New]mkdir -p /media/SEAGATE
sudo mount /dev/mapper/external /media/SEAGATE
[/FONT]

To remove:

[FONT=Courier New]cd /
sync
sudo umount /media/SEAGATE
sudo rmdir /media/SEAGATE
sudo cryptsetup luksClose external[/FONT]

---

