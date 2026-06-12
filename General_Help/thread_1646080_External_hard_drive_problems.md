---
title: "External hard drive problems"
date: 2010-12-15
forum: General Help
---

### Post by Ezra Avalon on 2010-12-15
Disclaimer: If I'm not posting this in the right category let me know.

The problem is my hard drive containing UNR won't boot. 

It is a Western Digital 2.5" external hard drive, Simpletech with UNR 1.0.1 loaded as the OS. 
UNR had been going wonky for a while but it was very minor things. I left it on at nights and that never seemed to bother it. One night I left it on and then in the morning I rebooted it but it wouldn't come up. 
BIOS will recognize it, but when I hook the drive up to Windows I can't see it. I tried hooking it up to another computer and it didn't read it and I hooked it up to the same machine with another Linux running and it wouldn't read it. I even put the hard drive directly into the EEE and it still wouldn't boot. It was like it couldn't find anything on the hard drive.
The machine I"m running is an EEEpc 1005HAB with Windows XP.
What do I do? Can I even attempt to recover data? How can I make it be read by an OS?

---

### Post by ajgreeny on 2010-12-15
For a start, you can forget about windows for recovering anything from the disk, as windows is not able to read the linux formatted filesystems such as ext4.

Plug the disk into a ubuntu machine and then use the command ```
sudo fdisk -l
```and it should show you the device named as **/dev/sdb** or something similar.  With luck, it may even mount it for you.  Once we know the device name we can try to see what is wrong, and hopefully mount it and recover your files, at the very least.

---

### Post by Ezra Avalon on 2010-12-15
fdisk -l gave me 
```
Disk /dev/sdb:160.0GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units=cylinders of 16065*512=822580 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a vaild partition table.

```
and it didn't mount it.

---

### Post by ajgreeny on 2010-12-15
In which case I'm lost, I'm afraid.

Other than suggesting you try restoring the partition with **testdisk** on a live CD or USB live version, I can not come up with any answers.

---

### Post by Ezra Avalon on 2010-12-15
Thank you, though.

---

