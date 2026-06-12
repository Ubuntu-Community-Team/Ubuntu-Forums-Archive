---
title: "broke windows, help?"
date: 2010-04-03
forum: General Help
---

### Post by ut40755 on 2010-04-03
so i did a virus scan in linux on my xp partition, and i deleted a few files i shouldnt have because linux discovered them as root kits.  one was called sp2.api, and another one i cant recall.  now i cant boot into xp due to a 7b BSOD.

is there anyway to restore deleted files from virus scanner, or is there a way to just do a drive restore?  i also have windows 7, would a drive restore fix it there?

if i did an xp repair, would it overwrite all boot options?  im assuming reinstalling just the OS would, and it would also erase all drivers and updates.  and honestly i dont use xp that much to be troubled with that.  i use 7 and sometimes ubuntu.

thanks for any help guys.

---

### Post by 2hot6ft2 on 2010-04-03
Did you delete bypassing trash or Move to Trash?
If you moved it to the trash try restoring them or it.
sp2.api sounds like a service pack.
If you used an anti virus program and quarantined them does it have a restore option?
If it does try using it to restore them.

Beyond that I can't help much with a wubi install.

---

### Post by ut40755 on 2010-04-03
i didnt meant to hit wubi, im using ubuntu.

im using the only virus scanner in the software manager.  it doesnt delete to the trash bin, and i deleted them, not quarantined (which ill never do again lol).

---

### Post by 2hot6ft2 on 2010-04-03
If you have access to another xp machine you can copy the sp2.api file from it and paste it back to where it was you deleted it from, and whatever the other file was if you can find it.
You may be able to find one you can download by searching for it with google, just be careful of where you get it from.
Not much else you can do if you can't restore it.
[Google search for sp2.api]("http://www.google.com/search?q=sp2.api&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")

Maybe try reinstalling service pack 2

---

### Post by ut40755 on 2010-04-03
yea i was thinking about that, but i dont know if i can find the right files.  and i cant reinstall anything cause xp wont even boot.

---

### Post by 2hot6ft2 on 2010-04-03
Ouch, the pains of learning can sting at times.

This is a good source: [http://www.bootdisk.com/](http://www.bootdisk.com/)

[xp recovery cd download]("http://www.google.com/search?hl=en&client=firefox-a&hs=ugb&rls=com.ubuntu:en-US:official&q=xp+recovery+cd+download&revid=1918441746&ei=OAa4S-7xDML88AbyyZHfBw&sa=X&oi=revisions_inline&resnum=0&ct=broad-revision&cd=2&ved=0CEEQ1QIoAQ")

---

### Post by ut40755 on 2010-04-03
indeed it can.  i have all my xp discs, but my question is, will reinstalling xp screw up the grub menus and xp drivers?

---

### Post by 2hot6ft2 on 2010-04-03
> **ut40755 said:**
> indeed it can.  i have all my xp discs, but my question is, will reinstalling xp screw up the grub menus and xp drivers?
It sure would. You would have to reinstall grub2 (and do the xp updates all over again along with drivers). If you can just use the repair file system option. Here's how to re-install grub just in case save it.

Using Ubuntu 9.10 livecd

Here assuming the Ubuntu partition is sda8,and /boot partition is sda6 (if you have a separate /boot partition).

Boot up ubuntu from the livecd,
Applications > Accessories > Terminal
and run:
```
sudo -i
```
To find out you partitions run
```
fdisk -l
```
Use that info (use the size if you know what the ubunu partition size is to know what is what) for the following.
```
mount /dev/sda8 /mnt
```
```
mount /dev/sda6 /mnt/boot  #skip this one if not have a separate /boot partition
```
You'll want to install grub to the drive that is first in the boot order in the BIOS
```
grub-install --root-directory=/mnt/ /dev/sda
```
Reboot removing the livecd in the process and once you're back in ubuntu run
```
sudo update-grub
```

Good luck.

---

### Post by 2hot6ft2 on 2010-04-03
I just realized you didn't say what version of ubuntu you have.

That's assuming you're using ubuntu 9.10 with a hard drive install. If you have another version of ubuntu the directions may be different.

---

### Post by ut40755 on 2010-04-03
yea, ubuntu 9.10 with drive install.  i was hoping it wouldnt come to that, and honestly, i think ill just wait till i reformat everything again (i do kinda often just to keep things clean).  ill try a few more things and see if anyone else chimes in.

thanks for ur help though.

---

### Post by 2hot6ft2 on 2010-04-03
Sounds like a plan. I wish you luck, and you're welcome for what it was worth.):P

If you do reinstall xp you may want to save all the updates and drivers since it wont be supported too much longer if it is now.

---

### Post by ut40755 on 2010-04-04
im pretty much resorting to just trying various data restore programs.  so far ntfsundelete came up with nothing important looking, and because of the size of the drive, photorec wouldnt work (it apparently needs A LOT of space to work and restores almost everything).

any other ideas?  im doing an error check on the disk now, hoping that because it was deleted in linux it might catch it as an error.

does windows repair overwrite anything or just look for missing data?  i dont want it to screw up all the boot menus.

---

