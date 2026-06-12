---
title: "Quick Question"
date: 2011-11-28
forum: General Help
---

### Post by gennatolls on 2011-11-28
Trying to convert a new user from windows and want to make it as easy as possible for them. The goal is to have a dual boot pc with ubuntu 11.10 and windows 7.(Windows 7 is already installed) I dont have physical access to the pc so wanted to double check before I proceed. Can the ubuntu installer handle shrinking the windows partition to make room for ubuntu?  Or do we still need to use the disk management tool in windoze. Sorry easy question but I haven't dual booted since 9.10. Thanks!

---

### Post by roger_1960 on 2011-11-28
Hi

Much safer to use the windows partition tool.  Also don't forget to make sure your friend defrags the partition and does a good backup of all data before editing partitions and has a recovery method for windows just in case it all goes wrong!

---

### Post by Habitual on 2011-11-28
Be certain to have a Windows CD (installation media) handy.

---

### Post by jonobr on 2011-11-28
Have you tried [Wubi]("http://www.ubuntu.com/download/ubuntu/windows-installer")?
May be a better approach for the person to 'kick the tires"

---

### Post by WorMzy on 2011-11-28
I recommend against the use of Wubi. More trouble than it's worth.

As previously mentioned, use the Windows partition software to modify Windows partitions, using gparted (for example) to shrink a fragmented NTFS partition can result in data loss and sometimes, as a result, corrupted system files. The last thing you want to do is install this snazzy new operating system that your friend doesn't know how to use, only to find out that it's murdered the operating system that he *does* know how to use, as well as eating up all his ultra_super_important_documents.docs. 

That sort of thing can really ruin a friendship, as well as making the potential convert distrust Linux.

---

### Post by jonobr on 2011-11-28
Hey WorMzy,

Quick question for you, and I dont mean to steal this thread,
I have used Wubi on a few machines for people wanting to play around with Ubuntu.
Most recently a few Dells, - an old inspiron 710m and some fancy up to date latitude.
I do recall an issue on wireless with a Vaio, but maybe you could share more on ones you had problems with,
maybe you could drop me a note off this thread

Thanks

---

### Post by gennatolls on 2011-11-28
Thanks to all for your input, the last thing I wanted to do was make someones life harder and put a negative view on Ubuntu. I kept getting the impression it was safe to use the installer from the official Ubuntu documentation but my gut feeling was telling me otherwise. I'm glad I double checked. I wanted to skip the WUBI route because I have no personal experiences with it and the potential user wants to learn more about Linux, thus making the true install a good bit of experience for him.

Jonobr, I'm glad you mentioned the Vaio issue. My friends laptop is a Vaio giving me more reason to recommend a true install.

Thank you all very much for your input!

---

### Post by linuxrev on 2011-11-28
Why not give your friend a Ubuntu Live CD to try it out? Least risky, and if it meets expectations, installation is easy from there.

---

### Post by WorMzy on 2011-11-28
> **jonobr said:**
> Hey WorMzy,

Quick question for you, and I dont mean to steal this thread,
I have used Wubi on a few machines for people wanting to play around with Ubuntu.
Most recently a few Dells, - an old inspiron 710m and some fancy up to date latitude.
I do recall an issue on wireless with a Vaio, but maybe you could share more on ones you had problems with,
maybe you could drop me a note off this thread

Thanks

The main problem is that people treat it like a permanent OS, when it's not designed to be used for anything more than a temporary "trial" of the OS. Another problem stems from the way that updates to grub are handled -- there's regularly posts from disgruntled Wubi users on here who've allowed the update manager to install some updates (including grub), only to find that they can no longer boot *any* operating systems, because the grub update has overwritten the NTLDR but can't point to the grub files because they're not accessible from outside of the looped root.disk.

There's also the frequent "HALP, Y I R RUN OUT OF SPACE?!" complaint from Wubi users with poxy 5GB root.disks.

---

### Post by jonobr on 2011-11-28
Thanks for the feedback, the second point was a good one,
points 1 and 3 are people who will always have problems no matter route they take.

---

