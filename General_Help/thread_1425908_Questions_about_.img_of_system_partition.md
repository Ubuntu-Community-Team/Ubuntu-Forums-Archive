---
title: "Questions about .img of system partition"
date: 2010-03-09
forum: General Help
---

### Post by Gegenzeit on 2010-03-09
Hi,

After my switch to Linux I fell in a kind of 'configuring freenzy' - now, after I had my obligatory new-to-Linux-complete-system-crash and have reconfigured eyerything, I made an image of my Linux partition. My hope is that I can restore everything exactly as it is now, if (or when) I ruin my system again. 

I use Ubuntu 9.1 on a dual boot with Windows. Windows is /sda1, Linux /sda6. I have the image stored on an usb-backup-device. I used a gnomezilla-live-CD to make the image.

That's the situation! To the questions:

- How can I make sure the image will work? Is there anything like a md5sum, or...something?

- What happens, if I use the image I made on another partition - let's say sda1. 

Thanks for any advice/explanation!

Jörg

---

### Post by ibuclaw on 2010-03-09
> **Gegenzeit said:**
> 
- How can I make sure the image will work? Is there anything like a md5sum, or...something?

There is a saying that goes: "Don't just backup, backup and test."

> **Gegenzeit said:**
> 
- What happens, if I use the image I made on another partition - let's say sda1. 


1) You are going to have to update /etc/fstab so the new partition UUIDs/locations are correct.
2) You are going to have to update grub configuration to reflect the new boot device.

Regards
Iain

---

### Post by Gegenzeit on 2010-03-09
> **ibuclaw said:**
> There is a saying that goes: "Don't just backup, backup and test."

But how do I test it? ;)

> **ibuclaw said:**
>  

1) You are going to have to update /etc/fstab so the new partition UUIDs/locations are correct.
  
2) You are going to have to update grub configuration to reflect the new boot device.

to 1) I know (vaguely) what the fstab is, because I had to play around with it as I mounted my drives. I even know what the UUIDs are and how to find out which drive has which UUID, but to update the fstab so that UUIDs are correct might be beyond me right now ;) This means: Do you know where to learn more about it? A guide would be best ;)

to 2) The only thing about grub that I know is that it manages the boot procedure. I once read about a tool to do stuff with grub - but I forgot it (the name & the stuff). Same question: Where to learn more? 


Thanks

Jörg

---

### Post by Gegenzeit on 2010-03-10
to 1) I found the tool I forgot the name of: Super Grub Disk
It repairs the GRUB - i.e. when windows was installed/repaired.
 
Anyone knows whether this would work for my purpose (install the img of my linux partition on another partition than the one it is on now). 
 
to 2) Up to now I've had no chance to do research on my own. Any help would be great.
 
 
 
What I want do:
 
a) Make four partitions in this order: Windows (75 GB, NFTS), Free space for games (300 GB, NFTS), Linux (75GB, Etx4), Linux-SWAP (About 8GB, Ext4), DATA (about 800 GB, Ext4)
 
c) Install Win7
 
d) Install the img of my current Linux partition on the new Linux partition 
 
e) Make it so that the new UUIDs in fstab are correct (I don't know how to do that)
 
f) Run Super Grub Disk and hope it will fix GRUB
 
Tadaaa...everything is perfect and looks presicley the way it does now. Right?

---

