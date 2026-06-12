---
title: "Virus blasted my Vista OS PC at home last night"
date: 2011-05-17
forum: General Help
---

### Post by Deaf Smith on 2011-05-17
So I have to options...
 
One reload Vista from CD (which I have) and restore both mine and my wifes libraries.
 
or...
 
Load this Ubuntu 10.xx server on it.
 
Now since I work at a major hospital and I do log on at work from home I need to know this.
 
a) Does the Remote desktop connection on Ubuntu work just like the Microsoft version? That is will it allow me to get on the servers at work?
 
b) Does FTP, and Firefox, is it totaly compatable so I can browse needed sites we have at work (like Redwood's Report2Web we use for reports.)
 
c) will the backups I have on CD and memory stick from the Vista restore to folders on Ubuntu?
 
Thanks for any help!

---

### Post by Cfhs_1 on 2011-05-17
> **Deaf Smith said:**
> So I have to options...
 
One reload Vista from CD (which I have) and restore both mine and my wifes libraries.
 
or...
 
Load this Ubuntu 10.xx server on it.
 
Now since I work at a major hospital and I do log on at work from home I need to know this.
 
a) Does the Remote desktop connection on Ubuntu work just like the Microsoft version? That is will it allow me to get on the servers at work?
 
b) Does FTP, and Firefox, is it totaly compatable so I can browse needed sites we have at work (like Redwood's Report2Web we use for reports.)
 
c) will the backups I have on CD and memory stick from the Vista restore to folders on Ubuntu?
 
Thanks for any help!

Why do you want to install the server edition? I'm pretty sure the desktop version will meet all of your needs.

---

### Post by Deaf Smith on 2011-05-17
Cfhs_1,
 
Cause that is what I've got! I have that here at work on my test PC for training.
  
I presume it would give me the same services as the desktop plus...

---

### Post by Cfhs_1 on 2011-05-17
sure, sure, it will work. You will have to make sure you tell it to install the GUI during the setup process, otherwise you will end up with just CLI. Other than that, ubuntu should handle everything you are asking it do do.

---

### Post by Deaf Smith on 2011-05-17
Great!
 
Will see tonight which way I go!
 
Thanks.

---

### Post by potat on 2011-05-17
> **Deaf Smith said:**
> a) Does the Remote desktop connection on Ubuntu work just like the Microsoft version? That is will it allow me to get on the servers at work?
You will have to install the rdesktop program.

> **Deaf Smith said:**
> b) Does FTP, and Firefox, is it totaly compatable so I can browse needed sites we have at work (like Redwood's Report2Web we use for reports.)
Anything that works on Firefox for Windows should work on Firefox for Linux. As for FTP, gFTP is a nice client that should do everything you want.

> **Deaf Smith said:**
> c) will the backups I have on CD and memory stick from the Vista restore to folders on Ubuntu?
You should just be able to copy those files into your home folder (anything in C:\Users\<you>\ to /home/<you>) but note that the AppData folder will be useless (application settings will not be preserved).

Hope this helps.

---

### Post by pricetech on 2011-05-17
Without a lot more information, I'd answer "maybe" to all of your questions.

Best advise, therefore, is boot to the live cd and try it.  Check everything you need to do while live to make sure it all works the way you need it to.

I don't think you'll have to install anything extra to do what you're asking, though I'm not using xubuntu, so I can't be positive.  I can tell you this, based upon my use of Ubuntu:

RDP works better under Ubuntu than it does under windows.  BUT, I'm not using the increased security introduced in Windows 7 (Vista maybe)

Firefox under Ubuntu is not discernibly different from Firefox under windows.

FTP is FTP, and any client should work with any server, assuming standards compliance.

DON'T try to copy entire profiles or libraries over to your *buntu install.  Copy the documents, pictures, music, whatever, themselves.  Even though *buntu should just ignore anything irrelevant, you'll have sort them at some point anyway so might as well do it to begin with.

One other note;  Open Office does a really good job of working with MS Office documents, but it's not one hundred percent, so you may have issues if you have a lot of MS Office documents.

