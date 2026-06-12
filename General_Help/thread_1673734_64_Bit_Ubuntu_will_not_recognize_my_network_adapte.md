---
title: "64 Bit Ubuntu will not recognize my network adapter....."
date: 2011-01-22
forum: General Help
---

### Post by napoliforever13 on 2011-01-22
Hello guys. I decided to install Ubuntu 10.10 64bit on my desktop computer so it would run alongside Windows 7. Everything works fine except I cannot get it on the Internet. I use a wireless network adapter (Linksys AE1000 Wireless-N) to connect to the internet on Windows 7. I have been reading forums this entire day and it's gotten me to the point where I'm about to throw my desktop out the windows!!! Please help me as I want to use Ubuntu. I have my Adapters installation CD if needed.
-THINGS I'VE ATTEMPTED TO DO-
I've already download the NDISGTK along with the other two things it comes with. I used my Ubuntu CD as a source to download the files. 
I went to System>Administration>Wireless Network Drivers, and I put my network adapter's (Linksys AE1000) software CD in the CD Drive. I clicked "Install New Driver and went into the XP section (as none of the others worked, and it says "rt2870, Hardware Present: Yes)
I also posted this on Yahoo! Answers. The link is [http://answers.yahoo.com/question/index?qid=20110122170629AAhoUQm](http://answers.yahoo.com/question/index?qid=20110122170629AAhoUQm)

---

### Post by Bitrate on 2011-01-22
Did you read this thread ?

[http://ubuntuforums.org/showthread.php?t=1621022](http://ubuntuforums.org/showthread.php?t=1621022)

---

### Post by connork on 2011-01-24
Hey guys,

Got a somewhat similar issue. Using the AE1000 wireless-N adapter as  well; I've installed and reinstalled ndisgtk , ndiswrapper, and the  amd64 netr28ux.inf driver (win7).

However, running lsusb gives me no device information for the linksys adapter other than:

Bus 001 Device 006: ID 13b1:002f Linksys

Just 'Linksys', no ID information at all. Also:

:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


Anyone run into this before? I posted this as well in [http://ubuntuforums.org/showthread.php?t=1621022]("http://ubuntuforums.org/showthread.php?t=1630358") , but since that one is marked Solved, I figure it can't hurt to post it here.

---

### Post by cariboo on 2011-01-24
I've found that most 64-bit Windows drivers don't work with ndiswrapper. My D-Link WUA-2340 won't work when running a 64-bit vesion of Ubuntu, but works quite well on 32-bit versions, using the 32-bit windows drivers..

---

