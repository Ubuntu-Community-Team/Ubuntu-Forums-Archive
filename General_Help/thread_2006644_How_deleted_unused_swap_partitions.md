---
title: "How deleted unused swap partitions?"
date: 2012-06-19
forum: General Help
---

### Post by kkruecke on 2012-06-19
I believe I have several extra **unused swap partitions**, when I re-installed Ubuntu 11.04 over a LinuxMint installation, which had originally been Ubuntu 11.04.
[LIST=1]
[*]How do I know which of these swap partitions are unused--if any?
[*]How do I go about deleting them?
[*]How do I move the **unallocated** space to the end of the partition?
[/LIST]
This is what gparted shows. /dev/sad1 is Windows Vista:

[IMG]http://www.kurttest.com/gparted.jpg[/IMG]

---

### Post by dino99 on 2012-06-19
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

to remove to unneeded swap partition(s): use gparted from livecd (liveusb)

---

### Post by wilee-nilee on 2012-06-19
Boot a live cd, open gparted, make sure the swaps are unmounted, remove all of them it does not matter at that point which one is being used. I assume you have not hibernated the OS.

Make one at the right end and resize  the partition before it up against it.

The 1mib unallocated before the partition I would not worry about if you resized into it after clearing the space after ward it would take a long time to do so.

---

### Post by drs305 on 2012-06-19
Also please make sure all of the deleted swap partition entries are removed from /etc/fstab.

---

### Post by kkruecke on 2012-06-19
Thanks for the replies.

> Make one at the right end and resize the partition before it up against it.
I'm not sure I follow you when you say, "Make one at the right end". Make one of what. 

Should I first delete /dev/sda5, /dev/sda6, /dev/sda7? It seems, since they are the right-most partions (and don't have the grayish "key" icon to the left) I assume they are unused.

---

### Post by Deepak J on 2012-06-19
Is that mandatory to remove the entry from "fstab".

I mean what happens... if it is not removed...

---

### Post by wilee-nilee on 2012-06-19
> **kkruecke said:**
> I'm not sure I follow you when you say, "Make one at the right end". Make one of what. 

A new swap

> **kkruecke said:**
> Should I first delete /dev/sda5, /dev/sda6, /dev/sda7? It seems, since they are the right-most partions (and don't have the grayish "key" icon to the left) I assume they are unused.

The key means the partition is mounted.

You want to remove all the swaps, as the partition numbers are not consecutive.

So remove all, make a new swap at the end of the HD, and resize the OS up against it.

As suggested by drs305 make sure you only have one swap in fstab.

---

### Post by sudodus on 2012-06-19
From the SwapFaq (referenced in post #2)

> Enabling a (new) swap partition:
In case you do have a swap partition, there are several ways of enabling it. 
Use the following command 
```
sudo nano /etc/fstab
```
Ensure that there is a line link below. This enables swap on boot. 
```
/dev/sdaX       none            swap    sw              0       0
```
I would suggest that you use UUID instead of the device name:
Use ```
sudo blkid
``` to find the UUID of the swap partition! Use it without double-quotes (") in /etc/fstab
```
UUID=[COLOR="Red"]41413fbb-473b-4a54-9a9c-2ef3b93c258x[/COLOR]      none            swap    sw              0       0
``` where the [COLOR="red"]red string[/COLOR] should be substituted with the output for swap UUID of [FONT="Courier New"]sudo blkid[/FONT]

Save the file and reboot the computer.

Use ```
top
``` or the ***System Monitor*** to check that swap is actually used (and that it is the correct size).

---

### Post by kkruecke on 2012-06-19
There is only one swap entry in /etc/fstab.

---

### Post by wilee-nilee on 2012-06-19
> **kkruecke said:**
> There is only one swap entry in /etc/fstab.

Once you are done with the removal, making a new swap and resizing make sure the UUID's are correct.

This command will show you the UUID's
```
sudo blkid
```

---

### Post by wilee-nilee on 2012-06-19
@[sudodus]("http://ubuntuforums.org/member.php?u=1499021")

Bad information, as of now sda8 is the OS and the number will probably change as swaps are removed.

Please be careful on posting when a job is getting taken care of, and using another completely different method, that could confuse IE nano, and is just inaccurate.

No biggie we just want the user to understand and leave fixed. ;)

---

### Post by sudodus on 2012-06-19
> **wilee-nilee said:**
> Bad information, as of now sda8 is the OS and the number will probably change as swaps are removed.

Please be careful on posting when a job is getting taken care of, and using another completely different method, that could confuse IE nano, and is just inaccurate.
Sorry, I did not intend to confuse, I just quoted from the link provided by *dino99*, and suggested using UUID instead. I won't interfere again in this thread.

---

### Post by kkruecke on 2012-06-19
Thanks for the replies!

I booted the 12.04 Live CD, and I ran gparted. I now have only one linux-swap partition! And I resized the ext4 partition to included the unallocated space.

However, I still have somethings that are confusing me:

The linux-swap partition that I created is named "New Partition #1", and it has no UUID. What should I do?

Why, when I open up a Terminal window, and does "sudo fdisk -l", show the old partition information of
isk identifier: 0x1549f232

 ```
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   310713164   155356551    7  HPFS/NTFS/exFAT
/dev/sda2       310714366   625137344   157211489+   5  Extended
/dev/sda5       613008333   625137344     6064506   82  Linux swap / Solaris
/dev/sda6       604624896   613007359     4191232   82  Linux swap / Solaris
/dev/sda7       596240384   604622847     4191232   82  Linux swap / Solaris
/dev/sda8       310716416   587851775   138567680   83  Linux
/dev/sda9       587853824   596236287     4191232   82  Linux swap / Solaris
```

and not what I see in gparted, which is 
```
  Partition      File System  Label      Size         Used
 /dev/sda1       nfts          HP    148.16 Gib     73.65 Gib
 /dev/sda2       extended            149.93 Gib       --
 unallocated     unallocated           1.00  MiB      --  
 /dev/sda5       ext4                144.93 Gib      12.44 Gib
 New Parition #1 linux-swap            5.0  Gib       0.00 B 
 unallocated     unallocated           2.49 Mib       --  

```

What do I need to do?

---

### Post by kkruecke on 2012-06-19
Removed double post.

---

### Post by wilee-nilee on 2012-06-19
Post gparted again.

When you post code also include the command in the code area  please.

To show UUID use.
```
sudo blkid
```

---

### Post by kkruecke on 2012-06-19
I had forgotten to apply the gparted changes. But after I applied the gparted changes, I couldn't boot. I got the "Grub Rescue" prompt, so I booted using a Boot Repair CD and ran the "recommended fixes", which worked.  Here is the blkid output:
```
/dev/sda1: LABEL="HP" UUID="FC4CD6334CD5E902" TYPE="ntfs" 
/dev/sda5: UUID="d3a56e14-dc40-4e02-85d4-490847dc0614" TYPE="ext4" 
/dev/sda6: UUID="b71eeab3-4124-49aa-9f3c-eb6c60f12691" TYPE="swap" 

```

 Here is the new gparted output:
[IMG]http://www.kurttest.com/gparted2.jpg[/IMG]

**Thanks for all the help!**

---

### Post by wilee-nilee on 2012-06-19
Hehe it happens, now just open the fstab, and put the correct UUID's in for the OS and swap, you can mount the swap from gparted.

So for future refrence you could have set up the fstab from the live cd so you would have booted.
```
gksudo nautilus
```On the live cd with the OS mounted would have given you read and write to fsatb.

---

