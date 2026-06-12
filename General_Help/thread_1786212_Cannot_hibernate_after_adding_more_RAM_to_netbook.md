---
title: "Cannot hibernate after adding more RAM to netbook"
date: 2011-06-19
forum: General Help
---

### Post by lordofthemoon on 2011-06-19
Hi,
I'm running Ubuntu 10.04 (Lucid) and I recently upgraded the amount of memory in my Acer Aspire One A110 netbook from the default of 512M to 1.5G.  I don't use this netbook very often and only today after I was done with it did I try to put it into hibernation rather than shutting it down and discovered that the option was no longer there.

I googled for a bit and then realised that I didn't have a swap partition.  I don't know if I ever had one or whether I was using a swap file, but I followed [this guide]("https://help.ubuntu.com/community/SwapFaq") to create a swap partition, which I can now see.  I also followed the bit of the guide that talks about making the swap partition work for hibernate, but although I can now see "hibernate" in my power menu, if I select it, the disk thrashes for a bit but nothing happens.

I've tried running
```
sudo /etc/acpi/hibernate.sh
```from the command line in case it gave me any error message, but it doesn't, and neither does just typing
```
pm-hibernate
``` but this doesn't work either.

Any help would be greatly appreciated.

TIA,
Raj.

---

### Post by lordofthemoon on 2011-06-23
*bump*, any ideas here?

---

### Post by i.r.id10t on 2011-06-23
Don't own a laptop, but doesn't hibernating dump RAM into a partition/file to be read back in when "waking up" ?  Check partition sizes (esp your swap partition) as well as amount of free space available ...

---

### Post by akand074 on 2011-06-23
Yeah how much swap space do you have? Hibernating dumps your RAM into swap. If you don't have enough swap space you can run into issues. Open up a partition manager like gparted to find out if you don't know.

---

### Post by lordofthemoon on 2011-06-29
> **i.r.id10t said:**
> Don't own a laptop, but doesn't hibernating dump RAM into a partition/file to be read back in when "waking up" ?  Check partition sizes (esp your swap partition) as well as amount of free space available ...

Sorry for the late reply, I've been away for the past few days.  I've checked my swap partition and it *was* too small (which is odd, because I'm sure I had set it as something a bit larger than my RAM).  I went through the steps in the link in the original post again and now have a swap partition of 2G (I have 1.5G RAM) but although Hibernate shows up in my menu, it still doesn't seem to actually do anything.

Another (possibly) slightly odd thing is that although the swap partition is marked as being active in gparted, its usage level is "---" and when I view /proc/swaps the "Used" column there is 0 as well.

Any other ideas?

Raj.

---

### Post by dcstar on 2011-06-30
> **lordofthemoon said:**
> 
..........
I went through the steps in the link in the original post again and now have a swap partition of 2G (I have 1.5G RAM) but although Hibernate shows up in my menu, it still doesn't seem to actually do anything.
..........

And you did **everything** in the instructions regarding the UUIDs, did you?

---

### Post by grahammechanical on 2011-06-30
My swap usage is zero, as well. But then I am not doing anything memory intensive. I am just reading the forum posts. Swap gets used as a process uses up RAM memory. It is designed to stop the system from freezing up as it tries to do too many things at once. Things that are needed in memory but not at that moment can be filed on the hard disc to allow more urgent tasks the RAM memory they need.

Regards.

---

### Post by lordofthemoon on 2011-07-02
> **dcstar said:**
> And you did **everything** in the instructions regarding the UUIDs, did you?
Yup, modified [FONT=Courier New]/etc/fstab[/FONT], [FONT=Courier New]/etc/default/grub[/FONT], and [FONT=Courier New]/etc/initramfs-tools/conf.d/resume[/FONT] and executed the commands given.

---