Have fun with it and don't hesitate to post for help as needed.

---

### Post by wgarcia on 2011-05-17
An FTP server with an open IP adress can be cracked easily, I would recommend you to use SSH/SFTP and if you have an open IP adress protect it from brute force attacks, unless you want to see clinical histories and such of your hospital being shown in some website.

---

### Post by Deaf Smith on 2011-05-18
Ok and what about Microsoft Excell, Word, etc..
 
I know Linux has it's own word processor and when I copied a MS document it seemed to read it ok. 
 
But if I make documents with the Linux version will MS read it on Ms PC's? That way I can send documents to work as need (and my resume can be updated and sent to anyone without worring if their MS Word interpets it correctly.
 
Same with Excel.
 
I'm looking for my Vista boot disk today (DVD drive works here, not at home!) If I cannot find it then I'll go ahead.
 
Say I have a Dubain, newist version, at home I got from a PC magazine. Would that be better for a desktop at home or just go ahead with Ubuntu?
 
And how about Virus protecton? Does Norton or others work with Linux? Are they needed?
 
Thanks again.

---

### Post by Sam White on 2011-05-18
> **Deaf Smith said:**
> Ok and what about Microsoft Excell, Word, etc..
 
I know Linux has it's own word processor and when I copied a MS document it seemed to read it ok. 
 
But if I make documents with the Linux version will MS read it on Ms PC's? That way I can send documents to work as need (and my resume can be updated and sent to anyone without worring if their MS Word interpets it correctly.
 
Same with Excel.
 
I'm looking for my Vista boot disk today (DVD drive works here, not at home!) If I cannot find it then I'll go ahead.
 
Say I have a Dubain, newist version, at home I got from a PC magazine. Would that be better for a desktop at home or just go ahead with Ubuntu?
 
And how about Virus protecton? Does Norton or others work with Linux? Are they needed?
 
Thanks again.

OpenOffice / LibreOffice are both fully compatible with MS Office, just make sure you save as a .doc, .xls or whatever when you save on Ubuntu

---

### Post by Wim Sturkenboom on 2011-05-18
> **Sam White said:**
> OpenOffice / LibreOffice are both fully compatible with MS Office, just make sure you save as a .doc, .xls or whatever when you save on UbuntuIncluding macros, coding and other stuff?

---

### Post by Deaf Smith on 2011-05-19
Ok last night I did this:
 
Booted Ubuntu from CD on my home HP computer.
 
Found all my documents on the C drive and copied them to memory stick(s).
 
Installed Ubuntu as the only system (500 GB drive!)
 
Got up Firefox.
 
Today I did a virus scan on the memory stick (first one) and found no virus indicators (thank goodness!)
 
Tonight I will get the remote desktop to connect to my hospital.
 
And this weekend I'll bring home this Dell PC and network it to my home HP computer (gotta get some twisted cable here to connect them!)
 
Now the questions.
 
1. How much problem will I have with viruses via Firefox? Does it need some kind of virus checking software like on a Microsoft system?
 
2. When I changed users from my own account to my wifes a few times the screen went black and nothing would work. No keyboard, no mouse, no nothing. I had to turn of the electicity and reboot to get back to normal. Does 10.04 LTS have a problem that a newer release solves in this matter?
 
