---
title: "FAT 32 External hard drive"
date: 2011-01-12
forum: General Help
---

### Post by SOG420 on 2011-01-12
Hello,
I have a 500 GB External Hard Drive that has a 100 GB HFS+ Partition and a @400GB FAT32 Partition. I stupidly created the Fat32 and backed up my very important schoolwork thinking it could be accessed using the 4 OS's I use  (Ubuntu Ultimate, Mac OS X.5, Windows 7, and Windows XP)Now neither hard dive can be seen using any of the OS's but the disk can be populated in XP and 7. Any suggestions? Any help would be greatly appreciated!

---

### Post by deserthowler on 2011-01-12
I didn't know you could go that big on a fat32 drive; that might be an issue.  If you can see the drive in Ubuntu, you might have some strange permission problems.

Earl

---

### Post by SOG420 on 2011-01-12
If anyone ever tries this which I dont recommend this is what I did to make it work:
Goal: Get 180 GB of data from a Fat32 formatted external drive to a NTFS formatted Windows 7 partition so it can be read by Ubuntu Ultimate, MAC OS X.5, Windows 7, Windows XP.
Step 1: Plug in hard drive to Mac OS X
become root and type in *mkdir /Users/"yourusername"/Desktop/pcdisk* then type* mount_msdos /dev/"partitionname" /Users/"yourusername"/Desktop/pcdisk *
Step 2:Connect to Mac OS X via ethernet from ubuntu ultimate using Places>connect_to_server>"ipofMac"
(I used FTP(with login) and used my mac login)
Step 3: Copy folder to NTFS partition on Windows side of computer
I choose ethernet instead of wireless because I can get speeds of 10Mbps+ that way @4 hours total. To connect a Mac and Ubuntu together via ethernet I went to the eth0 connection in Network Manager and went to IPv4 settings and selected "shared to other computer"
I know this is the most difficult way to do this but hey its working!

---

