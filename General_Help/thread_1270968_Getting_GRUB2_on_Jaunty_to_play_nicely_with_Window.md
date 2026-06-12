---
title: "Getting GRUB2 on Jaunty to play nicely with Windows Server 2003"
date: 2009-09-20
forum: General Help
---

### Post by jrothwell97 on 2009-09-20
Since I sadly need to work with The Devil's Own Programming Language (VB.Net) for my computing class, I acquired a copy of Windows Server 2003 through Dreamspark, and stuck it on a spare hard drive I had lying around. It was installed in the slave position to the master drive, which has Ubuntu Jaunty, Debian Lenny and the Linux swap partition.

Naturally, Windows Setup hosed the bootloader (I had GRUB2 installed), so I have to go about reinstating it. The way I hope to do it (to avoid screwing up Windows's startup settings) is to use the Windows bootloader (ntldr) to chainload GRUB stage 1, which will then start GRUB as normal and allow me to boot into Ubuntu and Debian.

There seem to be two main problems with this:

[list=1][*]All the HOWTOs and manuals on the Internet detailing this process use GRUB Legacy. I am using GRUB2.
[*]I cannot find a way to boot into the Ubuntu installation (GRUB floppies don't seem to work).[/list]

As I said, I'd like (if possible) to avoid installing GRUB back to the MBR. If someone cleverer than me has a step-by-step solution, I'd love to hear it :D

Thanks in advance.

---

### Post by oldfred on 2009-09-20
This site has instructions on creating a Grub2 CD or floppy.
[http://www.justlinux.com/forum/showthread.php?threadid=152790](http://www.justlinux.com/forum/showthread.php?threadid=152790)

I installed Karmic and put the grub2 into the partition. It gave me a warning in CAPS saying not to do this but I am able to chainboot from my old grub entries to grub2 and karmic.

I added a tiny Grub only partition to allow chainbooting the installs on my sdc drive, but still primarily boot into my sdb drive and chainboot to sdc's grub when I want to play with the other installs. Old grub allows me to chainboot to grub2 in my karmic partition.
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

---

