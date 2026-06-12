---
title: "Is it possible to move an extended partition"
date: 2011-07-06
forum: General Help
---

### Post by westie457 on 2011-07-06
Hello to all.

Attached is a screenshot of the current state of my hard-drive. The fact that there are mounted partitions can be ignored as any work to be done will be done from a LiveCD.

The question is Can the extended partition - SDA4 which contains SDA5 (Maverick Meercat) and SDA6 (swap) - be moved to occupy space at the end of the drive somewhere within the unallocated partition so I can then extend SDA3 to take all of the remaining space?

At the moment using Gparted all I can do with the free space is create another partition.

SDA1 through to SDA6 is a copy of the original hard-drive.

The copying was done using Paragon Partition Manager (a Windows program). This caused all sorts of problems Grub, and was a PITA to sort out. The program installed its own version of the MBR which had to be sorted with a Windows 7 install disk and then I had to sort the Grub problems after. The laptop is working now as I am using it to post this.

Thank you in advance for any help and advice.

---

### Post by stlsaint on 2011-07-06
As far as my knowledge goes there is no way to move an extended partition without deleting it first. Is this a option for you?

---

### Post by westie457 on 2011-07-06
> **stlsaint said:**
> As far as my knowledge goes there is no way to move an extended partition without deleting it first. Is this a option for you?

It could be as there is nothing important in the ext4 partition and everything else is backed up. As long as I do not stuff the Windows partition. 3 days of installing updates and programs and about 3000 reboots is not a good proposition. :lolflag:

---

### Post by CatKiller on 2011-07-06
> **westie457 said:**
> The question is Can the extended partition - SDA4 which contains SDA5 (Maverick Meercat) and SDA6 (swap) - be moved to occupy space at the end of the drive somewhere within the unallocated partition so I can then extend SDA3 to take all of the remaining space?

You should be able to. Use Resize/Move to move the right-hand end to the end of the unallocated space, then move the partitions inside to the end of the (now much larger) extended partition, and then finally move the left-hand end of the extended partition to shrink the partition to the size of the partitions inside it. Then you can extend SDA3.

You'll need to turn swap off before you can move your swap partition.

---

### Post by stlsaint on 2011-07-06
Some quick google searches will give you more a specified guide on exactly what you want to do as long as you back up your data and be willing to delete the partition.

---

### Post by oldfred on 2011-07-06
Just extend the right side of the extended partition all the way to the end of the drive. You could then move the swap & / if you want. Move may take a very long time, so do not interrupt. A move should not change UUIDs so it still should boot. But be prepared to install grub2's boot loader just in case. 

But I would suggest a separate /home for all you Ubuntu data and a shared NTFS for any data you want to share between windows and Ubuntu until you convert to Ubuntu. I have used my shared since I first started with Ubuntu, now rarely boot XP, but still have my profiles for Firefox & Thunderbird in my shared NTFS partition.

---

### Post by CatKiller on 2011-07-06
> **oldfred said:**
> A move should not change UUIDs so it still should boot.

Actually, that's a good point. When I last did a similar thing, the UUID of my swap partition changed. There's no reason why it should have, but it did. Probably worth checking afterwards so that you still have swap. It's just amending the /etc/fstab entry with the new number to fix it.

---

### Post by westie457 on 2011-07-07
Progress is being made see attached screenshot.

What I have done so far is 

1, Boot into a LiveCD and run Gparted.

2, Turn off the Swap so nothing is mounted.

From here things started to get awkward but with a bit of patience I got to how things are in the pic.

3, Selected sda4 and extended it to fill all the remaining space. Clicked on apply and again on continue.

4, Selected sda6 and moved it all the way to the end. Repeated the last sentence of part 3.

5, Selected sda5 and did the preceding instructions.

 I am now doing things that are not in the screenshot

6, Selected sda4 and moved it all the way to the right. Clicked yada yada.
   Got a warning about 'start being in the wrong place - the start of sda4 was after and not before the start of sda5.
   Tried again leaving some space between the two, this worked. 

7, Went back to sda5 and resized it to fill the remaining space in sda4. See new screenshot.

  All that is left for me to do now is wait until I can resize sda3. 

  The idea of a separate /home partition will happen on the next clean install, probably the next LTS.

  After all this I expect Grub will need to be updated.

Assuming a SGD2 disc will find and allow me to boot the current installation in a terminal I will be running ```
sudo update-grub
``` or any variation that works.
Or is the best way to update Grub going to be from the LiveCD?

Advice on that will be appreciated. 

Thank you

---

### Post by CatKiller on 2011-07-07
> **westie457 said:**
> After all this I expect Grub will need to be updated.
I wouldn't expect so. I've only ever had UUIDs change on me with swap partitions.

Looks like you're getting there.

---

### Post by westie457 on 2011-07-07
Update.

All partitioning work is now complete (see pic). Swap has been turned on.

Now for the moment of truth. going to reboot.

---

### Post by westie457 on 2011-07-07
Update.

YAY it works. The bonus was there was no work to be done to Grub.
Swap was found as well.

Thanks to all who replied.

Hope this will be of help to others wanting to migrate to a different hard drive

---

### Post by CatKiller on 2011-07-07
> **westie457 said:**
> update.

Yay it works. The bonus was there was no work to be done to grub.
Swap was found as well.

Yay! \\:D/

---

