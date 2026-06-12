---
title: "Ubuntu hard-drive not recognised on other machines"
date: 2010-06-07
forum: General Help
---

### Post by neilraygun on 2010-06-07
Hi, 

I installed Ubuntu a few weeks ago on a spare laptop (on a Serial ATA Samsung 500500JI). It was my first experiment outside the Windows and Apple OSs and all went well. However, I need the hard-drive (and more specifically the files on it) on a new Windows-run laptop. 

I have attached the hard-drive via a caddy to both a Windows and an Apple laptop. Both recognise it as a healthy drive, but neither will allow me to browse the files on it. 

I'm a little out of my depth, but I get the sense that it may have something to do with either the file system, or the assigning of a drive letter. I can't currently change the drive letter in Windows 7 using its onboard drive management control panel. All such options are greyed out. I've now put the HDD back in the Ubuntu laptop and am looking at the disk utility, but honestly don't know what I'm looking to do.

ANy pointers anyone can give would be very gratefully received.

Cheers!

---

### Post by spiky001 on 2010-06-07
I think the problem is maybe the linux file system is in ext4 I,m pretty sure it cant be read by the other OS,s i,m not a 100% sure if I,m wrong some 1 will correct me

---

### Post by neilraygun on 2010-06-07
Thanks Spiky. I did wonder that, but I also thought that Macs work on a linux-based system. So will I need to change it to NTFS or FAT32 to work as an external drive for Windows 7?

And if so, how....?

:-)

---

### Post by HermanAB on 2010-06-07
Good old FTP to the rescue.

Leave the disk in the Linux machine and install Filezilla Server and Client on Windows, or vsftpd on Linux with Filezilla Client on Windows.

FTP is insecure, but very easy to install and get to work.  It is fine for use on a LAN.

---

### Post by spiky001 on 2010-06-07
haha not sure how to or if is a good idea maybe make a new partition on ubuntu make it ntfs, then move your files to there

---

### Post by darkdragn on 2010-06-07
Herman's idea is the best route... ^_^, but i say try using samba instead, in case you want a more drag and drop way to push the data.
(Need any tips on the config, i can help. Just PM me... i'm a little bored right now anyway)

---

### Post by spiky001 on 2010-06-07
That is if the op can network

---

### Post by linux-hack on 2010-06-07
if you want to share files between linux and other OSs you should make a NTFS or even better a FAT partition so other systems will be able to read 'it. Almost all systems can read FAT32 file systems ans it's the best way to share the your files. and install samba also on you linux machine if your on a windows network.

---

### Post by neilraygun on 2010-06-07
Thanks all. The FTP concept is a good one, but as my ISP gives awful up-speed (just took over an hour to upload a 184mb file to Yousendit) I'm not sure I want to think about how long 150gb will take.

I think I'm going to go the route of dragging everything across a network, then reformatting the HDD to be HDD or FAT32 so that I can use it as an external backup drive. The only issue I have now is making this Ubuntu machine networked.

Am playing around with Samba, but I'm a little out of my depth with the command line stuff and it's so far not proved too fruitful! I *think* I've installed it, but can't find anything in the applications or system drop downs.

---

### Post by spiky001 on 2010-06-07
Hi I think if you installed samba it will listen as a server  I have not used it but i think you should be able to connect via file manager

---

### Post by neilraygun on 2010-06-07
Right, so you're saying that I should be able to see it from a Windows machine? In other words I can "pull" from it, instead of pushing from it?

Will it automatically have made the whole drive shared? If not, how do I make it shared?

Sorry, so many questions....!

:-)

---

### Post by spiky001 on 2010-06-07
yes pull from it 

[B]Windows Network Neighborhood 
can you see samba shares
[/B]

---

### Post by neilraygun on 2010-06-08
Thanks again, all. 

Reckon I'll be able to sort this tomorrow with a bit of luck, but had to head to Dublin on short notice. Will be back at home again tomorrow, with a bit of luck!

---

### Post by linux-hack on 2010-06-11
If your not comfortable with the command line try using webmin ..

---

