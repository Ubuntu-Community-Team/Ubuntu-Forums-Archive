---
title: "RDP/VNC from Ubuntu to Windows"
date: 2011-05-22
forum: General Help
---

### Post by Joe- on 2011-05-22
Im trying to remote desktop or VNC from my ubuntu laptop to my windows 7 pc. I can VNC my laptop from my pc using tightVNC and it works ok, quite laggy (any ideas on how to sort this out?) but i want to either rdp or vnc from my ubuntu laptop to my pc. My version of windows 7 is 'Home' so i dont think RDP works but i can use a vnc program to access my win7 pc? 
 
So can somebody explain to me how i can rdp/vnc to my win7 pc from my ubuntu laptop and in simple terms im still learning.
 
Ive read this post but don't really understand it : [http://ubuntuforums.org/showthread.php?t=234001](http://ubuntuforums.org/showthread.php?t=234001)
 
Cheers Joe

---

### Post by howefield on 2011-05-22
> **Joe- said:**
> ...So can somebody explain to me how i can rdp/vnc to my win7 pc from my ubuntu laptop and in simple terms im still learning.
 
Cheers Joe

I install xtight VNC on the Windows 7 machine and then use Remote Desktop Viewer from the Ubuntu machine to connect using VNC and the Windows 7 machine ip address.

---

### Post by Joe- on 2011-05-22
I have tightVNC on the windows machine but not xtightVNC? And if i try and remote view the windows 7 pc from ubuntu it just loads a black screen and then says 'Connection to *host 192.168.1.*74 was closed.'

---

### Post by CharlesA on 2011-05-22
Since you are using the Home version on Win7, you'd have to user VNC. There are a few different vnc servers for Windows. Maybe try tightvnc - that's the one I've used most often.

There is also ultravnc and a few others.

---

### Post by Joe- on 2011-05-22
I have tight VNC on my Windows 7 pc and use that to connect to UBUNTU and its fine, so what do I need to do to connect to my windows 7 pc from UBUNTU, remote viewer doesn't seem to work.

---

### Post by howefield on 2011-05-22
> **Joe- said:**
> I have tightVNC on the windows machine but not xtightVNC? 

My mistake, I mean TightVNC on windows.

---

### Post by CharlesA on 2011-05-22
> **Joe- said:**
> I have tight VNC on my Windows 7 pc and use that to connect to UBUNTU and its fine, so what do I need to do to connect to my windows 7 pc from UBUNTU, remote viewer doesn't seem to work.
Try using the Terminal Server Client, IIRC, it can connect via VNC.

---

### Post by Joe- on 2011-05-22
I trying using terminal server to connect using RDP and RDPV5 and get these errors: (See Pictures, First is RDP second is RDPV5)

The VNC selection on the options menu is greyed out? Any ideas on how I can enable it?

---

### Post by CharlesA on 2011-05-22
Hrm.

That's normal since you aren't running RDP on the windows box.

Not sure why VNC is disabled.

Have you set a password on the VNC server?

---

### Post by Joe- on 2011-05-22
Sorry what do you mean by the VNC server? The win7 pc or my ubuntu laptop?

Sorry im new to ubuntu.

---

### Post by CharlesA on 2011-05-22
On the Win7 pc. :)

---

### Post by linuxinstalledfromhdd on 2011-05-22
If just can't get it to work, for now you can try Teamviewer 6. I've used it for months with no issues, and it does a great job.

---

### Post by Joe- on 2011-05-22
Ok il give teamviewer a go, do i need to install it on both pcs? the Win7 pc and the ubuntu laptop?

---

### Post by linuxinstalledfromhdd on 2011-05-22
Yes. It's the equivalent of LogMeIn but it works in Linux and is free.  I love Teamviewer 6 for certain specific situations.  And in the future if you need to "RDC" from one linux system to another linux system you can use the "share desktop" feature in Empathy chat.  Same as old MS-CHAT RDC back in early winxp.

---

### Post by Joe- on 2011-05-22
Dude this is an epic program. Just connected to my friends pc who lives up the road from me running vista and helped him install audacity! and it works great on my ubuntu to win7 pcs.

Cheers guys really appreciate the help!

---

### Post by linuxinstalledfromhdd on 2011-05-22
Ok good. Yes, Teamviewer 6 is fun.

---

