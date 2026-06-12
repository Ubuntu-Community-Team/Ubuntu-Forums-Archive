---
title: "Clonezilla Live CD Not Backing Up"
date: 2010-09-05
forum: General Help
---

### Post by belkinsa on 2010-09-05
I having some problems backing up my disk with Clonezilla Live (the Ubuntu 10.04 version).  When I try to backup my disk, I get this error:

> 
C:bitmap count err, Free: 3596613
Checking free space...
(standard_in)1: Syntax error
[COLOR=Red]Something went wrong![/COLOR]  
This is after partclone checks the drive that it will put the backup on.  It stops at 97.86%.

I always get this error every time I try to do it.

---

### Post by belkinsa on 2010-09-05
I hate to do this, but anyone?

---

### Post by lmarmisa on 2010-09-05
I prefer to use the Clonezilla stable version Debian-based.

It works fine here.

---

### Post by belkinsa on 2010-09-05
What's the difference?

---

### Post by lmarmisa on 2010-09-05
I think it is more stable.

---

### Post by belkinsa on 2010-09-05
Okay, I will try that.  Thanks.

---

### Post by belkinsa on 2010-09-06
Okay, I have tried it with the other sable version and it gave me the same error.  I now understand what the error means.  It means that my drive that I will write the image to doesn't have enough room on it.  But I only have 6.5 GB used space on my Linux drive out of 144.6 GB drive.  This drive is a 280 GB drive.  Is there a problem there rather then in drive that I want to make the image?  My other drive has 53.6 GB free and used space (same number).

---

### Post by kylea on 2010-09-25
I am getting a similar error - the cloned disks are identical and the target is empty

---

### Post by Quackers on 2010-09-25
I used Clonezilla to clone two hard drives yesterday for the first time ever. I must say that all went well for me. During the running of the programme it does say that if it fails you should check the available space on the designated backup drive. I don't know why it doesn't do that itself really.
I haven't tried restoring yet, so I'll reserve my judgment for the moment :-)

---

### Post by kylea on 2010-09-25
I have downloaded a later 64bit version to see if the issue continues -

Ok version clonezilla-live-1.2.5-17-amd64 - has not got the issue.

---

### Post by bryanagee on 2010-09-26
I had this same problem; turns out, it was caused by some orphan i-nodes. The short of it: run fsck on the partition before attempting to clone it.

---

### Post by david91 on 2010-11-25
¡¡¡¡SOLUCION!!!!
 
Your Operating System has "inodos" in poor condition. To solve this do the following thing:
 
1. It initiates clonezilla of normal form.
2. When it appears, it selects to do the copy of the system in expert way.
3. In one of the emergent windows, we will have the option to scan and repair the disc before copying, we activate her.
 
Sorry I dont know very much english.
 
[EMAIL="davidrh91prueba@gmail.com"]davidrh91prueba@gmail.com[/EMAIL]

---

### Post by kylea on 2010-11-26
On my 10.04 64Bit system the solution was to use the latest 64bit version - that fixed it.

---

