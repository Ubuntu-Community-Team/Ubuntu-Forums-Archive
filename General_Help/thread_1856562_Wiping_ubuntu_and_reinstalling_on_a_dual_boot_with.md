---
title: "Wiping ubuntu and reinstalling on a dual boot with XP"
date: 2011-10-08
forum: General Help
---

### Post by choclo on 2011-10-08
Hello there, i completely fubar'd my ubuntu messing around with things beyond my realm of intellect and i need to wipe it and reinstall. I am wondering if i can just wipe it from the command line or what steps would be necessesary to complete this task.

It's on a dual boot with windows xp and i don't think there'l be too much interference because the hard drive is already partitioned for this. So I just wipe it and reinstall from a live cd right???

Thanks in advance

---

### Post by mike555 on 2011-10-08
after backing up anything you want to save, just take note of Ubuntu partition letters (like sta2) and install new to that partition ,formating as you go ......

---

### Post by stlsaint on 2011-10-08
Yes, the same steps you took to install you will take to wipe. Only difference would come to when you select the partition. Don't let ubiquity set the partitions. Use the manual option and just select the already partitions in place for swap and /home.

---

### Post by WasMeHere on 2011-10-08
Yes :-)

I guess you already have a swap partition, so I suggest that you select manual partitioning, 'advanced', and re-use the linux partition and the swap partition.

Good luck
Olle

---

### Post by viperdvman on 2011-10-08
I second what everyone else said about manually setting your partition. You can just do a clean wipe right from the install. Whatever partition contains your current install, install your new Ubuntu to that. And don't forget to select "Format this partition" so that it wipes it for you before you install... and ONLY that partition.

If you're using the Windows bootloader, you'll have install the bootloader to the same partition as your Ubuntu install. And don't forget to reset your bootloader settings in Windows. However, if you're using GRUB as your bootloader, then just install as you did before and no worries. If Ubuntu is your only OS, then no worries.

---

### Post by choclo on 2011-10-08
Gee that was quick, thanks alot peeps! I'll give it a go and get back to yee if i run into any snags.

---

