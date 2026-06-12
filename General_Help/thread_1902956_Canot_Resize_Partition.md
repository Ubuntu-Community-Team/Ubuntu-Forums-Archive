---
title: "Canot Resize Partition"
date: 2012-01-01
forum: General Help
---

### Post by linux_noobq2m on 2012-01-01
This is my first time using Linux and Ubuntu, so try to bear with my ignorance.

I installed Ubuntu using Wubi installer for windows.
While installing, I chose the installation size to be 1GB.
My ubuntu version is 11.10
I had vista running previously, and now its dual boot.
Vista was on 110 GB hard disk. I partitioned that using disk management in windows to make a 30GB partition for ubuntu.

So, the ubuntu is on 30GB partition. But, when I try to copy something more than 1 GB to the home/Documents folder, it says there is no enough space. When I check properties of home folder, it shows only 426.8MB of free space, and 556MB used space.

Now, I need to increase the size. Cna someone tell me WHY do I have to increase size even when there is 30GB available?

Next, when I restart my computer after suspending it, an error message of "low Swap memory" shows up. Now, I found one way to add swap partition was using gparted [here]("https://help.ubuntu.com/community/SwapFaq"). I downloaded Gparted, but after opening it, I cannot use the resize option. Its greyed / I cannot click on it to choose it.

Sorry for not posting a screnshot, coz I am still trying to figure out how to do that (prt sc not working...another issue :S)

Thanks :D

btw, I am using HP Mini 2133 netbook...everything else (wifi/bt/mic/speakers/webcam) working fine.

---

### Post by grahammechanical on 2012-01-01
You are confusing me or perhaps you, yourself are confused.

It is customary when we partition a hard disk to make space for a Ubuntu partition to actually install Ubuntu into that partition.

By using the Wubi method to install Ubuntu you have not actually installed Ubuntu into the 30GB partition that you re-sized the Vista partition to create. What you have done is install Ubuntu as a kind of Windows program in a folder in your Vista partition.

It is my guess that you limited a data folder (was it called a virtual disk?) inside the Ubuntu folder to 1GB and that folder is now almost 50% full.

Here is a link that might help you:

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

Regards.

---

### Post by coffeecat on 2012-01-01
> **linux_noobq2m said:**
> Cna someone tell me WHY do I have to increase size even when there is 30GB available?


This *may* have something to do with it:

> **linux_noobq2m said:**
> While installing, I chose the installation size to be 1GB.

With wubi, it doesn't matter what the size of the partition is that it is installed to. Wubi itself is installed to a virtual partition contained within a single file in the Windows filesystem. But having said that, it is impossible to install Ubuntu within 1GB, so let's do some investigation.

Boot up Ubuntu, open a terminal, run these three commands and post the output:

```

df -h
sudo fdisk -lu
sudo blkid
```

Sorry to throw terminal commands at you for your first thread, but they really are the most efficient way of getting useful information. The output will be lengthy, so highlight it with the mouse, right-click -> copy and then paste it into your post. After the second command you will be prompted for your password. Don't be concerned if it appears not to be going in. Just type the password - it is being recognised by the system.

When you post the output, post it between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

### Post by linux_noobq2m on 2012-01-01
@Grahammechanical

Thanks for the Wubi Guide link! I think that might solve my problem (first increase virtual size, and then increase swap memory)

I dont think it was called virtual disk. As given in the image on [this]("http://www.ubuntu.com/download/ubuntu/windows-installer") page, I chose the installation size to be 1GB. But again, that might mean virtual disk size.

@coffeecat

first off, how do I reply to a selected portion of the post?

ANd, thanks for the reply. Here's the code after each instruction:

df -h

```
[CODE]Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            4.5G  4.2G  375M  92% /
udev                  874M  4.0K  874M   1% /dev
tmpfs                 352M  844K  352M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  880M  1.5M  879M   1% /run/shm
/dev/sda2              30G  4.8G   26G  16% /host
```

sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4e7ec0fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   171524087    85761020    7  HPFS/NTFS/exFAT
/dev/sda2       171524096   234436607    31456256    7  HPFS/NTFS/exFAT[/CODE]

sudo blkid

```
/dev/loop0: UUID="6d230e1c-6ec9-4931-9e64-bf6c0a002790" TYPE="ext3" 
/dev/sda1: UUID="6612F8D112F8A769" TYPE="ntfs" 
/dev/sda2: LABEL="Locsal Disk" UUID="E82EFD172EFCE00C" TYPE="ntfs" 
```

