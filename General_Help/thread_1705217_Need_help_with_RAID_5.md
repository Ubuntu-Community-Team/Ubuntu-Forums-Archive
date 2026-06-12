---
title: "Need help with RAID 5"
date: 2011-03-11
forum: General Help
---

### Post by carbon13 on 2011-03-11
OK, this is fairly complicated so I'm going to do my best to explain in detail my current dilemma:

I have a silicon image 3114 controller card that supports RAID 5. I'm trying to set up the RAID 5 Array (4x 1TB) on an old Dell Dimension 4100 Pentium 4 computer (has BIOS A08). I want to install ubuntu 9.10 on the RAID Array and boot from here.

I have created the RAID array on the controller card BIOS. Ubuntu installer sees the array and installs on it. When I try to boot from the controller card (option ROM in the Dell BIOS) it times out and asks for a floppy (floppy isn't even installed...).

I can install the OS onto the IDE drive (20GB) and then see the RAID array as a separate 3TB filesystem. But I would rather have the array as my home folder so I don't have to mess around with mounts and shares every time I reboot.

Anyone have any insight on how I can boot from the RAID ARRAY?

As an aside, I had a similar 2xSATA sil card that I ran a RAID 1 mirror ARRAY on previously and it worked like a charm.

-Carbon13

---

### Post by Hedgehog1 on 2011-03-11
carbon13,

When we setup our big servers, we have learned the hard way never to boot from a raid array.

Our server may boot from a high-speed USB stick physically mounted on the mother-board (it takes a screwdriver to remove it), or a small hard drive (or SSD).

Raid arrays take time to boot, and in nearly all cases need self-check time.

Booting off the 20 gig drive and seeing the raid array as the '/home' directory is a very viable solution.  This would yield you what appears to be one giant 3,020 gig drive.

You can install Ubuntu that way, in fact.

***The Hedge***

:KS

---

### Post by carbon13 on 2011-03-12
OK. This was actually my initial thought as well; but I'm not sure how to boot from the IDE and still have the RAID array as my home folder (and not have to mount and reset shares after every reboot). Can you advise on how to do this?

Thanks for the reply

-Carbon13

---

### Post by carbon13 on 2011-03-12
I can now boot ubuntu 9.10 from the 20G IDE drive.

The fakeraid 5 array is detectable as a filesystem but I have to mount it.

Is there a way I can mount the filesystem at boot so I don't lose the location and shares every reboot?

Appreciate any help. I've been at this for days and I'm almost at the point of trying windows (gack!!)

-Carbon13

---

### Post by carbon13 on 2011-03-12
Progress!!

I followed this post for mounting an internal drive and it seems to work for the fake RAID 5 array on the sil3114 card:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

The only sketchy part is that every time I reboot, the RAID array doesn't appear in the new "storage" folder UNLESS I first open gparted (which scans for devices upon opening). Then all is good and the "storage" file appears as the 3TB array. Wonder if there is anyway to do an equivalent device scan on startup in order for the the array to mount properly??

Otherwise, I think I'm in business. I'm copying over some files and ensuring that all the shares etc. stay in place after a couple of reboots.

-Carbon13

I kinda feel like I'm talking to myself here...anyone have any thoughts...

---

### Post by Hedgehog1 on 2011-03-13
> **carbon13 said:**
> 

The only sketchy part is that every time I reboot, the RAID array doesn't appear in the new "storage" folder UNLESS I first open gparted (which scans for devices upon opening). Then all is good and the "storage" file appears as the 3TB array. Wonder if there is anyway to do an equivalent device scan on startup in order for the the array to mount properly??

...

I kinda feel like I'm talking to myself here...anyone have any thoughts...

carbon13,

To mount the RAID array at boot up, adding it into the /etc/fstab file is your best bet.  Do you know how to do that?

[How Linux makes larger 'file systems' using /etc/fstab]("http://ubuntuforums.org/showthread.php?t=1705788")  (in your case, a RAID ARRAY is presented as a single drive)

***The Hedge***

:KS

p.s. And just what is wrong with talking to yourself...  It keeps and AND my alternate personality sane(ish) :D

---

### Post by carbon13 on 2011-03-14
Hedge - Thanks for the reply (not feeling so crazy talking to myself now...).

Similar to the post in the thread you linked me to, a step-by-step on mounting the array on /etc/fstab would be useful.

Although, I must admit, I'm really hesitant to do anything now that I have it working semi-decently. My wife is ready to kill me since I spent the last week with my head in the guts of an old computer.

Thanks again for the help. 

-Carbon13

---

### Post by Hedgehog1 on 2011-03-15
One must take into account the WAF (**W**ife **A**cceptance **F**actor) when messing about with computers and purchasing large TVs.
 
SOOOOO, when she isn't looking....
 
Create a real directory you can 'mount' with the RAID
```
sudo mkdir /raid5
```
 
Find out the UUID (**U**niversal **U**nique **ID**entifier) of the RAID
 
```
sudo blkid -o value -s UUID
 
965E0E865E0E5EFD
EA561004560FCFED
**f2fd03c5-2835-415c-8448-75473daf624a**
**cb0c7226-150e-45ca-ba5c-2e161dc10f6a**
**4aebc2c6-5984-47e3-b2ea-7fdfaf23343e**
**11111111-2222-3333-4444-555555555555**
5C28DA0E28D9E754
```
 
The BIG ones in are the UUIDs of your Linux Partitions. One of these will be the UUID for your RAID.
 
Next:
```
gksudo gedit /etc/fstab
```
 
The fstab (**F**ile **S**ystem **TAB**le) defines what your file system looks like at boot up.
 
Mine look like this:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda5 during installation
[COLOR=seagreen]UUID=f2fd03c5-2835-415c-8448-75473daf624a  /                 ext4  errors=remount-ro    0  1[/COLOR]  
# swap was on /dev/sda6 during installation
[COLOR=darkorange]UUID=cb0c7226-150e-45ca-ba5c-2e161dc10f6a  none              swap  sw                   0  0[/COLOR]  
# /home partition was /dev/sda7
[COLOR=deepskyblue]UUID=4aebc2c6-5984-47e3-b2ea-7fdfaf23343e  /home             ext4  nodev,nosuid         0  2[/COLOR]
# Automount Windows paritions
[COLOR=darkorchid]UUID=EA561004560FCFED                      /media/Area51     ntfs  defaults             0  0  [/COLOR]
[COLOR=darkorchid]UUID=5C28DA0E28D9E754                      /media/Area52     ntfs  defaults             0  0[/COLOR]
```
 
You can see that I assign my '/home' in its own partition.
 
I also auto mount two Windows partitions (Area51 & Area52).
 
In your case, you will see one more UUID from the **bklid** than is in the **fstab** file. That extra UUID is your RAID.
 
So now we want to 'override' the real '**/raid5**' directory with your RAID 'drive'. We do that by adding one more line to **fstab**:
 
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda5 during installation
[COLOR=seagreen]UUID=f2fd03c5-2835-415c-8448-75473daf624a  /                 ext4  errors=remount-ro    0  1[/COLOR]  
# swap was on /dev/sda6 during installation
[COLOR=darkorange]UUID=cb0c7226-150e-45ca-ba5c-2e161dc10f6a  none              swap  sw                   0  0[/COLOR]  
# My cool RAID drive
[COLOR=red]UUID=11111111-2222-3333-4444-555555555555  **/raid5**            ext4  nodev,nosuid         0  2[/COLOR]
```
 
Save the **fstab** file, and reboot.
 
The **/raid5** directory is now really your RAID.
 
You don't have to call it **/raid5**, just use the same name for the real directory and the entry in **fstab**.
 
***The Hedge***
 
:KS

---

### Post by carbon13 on 2011-03-15
Hedge,

This is great! Thanks for your help.

So one question, how is this different from what I currently have following the instructions here: [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Reason I ask is that I followed the psychocats directions (yes...I have only myself to blame...psychocats?...really?) and now I have a /storage folder in the root of my system drive. Problem is, the computer does not see the raid drive (/storage appears as a component of the 20GB IDE that the system is installed on) unless I open and close gparted; then all is well with the world and /storage has 3TB of space.

So is there something different in your instructions vs. psychocats that would solve this mysterious occurrence every time I reboot?

Thanks,

Carbon13

PS. WAF is currently at orange alert...

---

### Post by Hedgehog1 on 2011-03-16
I had not seen that tutorial.  Thanks for the link.

The difference between the tutorial and my post is small:  The last three options of the line added in /etc/fstab.

mine ended with: **nodev,nosuid  0  2**
cats ended with: **defaults      0  0**

There may be an issue with the raid not being available as quickly as Linux wants to see it.

Also, is the RAID really presenting itself as ext4?  What does gparted say it's format is?  That is the format that fstab needs.

***The Hedge***

:KS

---

### Post by carbon13 on 2011-03-18
So I tried changing the last options over to nodev,nosuid 0 2. No help in recognizing the raid. Gparted does recognize it as ext4.

I kinda think you are right that the raid array isn't available as quickly as Linux wants to see it. Must be used to slow poke windows bootups versus Linux fast booting efficiency!! 

Anyway, I can live with it the way it is. Not really a big deal to have to open and close gparted on reboot (I usually leave it on most of the time anyhow).

Thanks for all the help Hedge!!

-Carbon13

---

