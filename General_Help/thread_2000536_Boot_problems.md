---
title: "Boot problems"
date: 2012-06-09
forum: General Help
---

### Post by alexandrunva on 2012-06-09
Hello,
When trying to delete an ubuntu partition from my hdd ( it was made with paragon from an existing partition) I accidentally rebooted my computer. After that when i tried to start the computer i got the grub rescue terminal, i wasn't able to do much from that but i managed to boot ubuntu from an usb and to run boot-repair. But now when i try to select windows 7 from the boot selection menu i get the error 0xc0000225. Here is the link made bu the boot-repair [http://paste.ubuntu.com/1032584/](http://paste.ubuntu.com/1032584/). 

I have a lot of very important data on my hdd and i would really appreciate your help.

---

### Post by wilee-nilee on 2012-06-09
I am hesitant to say more then use a live cd to get what you need off the HD and reinstall a licensed windows.

There is a indication that some have suggested shows a cracked windows set up, and it is really missing important boot files anyway. 

This is what I mean these are not needed in a legal install, and commonly used in a crack or pirate version.
**/grldr **/bootmgr /Boot/BCD [B]/grldr
[/B]
So I am not saying you did this purposefully or even knew this but in order to help I would have to have you run commands that would remove these anyway, using a recovery or install disc of the windows install.

---

### Post by alexandrunva on 2012-06-09
@[wilee-nilee]("http://ubuntuforums.org/member.php?u=906928") Ok, thank you, but can you tell me how to acces my hdd from an usb live?

@[steverobert]("http://ubuntuforums.org/member.php?u=1670056") i am on a live cd now, but i don't know what to do.

---

### Post by wilee-nilee on 2012-06-09
> **alexandrunva said:**
> @[wilee-nilee]("http://ubuntuforums.org/member.php?u=906928") Ok, thank you, but can you tell me how to acces my hdd from an usb live?

@[steverobert]("http://ubuntuforums.org/member.php?u=1670056") i am on a live cd now, but i don't know what to do.

[steverobert]("http://ubuntuforums.org/member.php?u=1670056") was a spam post.

Boot the live cd, and the partition for the windows install should show in the home left panel, just open it and pull out what you need.

If this was a non legal install that was pirate stuff I would be very careful in that pirate ware can have who knows what inserted in the install in order to steal what they want from you, that is an area you want to be aware of.

Just a warning in that you don't want to carry a rootkit or malware or a virus to a new install.

Once again I am not accusing here just trying to pass on some safety concerns.

---

### Post by alexandrunva on 2012-06-09
I understand and I thank you.
On my home panel I can't see any of my hard drives. I can see only the usb I'm on. Do you know what I can do to see all of my drives?

---

### Post by wilee-nilee on 2012-06-09
> **alexandrunva said:**
> I understand and I thank you.
On my home panel I can't see any of my hard drives. I can see only the usb I'm on. Do you know what I can do to see all of my drives?

Try this command to see if the partition mounts.

```
sudo mount /dev/sda1 /mnt
```

Then go to file in that left panel then mount and see if the windows is there.

---

### Post by alexandrunva on 2012-06-09
> **wilee-nilee said:**
> Try this command to see if the partition mounts.

```
sudo mount /dev/sda1 /mnt
```Then go to file in that left panel then mount and see if the windows is there.

sda1 is already mounted. I tried to mount sda3, sda4 and sda5 but i stiil can't see them on the left panel.

---

### Post by wilee-nilee on 2012-06-09
> **alexandrunva said:**
> sda1 is already mounted. I tried to mount sda3, sda4 and sda5 but i stiil can't see them on the left panel.

If you mount them that way they will not be in the side panel but in files-mount

Open gparted as well and check the partitions with the right click info, the ntfs may be messed up enough that it wont mount.

---

### Post by alexandrunva on 2012-06-09
I don't know if this means I lost all my data but on gparted it says that 560 gb ( the partitions I had on windows) are unallocated. Do you think i can do anything to save the data i had on it?

---

### Post by wilee-nilee on 2012-06-09
> **alexandrunva said:**
> I don't know if this means I lost all my data but on gparted it says that 560 gb ( the partitions I had on windows) are unallocated. Do you think i can do anything to save the data i had on it?

Unallocated can mean that gparted and Ubuntu will not mount the partition.

You are missing key boot files to begin with so something is up.

Some times it is as simple as a bad shutdown and the partition needs a chkdsk to get it showing.

So I can assume here that you have no backup of the info you need.

I have seen no mention of you having a recovery or install disc as well when I have mentioned this.
 
You would need one of these discs to even get started, you might consider going to the windows 7 forum as well, since the problem appears to be windows orientated. Just for more windows help that they may have more expertise in is all.

---

### Post by alexandrunva on 2012-06-09
> **wilee-nilee said:**
> Unallocated can mean that gparted and Ubuntu will not mount the partition.

You are missing key boot files to begin with so something is up.

Some times it is as simple as a bad shutdown and the partition needs a chkdsk to get it showing.

So I can assume here that you have no backup of the info you need.

I have seen no mention of you having a recovery or install disc as well when I have mentioned this.
 
You would need one of these discs to even get started, you might consider going to the windows 7 forum as well, since the problem appears to be windows orientated. Just for more windows help that they may have more expertise in is all.

I don't have the cd. This windows is almost 2 years old so I don't really remeber from which cd/how i installed it. 

I will try the windows 7 forum as well. 

Thank you very much!

---

### Post by wilee-nilee on 2012-06-09
> **alexandrunva said:**
> I don't have the cd. This windows is almost 2 years old so I don't really remeber from which cd/how i installed it. 

I will try the windows 7 forum as well. 

Thank you very much!

No problem, hope this gets fixed in some way. ;)

---

### Post by alexandrunva on 2012-06-10
The problem was solved with CHKDSK from the windows 7 recovery cd.

---

### Post by wilee-nilee on 2012-06-10
> **alexandrunva said:**
> The problem was solved with CHKDSK from the windows 7 recovery cd.

Cool you found a disk. ;)

That makes sense the part of the bootscript I posted originally was the read from the boot partition sda1 which the bootscript could read. The sda2 was not mounting so could not be read I suspect, so the bootfiles that should be there were not showing.

These were the missing files I was looking for that would have been in the sda2 partition.

/Windows/System32/winload.exe

---

