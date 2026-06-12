---
title: "Installed Ubuntu on Raid 0"
date: 2009-10-22
forum: General Help
---

### Post by DeMus on 2009-10-22
I did it. After having doubts and questions, see [_New installation on 2 disks_]("http://ubuntuforums.org/showthread.php?t=1296259") I decided to go ahead with it.
Yes, I wanted to wait for Karmic but I thought I can practice now on Jaunty so this morning I started the new installation. It went fantastic. No problems whatsoever.

```
NOTE: I did make a back-up of all my files and folders,
including the hidden ones, so I could delete everything form the disks.
```

I used the alternate install CD which uses a text-based installation program instead of a GUI program. Maybe this looks scary, I can tell you it is not. The same questions are being asked, you give the same answers. One difference: instead of pointing the mouse to the NEXT-button you use the TAB-key to get there and then press Enter.

What is the reason to use the alternate CD? Well, more questions are being asked. Questions about settings which are filled in by the normal installation program automatically, but which you can fill in yourself here.
I was especially interested in the questions about the partitioner, since I wanted to use the RAID 0 configuration.

When that part appeared on screen I saw a list of my 2 disks with all the partitions on them. First I deleted all partitions so I had 2 empty disks, 500.1 GB each.
I created a 100MB partition for /boot on sda. This can **NOT** be a part of the RAID. To make sure disk sdb would be the same, I created an sdb1 dummy partition, also 100MB and choose to NOT use it.
Then on sda 2 more partitions, 50GB for / and 450GB for /home. On sdb I did the same.
The sizes for sda2 and sdb2 are added so partition / is now 50 + 50 = 100GB, /home is 450 + 450 = 900GB.
These 4 partitions (sda2, sda3, sdb2 and sdb3) do not get one of the normally used filesystems, no they are being marked as Physical Volume for RAID.
Then, when you have the 4 partitions you want to put into a RAID configuration, you select the Configure Software RAID option.
It is here you join 2 partitions (sda2 and sdb2, sda3 and sdb3) together. First you get a list of what type of RAID you want to use. I chose RAID 0.

[COLOR="Blue"]This is not a real RAID because RAID is invented to avoid loss of data when a disk crashes by adding more (_R_edundant) data to the disks. With the extra data it is always possible to retrieve your original data. With RAID 0 it is just about speed, there is no extra data written to disk. Data is written to both disks at the same time. Each disk gets half of the amount of data, hence the writing process takes half as long. This is the same for reading of course.[/COLOR]

When both RAIDs are created you can set the filesystem for them. I chose EXT4, it's fast and although there are still people around who say it is not safe yet, I didn't have any problem using it since April of this year.

Continue the installation, which goes pretty fast since it is using the RAID.
In a blink of an eye Jaunty was installed and I was looking at the beautiful brown desktop. Right.

From the website: [_Kernels_]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") I installed kernel 2.6.30 which is a stable release. I did not use 2.6.31 with which I had some problems before.
The files you need are 2 files for your OS-type, the 32-bits or the 64-bits system and 1 file which is used for both systems. So, in total you need 3 files to download. They are .deb files, so easily to install using gdebi.
I use the 64-bit Ubuntu so I downloaded and installed the 64-bits kernel.```
linux-headers-2.6.30-020630_2.6.30-020630_all.deb
linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb
linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb
``` Do it in this order so all dependencies will be okay.

After re-boot to make the system use the new kernel I of course landed in the normal nVidia problems: no driver module. I booted into the low res system and from the website: [_nVidia drivers_]("http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/pool/main/n/nvidia-graphics-drivers-190/") I downloaded these files suited for Jaunty:
```
nvidia-190-kernel-source_190.36-0ubuntu1~jaunty~nvidiavdpauppa1_amd64.deb
nvidia-190-libvdpau_190.36-0ubuntu1~jaunty~nvidiavdpauppa1_amd64.deb
nvidia-190-modaliases_190.36-0ubuntu1~jaunty~nvidiavdpauppa1_amd64.deb
nvidia-glx-190_190.36-0ubuntu1~jaunty~nvidiavdpauppa1_amd64.deb
```
and installed them in that order.
Then after a next reboot all was fine and I have a new kernel and the latest nVidia proprietary driver.

Now it is just a matter of getting my data back into the /home folder, which I managed for Firefox and Thunderbird already. All my e-mails, addresses, dictionaries, add-ins, bookmarks, everything is back and working without doing anything. GREAT.
I'm still busy setting up the system, with some old programs and settings and maybe also some new.

---

