---
title: "How do I remove GRUB?"
date: 2010-03-10
forum: General Help
---

### Post by Eyaare on 2010-03-10
OK, so currently I have GRUB, which dual boots between XP and Ubuntu Netbook Remix (UNR). Then, if I select XP I get windows asking me if I want to boot XP or UNR (because I have it installed both as a separate partition AND in windows). I want to remove the separate partition, but BEFORE I do that I want to get rid of GRUB. I don't have my XP disk or whatever, but I DO still have both OS's running and bootable.
Basic rundown:
Partition A-
XP
UNR (installed inside Windows)
Partition B-
UNR (again, but with it's own partition)

I don't want partition B.

Basically, I want a way to remove GRUB through Ubuntu or XP. Any ideas?

---

### Post by mechro on 2010-03-10
You can easily remove Grub but you need to replace it with an XP bootloader.

If you don't have an XP disc, did you back up your Windows XP boot/MBR before replacing it with Grub?

---

### Post by Eyaare on 2010-03-10
Probably not. I'm not entirely sure what that means, so probably the answer's no.

I don't necessarily need the Windows booter, though, if I could get GRUB on the Ubuntu Netbook Remix I intend to keep instead of the partition I want to destroy, right? 

Because it's my understanding GRUB is on the partition I want to destroy. Could it be moved?

---

### Post by egalvan on 2010-03-10
UNR installed *inside* Windows is a WUBI install,

It is run from within Windows, *after* Windows starts..
and GRUB has nothing to do with it.

The MBR can be returned to a MS-type by using the Recovery Console. I have no experience with this, others will have to chime in.

I used to use 

```
fdisk /mbr
```


Now I use SuperGRUB for these chores... 

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

it has an automatic MBR restoration on it.

It´s a failry small download.

Works a treat.


Once the MBR is fixed, you can use Windows to erase the partition you don´t want, and format it to NTFS or some such.
Or use the partiton editor within UNR,
or boot with a gparted livecd.

---

### Post by hhh on 2010-03-10
Stop. If you indeed used WUBI...

You want to KEEP the Ubuntu partition and DELETE the WUBI install, as hard disc access on the WUBI install is slower.

So just remove the WUBI install from Windows via Control Panel>Add/Remove Programs>Ubuntu (or similar name, I haven't used the netbook remix).

Keep Grub, keep your dedicated Ubuntu install and dual boot to Windows.

Or not, it's your computer.

---

### Post by Eyaare on 2010-03-10
> **hhh said:**
> Stop. If you indeed used WUBI...

You want to KEEP the Ubuntu partition and DELETE the WUBI install, as hard disc access on the WUBI install is slower.

So just remove the WUBI install from Windows via Control Panel>Add/Remove Programs>Ubuntu (or similar name, I haven't used the netbook remix).

Keep Grub, keep your dedicated Ubuntu install and dual boot to Windows.

Or not, it's your computer.

Well, thing is, it's my understanding that having WUBI and XP means they'll both use the same hard drive space, in different ways. So if I free up space in my Ubuntu/WUBI OS the free space will automatically be usable in Windows XP, without me needing to manage partitions or any of that ****. And with 40GB of laptop space and a consistently changing lineup of games on my laptop, this becomes a very useful thing.

On the other hand, is there any way to run recovery console in XP, without the disk? Like, a built in exe file or something that I can do that on?

---

### Post by coffeecat on 2010-03-10
> **Eyaare said:**
> On the other hand, is there any way to run recovery console in XP, without the disk? Like, a built in exe file or something that I can do that on?

I believe not.

But re-read egalvan's post. Use Supergrubdisk to restore the Windows MBR, if that's what you want to do. Supergrubdisk is a useful thing to have around, and it only takes seconds to repair the mbr with it. Whereas running FIXMBR (that's the command you would need) from the recovery console in the XP install disc is painfully slow. Take it from me - I've done both.

Personally I would go for Ubuntu in its own partition rather than the wubi version, but with your small hard drive I can understand your reasoning.

---

### Post by hhh on 2010-03-10
> **Eyaare said:**
> Well, thing is, it's my understanding that having WUBI and XP means they'll both use the same hard drive space, in different ways. So if I free up space in my Ubuntu/WUBI OS the free space will automatically be usable in Windows XP, without me needing to manage partitions or any of that ****. And with 40GB of laptop space and a consistently changing lineup of games on my laptop, this becomes a very useful thing.
Right. The space in your Windows partition will be available if you remove WUBI. If you need more space than that you'll need to shrink or delete the *real* Ubuntu partition and expand the Windows partition with Gparted or a similar program. If you delete the Ubuntu partition you'll need to restore Windows' MBR with SuperGrubDisc or a similar program.

> On the other hand, is there any way to run recovery console in XP, without the disk? Like, a built in exe file or something that I can do that on?
No, but you can create a disc if you don't have your install CD...
[http://tips.vlaurie.com/2006/05/recovery-console-for-those-without-an-xp-disk/](http://tips.vlaurie.com/2006/05/recovery-console-for-those-without-an-xp-disk/)

---

### Post by Eyaare on 2010-03-10
OK, I found a recovery console only XP CD via google, ran fixmbr and I'm fixing up the partitions through Partition Wizard now.

Seems to be working. Thanks for the help.

---

### Post by psusi on 2010-03-10
> **Eyaare said:**
> Well, thing is, it's my understanding that having WUBI and XP means they'll both use the same hard drive space, in different ways. So if I free up space in my Ubuntu/WUBI OS the free space will automatically be usable in Windows XP, without me needing to manage partitions or any of that ****.

No.  When you installed wubi you should have had to tell it how much space to reserve for the install.  It then created a file that big within the Windows filesystem to hold Ubuntu.  That space is used as far as Windows knows, whether or not Ubuntu is using it.

---

