---
title: "Removed Ubuntu: Windows cannot boot now"
date: 2011-10-07
forum: General Help
---

### Post by AT99Scorpion on 2011-10-07
Hi there

I removed Ubuntu, since I never used it due to the fact of compatibility issues, and so anyhow i deleted the Ubuntu Partition, and now I cannot boot to windows anymore... There's a GRUB command like that comes up and I cannot get around it.

Any way to fix this? This pisses me off a lot.

---

### Post by TeoBigusGeekus on 2011-10-07
You need to fix your mbr (master boot record).
If you have a win7 dvd: [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html")
If you have a winxp cd: [http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/]("http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/")

---

### Post by ajgreeny on 2011-10-07
If you have a Windows install CD rather than just a restore CD from the computer maker, you can easily get back to the Windows MBR with a fixmbr command or similar depending on which version of windows you have.

If you don't have a windows CD you can install a Windows equivalent MBR to your sda drive by doing the following from your Ubuntu Live CD.
```
sudo apt-get install lilo
```Ignore the warning then 
```
sudo lilo -M  /dev/sda mbr

```Then you should be able to boot directly into Windows again if all goes well.

---

### Post by AT99Scorpion on 2011-10-07
Yes I know that, but Windows does not come with CD's anymore, so I never made a Installation disk, Is there anyway to bypass the GRUB command line?l\
I
My Windows worked Fine the other night, until I deleted the Ubuntu Partition, and as I cant recall, Ubuntu was the first on the lst of choices to choose from, so the Windows Boot loader will work if I can get passed The Grub Command Line

---

### Post by TeoBigusGeekus on 2011-10-07
[There]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/") you are sunshine.

---

### Post by katastrophenschutzplan on 2011-10-07
Or try this one, if you have no cd.
[http://robert.penz.name/221/mini-howto-restore-windows-mbrbootloader-with-linux/](http://robert.penz.name/221/mini-howto-restore-windows-mbrbootloader-with-linux/)

---

### Post by AT99Scorpion on 2011-10-07
After I put the Ubuntu disk in, a Fedora Boot manager popped up... So Now I realized it's grub from Fedora screwing everything up....

Idk if you guys can fix it since it's different from ubuntu, but i'll use your adive to try and fix it, and thanks for the help.

---

### Post by Mark Phelps on 2011-10-08
Use the link provided by TeoBigusGeekus -- BUT -- do not use anything like "sda1" in the command you enter.  The Windows MBR is written to the drive, not to the first partition.  Using anything like "sda1" is liable to hose up your Windows install.

Instead, the command should have "sda".  This points to the drive, not to a partition.

---

### Post by ajgreeny on 2011-10-09
> **TeoBigusGeekus said:**
> [There]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/") you are sunshine.
Are you sure this method still works?

I understood that ms-sys was no longer available in that way and the lilo method was the alternative way now.

I don't have any windows machines to check this myself, hence the query.

---

### Post by TeoBigusGeekus on 2011-10-09
I don't know; even if it isn't available, he could always download it from
[http://ms-sys.sourceforge.net/]("http://ms-sys.sourceforge.net/")
and compile it himself.

---

### Post by drofart on 2011-10-09
Hi 
  Insert installation disk of windows & goo to repair mode then select command prompr.

Now for windows 7 : bootrec/fixmbr
            then after succesful execution  : bootrec/fixboot . 


win xp  : bootrec/fixmbr


This ll fix u .

---

### Post by ajgreeny on 2011-10-09
> **drofart said:**
> Hi 
  Insert installation disk of windows & goo to repair mode then select command prompr.

Now for windows 7 : bootrec/fixmbr
            then after succesful execution  : bootrec/fixboot . 


win xp  : bootrec/fixmbr


This ll fix u .
It would be very easy if it were possible, but if you had read the OP's posts, you would then know that he has no Windows CD to use, hence the long, drawn out discussion of alternative ways.

---

### Post by mikejonesey on 2011-10-09
stupid microsoft buggers don't even want their users booting windows... 

ms-sys was cool shame it got the shunt, neways the method still works ms-sys is still availible in debs from the east, their internet laws and concers seen a little more lax...

---

