---
title: "Help! Printer Problem?"
date: 2009-09-21
forum: General Help
---

### Post by yuxinzhu93 on 2009-09-21
I had previously created a thread, but I wanted to change up the information to make it more clear, since it was rather confusing before 

I have a brother MCF-290C printer, and recently installed Ubuntu...i located the printer driver on the brother website but when i run the .deb file it says:

COULD NOT OPEN MFC290C...deb
THE PACKAGE MIGHT BE CORRUPTED OR YOU ARE NOT ALLOWED TO OPEN THE FILE. CHECK THE PERMISSION OF THE FILE

I already tried Package manager, running in root, etcetc

the website i used to dwload this was 
[http://solutions.brother.com/linux/e....html#MFC-290C]("http://solutions.brother.com/linux/en_us/download_prn.html#MFC-290C")

I decided to install the **MFC260C** . notice the 30 difference in the name, driver which installed with NO PROBLEM, but when i print a test page, my printer said RECIEVING DATA FROM COMPUTER, but no page came out. Would it work? what is the probelm there?

Does anyone have a solution that would allow me ot print? I need it by today?

---

### Post by Croatian_Judge on 2009-09-23
Hello, I'm not any help, but I am currently having exactly the same problem (error message) as you with the same model of printer. I'm going to be trying to figure it out tonight and if/when I do I'll post here immediately.

---

### Post by fluffman86 on 2009-09-23
re-download the .deb, and save it to your desktop as brother.deb

Go to applications > accessories > terminal and run:
```
cd Desktop
sudo dpkg -i brother.deb
```
Post the output if it doesn't install.

---

### Post by fluffman86 on 2009-09-23
actually, it looks like the files might be corrupt, just not built right.  I'm having trouble inspecting them.

---

### Post by Croatian_Judge on 2009-09-23
This is what comes out:

aaron@aaron-desktop:~$ sudo dpkg -i brother.deb
[sudo] password for aaron: 
dpkg: error processing brother.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 brother.deb
aaron@aaron-desktop:~$

Edit: Also, I am using the cupswrapper file

---

### Post by yuxinzhu93 on 2009-09-25
hm..im having same problem

---

### Post by Croatian_Judge on 2009-09-25
I did try downloading the .rpm files from the site and then converting them to .deb with alien. They installed with no problems at all but when I plug in the printer and try to find the drivers I don't see them.

---

