---
title: "Ubuntu not mounting my swap partition"
date: 2011-05-11
forum: General Help
---

### Post by chrisbay90 on 2011-05-11
Hello all,

Ubuntu has been complaining about swap not being ready during boot. The  swap partition was showing up un-known in gparted. I booted off CD,  reformatted it to swap. Error message gone but system monitor >  resources shows my swap size to be 86GB (the exact size of my shared  NTFS volume). gparted shows the swap partition as not 'swapped on'

I am running Ubuntu 11.04 along side Windows 7 (as well as my factory restore partition) and an NTFS shared partition.

My partition structure in order of location on disc. Screen shot below to help.
sda1-2 Windows 7
sda4, extended partition
--sda6 Ubuntu
--sda7 swap
--sda5 NTFS shared partition
sda3 Factory restore image

Any idea's guys and girls?

---

### Post by chrisbay90 on 2011-05-11
Im worried that this may zap my Data partition if it tries to write anything to swap. Any idea's?

---

### Post by ~Plue on 2011-05-11
Compare the UUID/device label of the current swap partition with the relevant line in fstab and see if they are the same.
```
sudo blkid -c /dev/null
cat /etc/fstab
```

---

### Post by chrisbay90 on 2011-05-11
> **~Plue said:**
> Compare the UUID/device label of the current swap partition with the relevant line in fstab and see if they are the same.
```
sudo blkid -c /dev/null
cat /etc/fstab
```

Thank you for your reply. Very much appreciated.

```
$ sudo blkid -c /dev/null
/dev/sda1: LABEL="System" UUID="0ADEDACCDEDAAEE7" TYPE="ntfs" 
/dev/sda2: LABEL="S3A9917D003" UUID="388600648600254A" TYPE="ntfs" 
/dev/sda3: LABEL="HDDRECOVERY" UUID="C4C81A54C81A4558" TYPE="ntfs" 
/dev/sda5: LABEL="Data" UUID="1DD2108177B20F39" TYPE="ntfs" 
/dev/sda6: UUID="46e8132c-6bb7-4ccd-bb7c-de7ecfc835e2" TYPE="ext4" 
/dev/sda7: TYPE="swap" 
/dev/mapper/cryptswap1: UUID="0d21657e-f202-49ce-8937-43c3e819714a" TYPE="swap" 

```
If I am reading this correctly, my swap partion has neither a UUID or a label. 

```
$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=46e8132c-6bb7-4ccd-bb7c-de7ecfc835e2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=77edb938-a210-464d-840f-934cab29a7ad none            swap    sw              0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```
Again, if I am reading this correctly. No partition is being told mount as swap due to the # comment.

---

### Post by VanR on 2011-05-11
Could be because I read 5 partitions on that hard drive and you are only allowed 4. Or am I reading it wrong?

---

### Post by plucky on 2011-05-11
> **VanR said:**
> Could be because I read 5 partitions on that hard drive and you are only allowed 4. Or am I reading it wrong?

That is because one of the partitions is an extended partition and you can have many logical partitions within the extended partition.You are only allowed 4 primary partitions.The extended partition counts as 1 primary partition.

The Op still has only 4 primary partitions.

---

### Post by chrisbay90 on 2011-05-11
> **VanR said:**
> Could be because I read 5 partitions on that hard drive and you are only allowed 4. Or am I reading it wrong?

There are 7 partitions. 4 primary (including the extended partition) and 3 partitions inside the extended partition. The image on this post should help explain.

---

### Post by cbowman57 on 2011-05-11
> **VanR said:**
> Could be because I read 5 partitions on that hard drive and you are only allowed 4. Or am I reading it wrong?

Don't tell my system that, I've got 15 partitions on a single drive. :)

Getting back to the original post.  Apparently something created some type of encrypted swap partition/file.  Since I haven't seen that entry before this is where my assistance ends.  I'm sure there is a fix, I just don't know what it is.

---

### Post by garvinrick4 on 2011-05-11
> # / was on /dev/sda7 during installation UUID=46e8132c-6bb7-4ccd-bb7c-de7ecfc835e2 /               ext4    errors=remount-ro 0       1 
# swap was on /dev/sda5 during installation #UUID=77edb938-a210-464d-840f-934cab29a7ad none            swap    sw  Something strange here /on sda7
and swap on sda5 during installation.

Now they have switched and sda6 partition been thrown in the mix as /:
sda5 now ntfs data:and sda7 is swap: HMMM something looks funny here: UUID's and sda#'s got screwed up when they were changed maybe. Mess though anyway.

Maybe you should back up your sda5 and /home onto a usb backup drive
if not already:
Reinstall with new partition scheme.
#got plenty of Ram do you really need a swap at all.

---

### Post by chrisbay90 on 2011-05-11
> **garvinrick4 said:**
> Something strange here /on sda7
and swap on sda5 during installation.
Now they have switched and sda6 data partition been thrown in the middle:

Maybe you should back up your sda6 and /home onto a usb backup drive
if not already:
Reinstall with new partition scheme.
#got plenty of Ram do you really need a swap at all.

