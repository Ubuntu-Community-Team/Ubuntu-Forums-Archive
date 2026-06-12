---
title: "Uninstall Ubuntu to get Vista back? (newbie)"
date: 2010-03-10
forum: General Help
---

### Post by blommee on 2010-03-10
Hi,

Today i heard about Ubuntu and i got really excited, so i just downloaded the thing and started the install! Everyone was like yeah its the best and shiz so i decided to get rid of my vista partitions and fully install Ubuntu.

Now, I have LOTS of problems with ubuntu, and im not really the person that has the patience to install alot of programs to make things work.

So i was like lets just reinstall my vista?

I insert my backup disc (acer laptop) which normally goes like automatic, but now it doesn't..

I think it has to do with the fact ubuntu isn't the normal partition for it, and so the disc wont regognise it ...

Could anyone tell me how to delete ubuntu (yeah i know u guys love it, but i dont) and get my vista installed again?

Help would be really appreciated :icon_frown:

Grtz
Blomme
*sorry for my "bad" english i hope u guys understand my point. 
Also try not to use alot of difficult words :)

---

### Post by Ferb on 2010-03-10
I am sorry to hear that your first experience with ubuntu was bad.
So your pc doesn't want to boot from the backup disks?
Have you made sure that the boot order has been set correctly in the bios?
I take it that this is a laptop we are talking about?
You should be able to type one of the f-keys to get a boot menu

---

### Post by desnaike on 2010-03-10
If u allowed ubuntu to install to the entire hdd u may have wiped the the recovery hidden partition on your acer's hdd if so the recovery cd may not work. If u set up dual boot with vista the os may still be there along with the recovery partition can u elaborate.

---

### Post by QIII on 2010-03-10
Sorry you had such a bad time.  That is unusual.  We'd have been willing to help.

If you really want to go back to Windows, I won't give you any grief.

You will need to reformat your entire drive as NTFS, since Windows often pukes when it sees ext3 or ext4.

If you use the LiveCD, go to Applications | Terminal and in the terminal type 

```
gksudo gparted
```followed by your password (which will not show up, so don't worry if you don't see anything showing up while you type it).   Edit:  Actually, running from the LiveCD, you may not need to enter a password.  Not sure.  So you may just be able to issue "gparted" in the terminal.

This will get you to an application that will allow you to delete all the partitions on the drive and create one new, large NTFS partition out of your whole drive.

Remove the LiveCD, shut down and restart with the Windows installation disk in the drive.

Just for our edification, could you describe some of the problems you ran in to?


PS:  If your "back up disk" is the OEM "restore" disk, you will get back a fresh copy of Windows as it was when you bought the machine.  Everything else will be gone.  This assumes:  Your BIOS is set to boot first from your optical drive and that your disk will install a complete OS without a partition with restoration data existing.

---

### Post by wilee-nilee on 2010-03-10
Acer has a ISO download for XP that is slipstreamed to sp3, I suspect you can get a Vista ISO download as well if needed.

---