@both of you:

Will the functioning of ubuntu will be any different (performance wise) if I migrate wubi instal to partition as shown [here]("http://ubuntuforums.org/showthread.php?t=1519354")? After shrinking 30GB partition to 28GB and making the 2GB as swap partition? 

I really want performance to improve, because the main reason I changed from Vista to Ubuntu was better performance of ubuntu. I checked, and it seems Xubuntu is faster than normal ubuntu. But, its kind of complicated to install it. So any help with how to increase performance with this would be great.

---

### Post by coffeecat on 2012-01-01
> **linux_noobq2m said:**
> @coffeecat

first off, how do I reply to a selected portion of the post?

Click on the quote button, and then edit the quoted post so that only the part you want appears. If you copy the "QUOTE=poster's_name" bit and ensure that a quoted fragment is enclosed in [noparse]>  and [/noparse] tags, you can get this effect:

> **linux_noobq2m said:**
> 
I dont think it was called virtual disk. As given in the image on [this]("http://www.ubuntu.com/download/ubuntu/windows-installer") page, I chose the installation size to be 1GB. But again, that might mean virtual disk size.

The virtual disk or virtual partition is the root.disk file, often C:\ubuntu\disks\root.disk, but it can be on D: or E: or whatever. The file root.disk is a file in the Windows NTFS filesystem, but it contains an ext2 (Linux) filesystem within itself for the Ubuntu system.

> **linux_noobq2m said:**
> Will the functioning of ubuntu will be any different (performance wise) if I migrate wubi instal to partition as shown [here]("http://ubuntuforums.org/showthread.php?t=1519354")? After shrinking 30GB partition to 28GB and making the 2GB as swap partition? 

So long as the migration goes successfully, you will see a significant improvement in performance. Running Ubuntu natively in a Linux fileystem is more efficient than running it in a Linux fileystem contained within a file that is itself in a Windows filesystem.  

> **linux_noobq2m said:**
> 
df -h

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            [COLOR="Red"]4.5G[/COLOR]  4.2G  375M  92% /
udev                  874M  4.0K  874M   1% /dev
tmpfs                 352M  844K  352M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  880M  1.5M  879M   1% /run/shm
/dev/sda2              [COLOR="Red"]30G[/COLOR]  4.8G   26G  16% /host
```

I've highlighted the significant bits, but the fdisk and blkid outputs were useful too. My guess is that sda2, the 30GB partition, is your D: or E: partition. Your root virtual partition is only 4.5GB and nearly full. That is too small. I can't see anything that relates to your 1GB, but that's moot. You need to enlarge the root.disk or migrate it to a larger partition as you intend.

Good luck with that! :)

---

### Post by linux_noobq2m on 2012-01-01
Thanks for the info!I guess I will migrate. 

But, another problem occured when I tried to increase swap size using instructions on [this]("rename file using terminal ubuntu") page. When I restarted the computer after suspending, it says Swap Loader Not Found. So, I tried deleting the swap.disk file and renaming the swap.disk.bak to swap.disk. I could not delete the file even after logging in as root through terminal(sudo su and then password) and trying to delete through terminal(cd /host/ubuntu/disks and then rm swap.disk). Both the times, it gave error: Operation not permitted.

Should I make this as new post? or continue posting here?

Thanks again for the quick replies!

---

### Post by linux_noobq2m on 2012-01-01
And, can you please explain what do all those filesystems mean / what are their functions / why are there so many of them?

Thaks again :D

---

### Post by coffeecat on 2012-01-01
> **linux_noobq2m said:**
> 
But, another problem occured when I tried to increase swap size using instructions on [this]("rename file using terminal ubuntu") page. When I restarted the computer after suspending, it says Swap Loader Not Found. So, I tried deleting the swap.disk file and renaming the swap.disk.bak to swap.disk. I could not delete the file even after logging in as root through terminal(sudo su and then password) and trying to delete through terminal(cd /host/ubuntu/disks and then rm swap.disk). Both the times, it gave error: Operation not permitted.

Try rebooting rather than suspend and restart. Also, if you are trying to delete and rename swap files from within Ubuntu, you need to:

```
sudo swapoff -a
```

... before you do your deleting and renaming. Or, if you've sudo su'd to a root terminal:

```
swapoff -a
```

---

### Post by linux_noobq2m on 2012-01-02
Thanks coffeecat! 

did swapoff -a and restored back the old swap.disk, though it did not solve the problem :( .

---

