---
title: "How to restore old MBR (ntldr)"
date: 2009-09-29
forum: General Help
---

### Post by GrayBear on 2009-09-29
I just installed Ubuntu 9.04. To be honest I think it's a very bad idea not to let users choose where to install the grub boot loader (which hard disk, or which partition etc). And it's also bad that Ubuntu doesn't make a backup copy of the MBR before installing itself.

however, before installing Ubuntu, I made a copy of the MBR like this:
```
dd if=/dev/sda of=MBR.WIN count=1
```which resulted in a 512 Bytes file
Is it enough to do the following, to restore the old boot loader (ntldr i guess) that Windows XP was using?
```
dd if=MBR.WIN of=/dev/sda count=1
```I am using grub4dos, so I will be fine starting Ubuntu

---

### Post by stinger30au on 2009-09-29
why back it up for???

have you done a dual boot and find you now get an error like

ntldrl missing 

when booting windows?

---

### Post by GrayBear on 2009-09-29
> **stinger30au said:**
> why back it up for???
have you done a dual boot and find you now get an error like
ntldrl missing 
when booting windows?
Yes, those kind of things happened to me before, so it's just better to take some extra safety measures. Better safe than sorry.

I preffere to use the boot loader of the Windows and add all my Linux installations to grub4dos. I am installing many distributions (ubuntu, kubuntu, xubuntu, fedora, opensuse etc), so I preffere to have just one place to start all of them from (that place is menu.lst of grub4dos), instead of having all those distributions re-writing the boot menu

Later edit: in addition, if I need to modify menu.lst, I can edit in Windows too. Keeping menu.lst on a ext2 partition means that editing it from Windows is quite difficult. It is possible, but its a bit painful

so, there are many advantages in using grub4dos

---

### Post by rbc on 2009-09-29
> dd if=/dev/sda of=MBR.WIN count=1

> dd if=MBR.WIN of=/dev/sda count=1

These are OK, with one correction, that you probably actually did, but forgot to include in the posting. You need to specify the block size, e.g.

dd if=/dev/sda of=MBR.WIN count=1 bs=512

This will get you the boot loader code, and the partition table information.

dd if=/dev/sda of=MBR.WIN count=1 bs=446

will get you just the boot loader code

---

### Post by oldfred on 2009-09-29
If you are going to be in Windows a significant amount I understand you desire for Grub4dos. But, I prefer chainbooting. 

Yes I have to go thru 2 menus but rarely have to edit any menu.lst as each is auto updated as a new kernel is downloaded. I only have to edit the chainboot menu if I add or delete a distrubution.

---

### Post by Arand on 2009-09-29
Yes your method is correct, (adding the bs=512).
And yes I fully agree with you that it's a good idea to back this up, since it's the only thing that ubuntu is incapable of restoring upon removal.

The problem with automatically backing it up on install is:
1. Where would it be stored?
2. How would you restore it in a user-friendly way?
   - Ubuntu-uninstaller on the liveCD?
3. How would it sense that that specific windows bootloader was still present in the same location, so as to not hoose the system completely?
- Arand

---

### Post by GrayBear on 2009-09-29
> **Arand said:**
> Yes your method is correct, (adding the bs=512).
And yes I fully agree with you that it's a good idea to back this up, since it's the only thing that ubuntu is incapable of restoring upon removal.

The problem with automatically backing it up on install is:
1. Where would it be stored? I think that it would be very intuitive to save it in /boot/backups/MBR.OLD. But it also can ask the user if he wants to save it in another location too.
>  2. How would you restore it in a user-friendly way? First, at install time, Ubuntu shall tell to the user where the MBR backup was saved, and tell him to read further instructions in let's say "/boot/backups/README.txt". The readme shall contain instructions to restore with commands like "dd if=MBR.WIN .." etc.
>      - Ubuntu-uninstaller on the liveCD? Not uninstaller, but I think Ubuntu CD should contain some recovery options. Create an entry at the begining, near the other options (Install Ubuntu, Test memory), an entry like "Recovery tools". There, between other menus, offer the user the option to restore MBR
>  3. How would it sense that that specific windows bootloader was still present in the same location, so as to not hoose the system completely?  by hoose you mean scramble? 
Look, you don't have to be a computer specialist to be able to use one of the so many boot loaders available. There is gag, grub2dos, lilo, etc ([http://en.wikipedia.org/wiki/Category:Free_boot_loaders](http://en.wikipedia.org/wiki/Category:Free_boot_loaders))
I find it very convenient to use grub4dos:
- I can edit the boot options while I'm in Windows.
- Even if I mess the Linux partitions completely, Windows will not be afected
and other advantages.

I am using grub4dos, and my MBR is the plain old ntldr of Windows XP. Ubuntu has no problem with it at all. I copied the boot options from /mnt/hda5/boot/grub/menu.lst into C:\boot\grub\menu.lst and everything works smooth. It does not matter if one day I feel like deleting the Ubuntu partition (/mnt/hda5), Windows will still boot without any problem.