When disk space is so cheap why not? Although my main concern is not the lack of swap, but the potential that sda6 seems like its mounted as swap and may be zaped by linux. I do a fair bit of VM work on this machine, so swapping definatly occurs and linux doesn't handle out-of-memory gracefully.

I will consider that. Had a few drama's latlet and reinstalled twice this week after a failed upgrade. I think the partition number changes came about after i deleted/recreated swap today. Had to repair grub as a result.

---

### Post by chrisbay90 on 2011-05-11
Okay so I deleted the swap partition and created a new one. It now has a label and UUID.

partition table now reads
```
$ sudo blkid -c /dev/null
/dev/sda1: LABEL="System" UUID="0ADEDACCDEDAAEE7" TYPE="ntfs" 
/dev/sda2: LABEL="S3A9917D003" UUID="388600648600254A" TYPE="ntfs" 
/dev/sda3: LABEL="HDDRECOVERY" UUID="C4C81A54C81A4558" TYPE="ntfs" 
/dev/sda5: LABEL="Data" UUID="1DD2108177B20F39" TYPE="ntfs" 
/dev/sda6: UUID="46e8132c-6bb7-4ccd-bb7c-de7ecfc835e2" TYPE="ext4" 
/dev/sda7: LABEL="swapx" UUID="4570ccf9-3f82-4eca-bcdd-e83b7d04fa23" TYPE="swap" 
/dev/mapper/cryptswap1: UUID="0d21657e-f202-49ce-8937-43c3e819714a" TYPE="swap" 

```

So it should just be a matter entering this new UUID into fstab. Anyone kind enought to help me with that?

Also while I have you. I would like to put links to some information threads i have created in my sig. Silly question, i can't find where to edit my sig?
[http://ubuntuforums.org/showthread.php?t=1755128](http://ubuntuforums.org/showthread.php?t=1755128)
[http://ubuntuforums.org/showthread.php?t=1589285](http://ubuntuforums.org/showthread.php?t=1589285)

---

### Post by vanadium on 2011-05-11
You now have this in /etc/fstab:
```

#UUID=77edb938-a210-464d-840f-934cab29a7ad none            swap    sw              0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```

and you would need to change it to
```

UUID=4570ccf9-3f82-4eca-bcdd-e83b7d04fa23 none            swap    sw              0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /dev/mapper/cryptswap1 none swap sw 0 0

```
(line 1: remove comment sign and update UUID, line 3: include comment sign)

Check wether all is good with the command
```

sudo mount -a

```
There should be no output. If that is the case, you should see your swap in the output of
```

cat /proc/swaps

```

---

### Post by chrisbay90 on 2011-05-11
Thanks vanadium. Seems so simple now. Except

```

# cat /proc/swaps 
Filename                Type        Size    Used    Priority
/dev/dm-0                               partition    90194940    0    -1
```

is not silent

---

### Post by vanadium on 2011-05-11
A reboot might be needed anyway.

---

### Post by chrisbay90 on 2011-05-11
> **vanadium said:**
> A reboot might be needed anyway.

That worked perfectly. Thank you vanadium, ~Plue and everyone else for lending your expertise. It was greatly appreciated.

So this signature thing seems like a big secret that I don't know about?

---

### Post by cbowman57 on 2011-05-11
> **chrisbay90 said:**
> Thanks vanadium. Seems so simple now. Except

```

# cat /proc/swaps 
Filename                Type        Size    Used    Priority
/dev/dm-0                               partition    90194940    0    -1
```

is not silent

That shouldn't be silent, **sudo mount -a** should be.

I think you still need to address whatever it was that created the encrypted swap partition/file in the first place but you can safely ignore it I suppose with it commented out.

---

### Post by cbowman57 on 2011-05-11
> **chrisbay90 said:**
> That worked perfectly. Thank you vanadium, ~Plue and everyone else for lending your expertise. It was greatly appreciated.

So this signature thing seems like a big secret that I don't know about?

LOL!  Upper left **User CP** then edit signature. :)

ps.  Since you have plenty of RAM but just want the swap "in case" you need it I always recommend editing sysctl.conf and change swappiness values.  To do so **sudo gedit /etc/sysctl.conf** and at the bottom add **vm.swappiness=1** some recommendations are to change it to 10, etc.. but even 10 let's the system start swapping out earlier than it should IMO.

---

### Post by chrisbay90 on 2011-05-11
> **cbowman57 said:**
> LOL!  Upper left **User CP** then edit signature. :)

ps.  Since you have plenty of RAM but just want the swap "in case" you need it I always recommend editing sysctl.conf and change swappiness values.  To do so **sudo gedit /etc/sysctl.conf** and at the bottom add **vm.swappiness=1** some recommendations are to change it to 10, etc.. but even 10 let's the system start swapping out earlier than it should IMO.

Thanks cbowman57. Your right, i definatly shouldnt turn a blind eye to  these issues. Hmm the swampiness val seems like a good idea. I'll do  something reading and consider changing it.

Haha, how did i miss that.

---

### Post by cbowman57 on 2011-05-11
> **chrisbay90 said:**
> 

Haha, how did i miss that.

Cheers! :cool:

---

