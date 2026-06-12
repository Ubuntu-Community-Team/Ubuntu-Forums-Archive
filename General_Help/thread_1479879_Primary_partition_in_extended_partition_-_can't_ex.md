---
title: "Primary partition in extended partition - can't expand"
date: 2010-05-11
forum: General Help
---

### Post by Halfling Rogue on 2010-05-11
I have both Hardy and Lynx on my machine, and recently nuked a Windows partition to make space for my sorely undersized Lynx partition. I'm not too familiar with partitioning, so I want to make sure I'm doing this right before I break anything.

Is there any way at all to extend sda7 into the unallocated space, or is the structuring not going to allow for that? I tried moving/resizing it using Gparted off a live CD, but no go.

[IMG]http://i39.tinypic.com/f2muyp.png[/IMG]

---

### Post by dcstar on 2010-05-11
> **Halfling Rogue said:**
> I have both Hardy and Lynx on my machine, and recently nuked a Windows partition to make space for my sorely undersized Lynx partition -- but Gparted isn't letting me expand it into the free space (and yes, I am using a live disk with root unmounted).


As has been explained multiple times in virtually every thread on changing partitions, you cannot change an Extended Partition with mounted partitions inside it.

Stop using the swap partitions inside the Extended Partition.

---

### Post by Halfling Rogue on 2010-05-11
Sorry! I found a lot of threads on the subject, but it was late at night and I was having trouble comprehending a lot of them (I couldn't figure out how to unmount my swaps), and I didn't want to permanently break anything. So I need to nuke my swaps and that will get rid of the Extended partition? Will they reestablish themselves automatically in the unallocated space or am I going to have to recreate them?

---

### Post by Mark Phelps on 2010-05-11
You're NOT going to be able to mess with the contents of the Extended partition from inside Ubuntu if you're using files contained on the mounted partition.  You will have to boot from the LiveCD and run GParted from there.

Getting rid of your swap partitions will have no effect on the extended partition containing them other than freeing up some space.

And no, they will not be recreated automatically; you will have to manually create a new swap partition.

---

### Post by Halfling Rogue on 2010-05-11
I was using Gparted via the live CD, yes, and it wasn't letting me extend or move sda7 into the unallocated space. So even if I get rid of the swaps, I won't be able to do that? I guess that means my only option is to wipe my current Lynx installation and reinstall it in unallocated space.

---

### Post by srs5694 on 2010-05-11
Fundamentally, you need to do two things to extend /dev/sda7:


[list]
[*]Stop using the swap partitions. This does *not* mean you need to get rid of them; it just means that you need to temporarily turn off swap on your system. I believe you can do this by right-clicking each swap space in GParted and selecting an option to turn it off; or you can type "sudo swapoff -a" in a text-mode shell. Either way, the little key icons should then disappear.
[*]Resize your extended partition (/dev/sda3). Primary partitions exist outside of the extended partition, and logical partitions exist inside the extended partition. When you want to expand a logical partition into space that's not covered by the extended partition, you must first resize the extended partition. Depending on which partitions you want to extend and by how much, though, you might not need to do this.
[/list]


One critical question about your configuration is this: What are your /dev/sda2 and /dev/sda7 partitions? Is one root (/) and the other /home? If you don't know, please boot into Linux and post the output of "df -h" (note the space between "df" and "-h"). This will show us how your system is currently set up and enable us to better advise you about how to proceed.

---

### Post by Halfling Rogue on 2010-05-11
My /dev/sda2 is my Hardy, and my /dev/sda7 is my Lynx. Lynx is root, Hardy is /home.

---

### Post by srs5694 on 2010-05-11
> **Halfling Rogue said:**
> My /dev/sda2 is my Hardy, and my /dev/sda7 is my Lynx. Lynx is root, Hardy is /home.

"Lucid Lynx" and "Hardy Heron" are code-names for different Ubuntu versions (10.04 and 8.04, respectively). Are you saying that you're re-using the 8.04 installation as a /home partition for 10.04? If so, does 8.04 still boot? Do you want to be able to boot either version?

---

### Post by Halfling Rogue on 2010-05-11
Yes. I had 8.04 installed first as a dual boot with my Windows, then I installed 10.04, then I deleted the Windows partition. I would like to boot both 8.04 and 10.04, if only because [my external hard drive won't mount in 10.04.]("http://ubuntuforums.org/showthread.php?t=1479792")

---

### Post by srs5694 on 2010-05-11
OK, so it sounds like you ultimately want to expand both /dev/sda2 and /dev/sda7. There are a lot of ways to do this. I'm going to suggest consolidating your swap space into a single swap partition while you make your other changes. To do so, try this:


[list=1]
[*]Boot your live CD.
[*]Launch a command prompt and type "sudo swapoff -a"; or select your swap partitions in GParted and disable them, as described in my earlier post.
[*]Launch GParted.
[*]Select and delete each of your swap partitions. This will clear up some space [i]after[i] /dev/sda7.
[*]Select /dev/sda7 and expand it to the right. I recommend committing your changes at this point (by clicking the green check mark) just to be sure this much goes smoothly; however, you could put this off for a while if you prefer. It's likely that /dev/sda7 will be renamed to /dev/sda5 at this point, particularly if you commit your changes.
[*]If the expanded /dev/sda7 isn't as large as you'd like it to be, select /dev/sda3 (the extended partition) and expand it to the left by as much as you want to grow /dev/sda7; then select /dev/sda7 and expand it to the left to fill the extra space you've created in /dev/sda3. This operation, when you commit it, is likely to take a while to finish since there may be a lot of moving of files. Moving/expanding partitions to the left like this is also riskier than expanding to the right, so if you think you can live with /dev/sda7 expanded only to the right, you might want to do so. I recommend committing your changes again at this point.
[*]Create a new primary partition, positioned at the *end* of the free space, to be used as Linux swap space. Make it at least as large as your computer's RAM. (You could create it as a logical partition instead of as a primary partition, but this will require expanding the extended partition by a suitable amount and creating the swap space to fill that extra space in the extended partition.)
[*]Select /dev/sda2 and expand it to the right.
[*]Apply your changes by clicking the green check-mark icon.
[*]Mount /dev/sda2 and /dev/sda7 (their partition numbers may have changed by now).
[*]In a text-mode shell, type "sudo blkid /dev/sdan", where "/dev/sdan" is the device ID for the new swap space. (Probably /dev/sda1 or /dev/sda4; or /dev/sda5 if you created it as a logical partition.)
[*]Edit the /etc/fstab files in both of your Linux installations. (Say, /mnt/one/etc/fstab and /mnt/two/etc/fstab, depending on where you mount them.) Locate the entries for the swap partition(s). If an fstab file has multiple swap entries, delete all but one. Change the UUID value to the UUID value revealed by the blkid command.
[*]Reboot.
[/list]


With luck, both your Linux installations will now work. It's conceivable that your boot loader and/or /etc/fstab files will have to be edited and/or GRUB will have to be re-installed. This is most likely if you've got references to partitions by device filename -- that is, to /dev/sda2 or /dev/sda7 rather than to a UUID value. Default Ubuntu installations use UUID values, so this will probably only be the case if you've hand-edited these files in the past. If you do have problems, you should be able to correct them via your live CD.

Best of luck!

---

### Post by Halfling Rogue on 2010-05-12
Well, it seemed to work all right, except now my GRUB is messed up and I have nothing mounted to root, so I can't boot either of them. Using the live CD, I'm getting this:

/etc/fstab:
```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0
```


ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

[IMG]http://i44.tinypic.com/nqqv4m.png[/IMG]

[IMG]http://i41.tinypic.com/30hyl92.png[/IMG]

---

### Post by Halfling Rogue on 2010-05-12
I lost my wireless driver when I edited the partitions, and my tablet was giving me trouble, so I finally decided to just wipe the Lynx partition and start over with a new installation next to the Hardy. Everything works just fine now.

Thanks to everyone for your help!!

---

### Post by srs5694 on 2010-05-12
I know it's too late, but in case anybody else has this problem: I suspect that the /etc/fstab file you posted is from a live CD, not from your main installation. You could probably have gotten it going by selecting an option to boot from the hard disk when using the live CD or by using [Super GRUB Disk.](http://www.supergrubdisk.org) Either way should have gotten the 10.04 installation booted, and from there you could have used grub-install to get the hard disk booted without CD/DVD help.

---

