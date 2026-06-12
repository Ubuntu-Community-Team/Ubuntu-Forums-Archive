---
title: "Had it with wubi, question about real dual boot"
date: 2012-01-28
forum: General Help
---

### Post by coldjeanz on 2012-01-28
So wubi has crashed three times in the past week and I had to hard reboot each time. So I'm done with it and want to do a real dual boot with Windows 7.

Do I have to uninstall wubi before I do this though? Also I don't think I have any partitions already made for Ubuntu and I'm not sure how to do it even after reading some FAQs. How can I go about doing this in the safest way possible? 

I've read you can move your Wubi data but it doesn't look that easy and I don't really have anything important that I couldn't just reinstall so I don't mind.

---

### Post by paulie-m on 2012-01-28
> **coldjeanz said:**
> So wubi has crashed three times in the past week and I had to hard reboot each time. So I'm done with it and want to do a real dual boot with Windows 7.

Do I have to uninstall wubi before I do this though? Also I don't think I have any partitions already made for Ubuntu and I'm not sure how to do it even after reading some FAQs. How can I go about doing this in the safest way possible? 

I've read you can move your Wubi data but it doesn't look that easy and I don't really have anything important that I couldn't just reinstall so I don't mind.
When I did this i booted from a DVD copy of xubuntu that came with linux user magazine. i was a bit unsure at first because i didn't really know about partitioning hdd and all that stuff but when the disc booted it walked me through step by step, asking how much of the drive i wanted for linux,and leaving the windows stuff alone.i don't know if this is the same if you download an image to CD/DVD but i suspect maybe not.back issues of mag are availble.hope this helps.

---

### Post by Frogs Hair on 2012-01-28
If are committed to a dual boot backup your data to a removable device , remove the Wubi installation , and proceed  from there . Wubi uses the windows boot loader and I would remove it to avoid any possible problems . [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by coldjeanz on 2012-01-28
I know that the Ubuntu install CD has a built in partition slider thing but I've been advised not to use this if I am on Windows 7. Is there any truth to that? It looks a lot easier than having to make a partition myself but maybe not...

---

### Post by Mark Phelps on 2012-01-29
> **coldjeanz said:**
> I know that the Ubuntu install CD has a built in partition slider thing but I've been advised not to use this if I am on Windows 7. Is there any truth to that? 

Unfortunateley -- YES.  Win7 is very finicky about changes being made to its filesystem from "outside" -- which can result in the filesystem being corrupted, and Win7 being unable to boot anymore.

There is a safer approach using Win7 directly, but first, you need to open the Win7 Disk Management utility and confirm that you do NOT already have four partitions on your drive.  IF you do, do NOT try to force the creation of another partition.  Instead, you will be faced with having to do the following:
1) Remove an existing partition
2) Shrink down Win7 using the Disk Management utility
3) Use the "something else" option in the Ubuntu installer to do manual partitioning.

Also, if you are determined to do a dual-boot install, then BEFORE you do that, after you have shrunk the Win7 partition, do the following:
1) Boot into Win7 a couple of times to allow the filesystem to make any needed adjustments
2) Download and install the FREE version of Macrium Reflect (MR)
3) Use MR to make an image backup of your Win7 install to an external drive
4) Use the MR feature to create and burn a Linux Boot CD
5) Use the Win7 Backup feature to create and burn a Win7 Repair CD.

NOW -- you have the ability to both, restore your Win7 install (should you accidentally overwrite it during the Ubuntu intall) and restore your Win7 Boot Loader (should it get corrupted during the Ubuntu install).

---

### Post by coldjeanz on 2012-01-29
This is what my setup looks  like:

[IMG]http://i.imgur.com/ZppPa.jpg[/IMG]

However shrinking has been a problem as it refuses to let me shrink by more than 86000 MB which I don't feel is enough since I want to make Ubuntu my primary OS. I have turned off pagefile and defragged and it still won't give me more space.

---

### Post by Mark Phelps on 2012-01-29
86000 MB is nearly 86GB -- MORE than enough room for any Linux distro.

You can get around the shrinkage limitation by avoiding the use of MS Windows tools to do the shrinkage -- but you do so at the risk of corrupting the filesystem.

You can't have it both ways -- ALL the shrinkage you want, coupled with no risk of filesystem corruption.

---

### Post by coldjeanz on 2012-01-29
I just went and shrunk it to about 80. Got tired of waiting. So yeah I still have access to my Windows drive so that's nice.

---