Ubuntu is the best Linux distribution, in my opinion. It is very user friendly. But it can still be improved a lot, to make the transition from Windows to Linux much more easier. For example another idea can be to offer the users the option to install grub4dos, so they can edit boot options from Windows if they feel more comfortable with that.

The philosophy should be like
"Install Linux, you can switch from Windows to Linux and come back anytime, take your time getting used to it, accessing your data from Linux"
not like
"Install Linux, and from now on, forget about Windows"

first approach would make people Windows users to forget about Windows faster. Because this is how things work. Users must feel comfortable using Linux, switching between the two systems, comparing them, accessing on system's files from the other.

---

### Post by oldfred on 2009-09-29
Ok it may not be intuitive but the Ubuntu installer will ask were to put the grub entry if you click advanced on the grub install screen, since the normal way to dual boot is to put Grub into the MBR.

If all you want to do is try Ubuntu the Wubi install is the best way to try it as it is like installing a program in Windows and does not change the MBR.

For those who want to go back there are many help files and reinstalling the MBR is easy with SuperGrub or your windows install CD. I typically like to have several ways to recover the MBR whenever I am doing major changes to the system.

Info on reinstalling:
Herman's uninstall Grub
[http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)

restore boot loaders Ubuntu Win xp Vista
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If your PC did not come with a complete Vista installation CD, you can download a Vista Recovery Disc at the following link:
Windows Vista Recovery Disc [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Vista will not repair XP(they create the boot sectors differently), for XP you can use your old win 98  disk.

---

### Post by Arand on 2009-09-29
::GrayBear:
1. The problem with that is that at the point where users realise they need the backup mbr, they've already deleted the ubuntu partition
At the same time, one pressing point that's being made with the installer is that it should be as simple as possible, therefore an option like this (backup your old bootloader sector and save it to [option]) might make it into the advanced bootloader option... maybe.  (And for this to work okay you'd need to start mounting partitions to save it to here as well --great-hassle).

2. In what way should it tell you? "Hello, important technomumbojumbo" -notification?
Although, if this only showed up in the case where you manually choose to save it, it might be acceptable.
Though, there definitely should be a readme, or even a simple script saved along with the mbr backup.

3. Hmm, I think adding more stuff to the boot menu might be a no-no (in favor of hiding complication for technophobic users) but just shoving a "recovery tools" under the [F6 -- other options] menu might be a solution here, a "recovery tools" menu alternative, in the live environment might be a good addition as well.

I'm still not sure whether ubuntu would do a better job than just promoting the use of the win CD for restoration though.

It would definitely be a good addition for ubuntu to put a backup file somewhere and document the fact in an accompanying readme, and on the online guide for uninstalling.

But implementing a recovery-tool proper, that's user-friendly enough to be in ubuntu per default, although it would be absolutely brilliant, and add a lot to the "friendlyness/sense of safety" of ubuntu...
I'm just saying it might be very tricky once it comes down to details.

I've actually been pondering over just this for some time:
1. Could ubuntu have a "backup/recovery tool" on the livecd?
2. (dd/partimage/ntfsclone/fsarchiver) are they mature/useful enough?
3. Should we just leave this to dedicated distros (Clonezilla SystemrescueCD Parted Magic et al.)?
4. Is it really useful to do things like "Hi, you have a 1TB harddisk, would you like to make a backup of it spanning 200 DVDs? (~worst case scenario)"
5. Would we be able to (re)write a GUI for this application to fit it into ubuntu properly?
6. etc....

  - Arand

---

### Post by GrayBear on 2009-09-29
>  I've actually been pondering over just this for some time:
1. Could ubuntu have a "backup/recovery tool" on the livecd?  Of course ! Or it can even have a separate Ubuntu rescue CD. IIRC, RedHat had such a rescue CD. And IIRC, other live distros were based on that CD.
Look, I recently tried SLAX and it's amazing. So many features, so easy to install, you don't even need a separate ext2 partition. You can install it on C:\ simply by extracting the files there, or even by copying the .iso file there. Has lots of features, easy to use as a recovery tool. Also other live Linuxes: SystemRescueCd, Finnix etc.
Those live linuxes are maintained by a single person each. So why not an Ubuntu rescue cd, when Cannonical has much more people available to do that? I am sure it can create an ultra-powerfull rescue cd.

>   2. (dd/partimage/ntfsclone/fsarchiver) are they mature/useful enough? Not sure, but defenately Ubuntu people can help a bit for making those programs more stable

>    3. Should we just leave this to dedicated distros (Clonezilla SystemrescueCD Parted Magic et al.)?  Defenately not. A serious distribution shall have its own rescue tools. Like the Win XP CD has its own rescue tools

>  4. Is it really useful to do things like "Hi, you have a 1TB harddisk, would you like to make a backup of it spanning 200 DVDs? (~worst case scenario)" :D
Not sure about creating a backup to DVD's but at least some basic recovery tools like fixig MBR, re-creating grub config file, reinstalling grub, resizing, backup and restore partitions, etc

>  5. Would we be able to (re)write a GUI for this application to fit it into ubuntu properly? Defenately. they just need to add some extra scripts to the already existing menus. The libraries for windows, interface are there already.

---