3. I presume any cheap printer will connect right to it (come to think of it I didn't test the one on it last night!
 
4. And if I buy one of those cool 1 TB external drives at Best Buy they should work fine even if they are formated for NTFS?
 
Thanks!

---

### Post by Deaf Smith on 2011-05-23
I now have two Linux PCs, both with Ubuntu.
 
Both have network cards and I have network cable to them.
 
I'm trying to make a peer to peer network of the two.
 
So do I need the network addresses for the network cards or the two? Neither seems to reconginze the other when booted.
 
I did a sudo ifconf on both and got the MAC addresses but still cannot figure out how to connect.
 
The Official Ubuntu Server book is kind of vauge.
 
Thanks for any ideas.

---

### Post by Deaf Smith on 2011-05-23
And one more question.
 
My home PC has a ethernet connection BUT the two PCs here have network cards but the network cable does not fit the ethernet at home. So do they make USB adaptors that have network cards in them so I just plug to a USB port and that is that?
 
Thanks.

---

### Post by linuxinstalledfromhdd on 2011-05-23
Try this walkthrough:

[http://www.techienote.com/2010/10/file-sharing-in-ubuntu-with-nfs.html](http://www.techienote.com/2010/10/file-sharing-in-ubuntu-with-nfs.html)

---

### Post by carson1 on 2011-05-23
I don't mean to be negative, but be sure that your employer will allow you to connect from a Linux box. I've worked at several places where this was simply not allowed, windows or nothing.

---

### Post by Hugh971 on 2011-05-23
> **carson1 said:**
> I don't mean to be negative, but be sure that your employer will allow you to connect from a Linux box. I've worked at several places where this was simply not allowed, windows or nothing.
Can't imagine that being a problem if he's just doing a standard MSTSC which it sounds like he's doing.

I think you're making things more difficult for yourself by installing the server version though. The desktop edition is geared towards home use so I'd put that on instead. 

Regarding your network, ethernet's just a standard port connection so if an ethernet cable doesn't fit then you're probably trying to plug it into a modem port. You can get USB ethernet adaptors but make sure it's linux compatible before buying.

This guide should help you set up a peer to peer network with Samba for accessing files from each computer. [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by Deaf Smith on 2011-05-23
Thanks guys I'll try the suggestions.

My employer is allowing me to learn while doing on two PCs. One I bought and the other a spare they had. Neither is connected to our network! Yes that would be a breach of security for sure.

Both of them are at work and I'm at home now! So tomorrow I take up where I left off.

Thanks.

---

### Post by Deaf Smith on 2011-06-03
Ubuntu Desktop installed. Terminal Service Client use RDP works to connect to work from home.
 
Still have one 10.04 Server OS running here at work for practice.
 
Desktop is not bad at all. 11.04 and it has alot. Was able to save most of my settings and documents by overlaying the Desktop OS over the server 10.04.
 
But....
 
When I put a User id for my wife and then switched over to her logon to test, and then tried to switch back the system went ape. A multicolor screen of lines showed up, keyboard froze, mouse froze, and I ended up having to reboot.
 
It did this twice, once again last night. So do I need some kind of upgrade or patch to allow switching of users?
 
Thanks.

---

### Post by slooksterpsv on 2011-06-03
> **Deaf Smith said:**
> ...
 
1. How much problem will I have with viruses via Firefox? Does it need some kind of virus checking software like on a Microsoft system?


I'd install an Antivirus just to check any files you may be sending to a Windows machine, it's just safer that way, otherwise you tech. don't need antivirus. I don't use any on my Linux.

> 
 2. When I changed users from my own account to my wifes a few times the screen went black and nothing would work. No keyboard, no mouse, no nothing. I had to turn of the electicity and reboot to get back to normal. Does 10.04 LTS have a problem that a newer release solves in this matter?

Uh... not sure on that one, could you get to a TTY (CTRL+ALT+F1), if so, the keyboard works and it sounds like a profile issue. Not sure on that one though...
> 
3. I presume any cheap printer will connect right to it (come to think of it I didn't test the one on it last night!

Printer, yes BUT! make sure you check the settings when printing, if mine was on photo or anything other than text (for printing) it would be blurry, could just be my printer do (HP Deskjet D1440), otherwise it works great.
>  
4. And if I buy one of those cool 1 TB external drives at Best Buy they should work fine even if they are formated for NTFS?
 
Thanks!

Yup I use an NTFS formatted Seagate drive, the only issue I have is sometimes I put files on there that Linux sees as proper naming, but Windows doesn't - so it won't copy the file or when I do chkdsk it ends up as a file001.chk - Annoying, yes, so I just skip the whole chkdsk. Either way it'll work perfect =D

---

