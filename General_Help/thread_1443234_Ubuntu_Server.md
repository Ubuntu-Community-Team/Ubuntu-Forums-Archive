---
title: "Ubuntu Server"
date: 2010-03-30
forum: General Help
---

### Post by Jeffster999 on 2010-03-30
OK you guys are going to get tired of my endless, novice questions and for that I apologize. Having said that, here is a question for you....

Can you and more importantly, is it wise to dual boot a computer running XP/Ubuntu Server...?

Additionally, is it necessary? 

Here is the scenario...I have a laptop (dual booted and working well) and a desktop with a TB HDD, I have partitioned 247 GB to run Ubuntu but in the windows environment I can only format NTFS and logic tells me that mapping a drive from my Linux box to a windows box for file storage will not be the best...for ease of use.

Please tell me if my thinking is off and any suggestions you might have.

BTW the desktop IS a 64 bit machine

---

### Post by johngreth on 2010-03-31
If I understand correctly you want to put Ubuntu server on your desktop to store files because it has a large hard drive. That sounds like a good plan if you are comfortable working with a command prompt because Ubuntu server is terminal only. It may be easier to use Ubuntu desktop on the desktop.

Also, you want to keep XP on the desktop? That is fine but just know that if you want access to the files from your laptop while you are using XP on the desktop you will need to network to XP anyway.

Also, you could setup file sharing from XP on the desktop and permanently mount it as a drive on the laptop. I've always had trouble with file sharing in xp, but if it works for you it may be easier.

Another more reliable option for file sharing from XP is to install an ftp server (like filezilla). This can also be perminantly mounted in Ubuntu.

There are many options and I don't think using Ubuntu Server is the easiest, but I'm sure it would be the most reliable after it is set up.

---

### Post by Jeffster999 on 2010-03-31
John,
Thank You for the reply...the only real reason I was thinking about Server was b/c it is the only 64bit version I could find. The notion on terminal only doesn't really bother me as I am sure I can muddle through the commands enough to get it running. I do like the idea of setting up the ftp. I would love to hear more from you on this.

---

### Post by t4thfavor on 2010-03-31
You can use samba to share files with windows or linux, it only matters what you want to do with the machine. 

If you want to use it for other things, think Windows, or Ubuntu desktop which you can get in x64. 

I have a Ubuntu file server thats been up for months, and I havent so much as looked at it.

---

### Post by johngreth on 2010-03-31
> the only real reason I was thinking about Server was b/c it is the only 64bit version I could find
All versions of Ubuntu are released in 32 and 64 bit versions. Also, 64 bit computers can still run 32 bit operating systems. The only difference is that 64 bit can handle more than 4 gig ram.

Anyway...

Filezilla ftp server only runs on windows, but it is very easy to setup and customize:
[http://filezilla-project.org/](http://filezilla-project.org/)

Ftp is also possible on Ubuntu Server, but it is a bit more complicated to set up:
[https://help.ubuntu.com/9.10/serverguide/C/ftp-server.html](https://help.ubuntu.com/9.10/serverguide/C/ftp-server.html)

Another option for file sharing on Ubuntu server is to use Samba, which works with windows file sharing. I haven't had very good luck with this, but it may be worth a try:
[https://help.ubuntu.com/9.10/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/9.10/serverguide/C/samba-fileserver.html)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

I don't know anything about this, but "Network File System" may also be a good option. I'm not sure that it is compatible with windows though...
[https://help.ubuntu.com/9.10/serverguide/C/network-file-system.html](https://help.ubuntu.com/9.10/serverguide/C/network-file-system.html)


Also, I think that if using a terminal doesn't scare you, Ubuntu Server is better because it is not Windows and more importantly because it is optimized to run all the time without using too much power, wearing down the system, etc. If you choose to use Ubuntu Server, I also suggest installing vsftpd (the ftp server).

---

### Post by johngreth on 2010-03-31
t4thfavor also has a good point. Samba would be very easy to install/use in Ubuntu Desktop. I think my problem with it is that I've messed up my windows computers so much that they don't do file sharing at all. And also like t4thfavor said, it would allow you to use the Desktop as a computer. Ubuntu Server is still more efficient, so all options have their perks.

---

### Post by Jeffster999 on 2010-04-01
Thank You for al of the posts.

I am thinking Samba at least until I have a 100% dedicated box for Server. I have ideas on that and I am sure you guys will see that as well....LoL

---

