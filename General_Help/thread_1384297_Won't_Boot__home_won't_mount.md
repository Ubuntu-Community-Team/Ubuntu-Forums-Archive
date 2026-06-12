---
title: "Won't Boot : /home won't mount"
date: 2010-01-18
forum: General Help
---

### Post by JohnMoriarty on 2010-01-18
Help!

Running Ubuntu 9.10 for some months without any problems, but with no obvious trigger it won't boot this afternoon. (I'm not aware of any updates happening this morning, when everything was fine.)

Grub loads fine, and then moves on to the first splash screen, on which I get this message:

```
One or more of the mounts listed in /etc/fstab cannot yet be mounted:
/home: waiting for UUID=ddaded40-ecae-4794-99f7-89f53b6db397
Press ESC to enter a recover shell
```

and it gets stuck; searching around shows lots of people get a similar message but then boot normally; this may have been happening to me in the past but I don't pay much attention to the boot up. 

The recovery console appears to load fine but I haven't a clue what to do with it!

John

---

### Post by john newbuntu on 2010-01-18
Enter the recovery shell and login.  Type "sudo blkid" without quotes.  This will give you the block device ids for every partition.  It appears that the blkid for /home in the file /etc/fstab does not match the one corresponding to the one for home partition.

So edit /etc/fstab (perhaps using vi or nano or any non-gui editor), make the change to the line that starts with UUID corresponding to /home.  Replace only the UUID=xxxx part, where xxxx is that long number.  Save and reboot.

---

### Post by JohnMoriarty on 2010-01-18
John
thank-you for your reply.

(The recovery shell doesn't ask me to login, it just goes straight to a root prompt.)

blkid lists all of my partitions apart from my home drive, which sda3!

This rather paniced me so I booted a "Parted Magic" livecd I had lying around, and GParted shows all of my partitions as they should be, allows me to mount the home partition and all the files are as they should be. From the livecd blkid does list sda3 and gives the same UUID as is already in the fstab file (the one it can't find).

What now?

Thanks
John

---

### Post by michy99 on 2010-01-18
What is the output of```
sudo fdisk -l
```

---

### Post by Xog on 2010-01-18
> **michy99 said:**
> What is the output of```
sudo fdisk -l
```

that's a lowercase L by the way, just to clear any confusion

---

### Post by JohnMoriarty on 2010-01-18
Michy99

thank-you for your reply.

'fdisk -l' results in a complete list of all my partitions, including the sda3 which isn't mounting. Do you need to know more than this, only I'm posting from a different computer, and would have to type the whole lot accross.

John

---

### Post by kseise on 2010-01-18
If you can edit the /etc/fstab, you might want to change the UUID back to the older format of /dev/sda3.  The UUID was causing me a ton of problems with my RAID setups.  I can't remember the exact syntax of the entry though.  But Don't Panic, your data is there.  We just need to link to it.

---

### Post by michy99 on 2010-01-18
It looks like there might be something wrong with the partition table. Try installing testdisk from the live cd (it's in the repositories) and see if it finds a problem. If it does, it can probably fix it.

---

### Post by JohnMoriarty on 2010-01-18
Thank-you everyone.

Following kseise's suggestion I looked up the format for fstab and replaced the UUID=xxx with /dev/sda3 (as the format turns out to be). And the computer now boots fine.

When I get a moment (after catching up everything I should have been doing, I'll check the partition table as michy99 suggests.

Anyone any ideas as to why it should suddenly have just happened?

Thanks again,

John

---

### Post by michy99 on 2010-01-18
Did you add, delete or re-size any partitions lately? Just fishing.

---

### Post by kseise on 2010-01-18
> **JohnMoriarty said:**
> Anyone any ideas as to why it should suddenly have just happened?

Thanks again,

John

I noticed it during my attempts to upgrade from 9.04 to 9.10.  It seems like the new preferred method of identifying disks.  The UUID is supposed to be something of a unique identifier for each disk, so that if you shuffle them around, the computer still boots from the right one.  The only downside, I found after much research, is that the UUID is a calculated thing, and not all systems calculate it the same way.  It is really frustrating with RAID, where each disk has a UUID and the RAID has a third UUID.  It is considered to be helpful, so get used to it, but bookmark this fix just in case.

---

### Post by Irihapeti on 2010-01-18
I had similar problems and discovered that there's a bug in the Karmic kernel that doesn't allow it to handle UUIDs:  /dev/disk/by-uuid doesn't exist in karmic kernels [https://bugs.launchpad.net/ubuntu/karmic/+source/util-linux/+bug/426027](https://bugs.launchpad.net/ubuntu/karmic/+source/util-linux/+bug/426027)

---

### Post by JohnMoriarty on 2010-01-18
Thanks to everyone for getting me back up and running.

I tried the testdisk as michy99 suggested and it didn't come up with anything untoward.

I haven't changed anything with the partitions since I separated /home into its own partition a few months ago (about the same time as I upgraded to Karmic). And I can't imagine what else could have changed either. It does look like it is related to the bug Irihapeti mentions though. 

Now that everything is working blkid lists all the partitions, including the one it wasn't listing earlier (see post #3).

Thanks again

John

---

