---
title: "Remote Desktop issues"
date: 2009-09-10
forum: General Help
---

### Post by Zylstra555 on 2009-09-10
Hello,
I have fully enabled Ubuntu's built in Remote Desktop. 
A password is set, boxes are checked for users to be allowed to access the desktop as well as control it, no confirmation to use is required, and the network is configured to automatically accept connections. 

When I open up VNC Viewer on another computer, here is what happens:
IF the computer is locked: 
I enter my password without an issue. 
ELSE IF
I get to the desktop, and I am unable to click anything. 
If I attempt to open something, and I double click it, and I return to the laptop later on, it did open. Its just that the remote view never refreshes. I have tried this on more than one computer. 


Thank you for your help, 
Jesse Zylstra
Computer IT

---

### Post by StuartN on 2009-09-10
> **Zylstra555 said:**
> I double click it, and I return to the laptop later on, it did open.

It sounds like either a low data rate on a wireless link or too much processing to generate the screen images.

I have a similar experience with one computer at a remote spot, while remote viewing works fine with other computers on my network. I recently tried remote shell instead (using "ssh -X my_remote_computer" and it provides a much better remote login - plus the remote user is unaffected, nobody needs to be logged in at all and there is no data transmission until it is actually required.

(note: ssh -X means forward X calls, so you can run graphical applications as well, such as Nautilus).

---

### Post by XCan on 2009-09-10
I'm not sure if I understand correctly, are you saying that remote desktop works fine if you have to unlock the computer, but it does not if it wasn't locked to begin with? 

For me it sounds like the classic Jaunty remote-desktop breakage. I too can unlock computers, but the desktop never refreshes, unless I disable visual effects (compiz). More info on this bug: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126)

---

### Post by Zylstra555 on 2009-09-10
I do have Compiz enabled. 

I am unable to access the desktop whether the computer is unlocked or not. I have no problem unlocking it, its just that when it reaches the desktop, I can not control it. 


I only use SSH where I beleive it is apropriate. I do not consider it a very good method of using the computer for normal every day function. I would like to use VNC (Ubuntu's built in remote access) however, assuming this compiz bug is what is causing the problem, I guess thats not happening any time soon.

---

### Post by Zylstra555 on 2009-09-12
How do I use the -noxdamage argument on Windows VNC Viewer?

---

### Post by XCan on 2009-09-13
That's a server setting. You'll have to patch Vino manually as mentioned in the link I posted, or install another vncserver that supports it out of the box. However, be advised that you can sit on your 100/100 Mbit line and with that flag enabled, it will still be slow as hell.

---

### Post by newsoft on 2009-09-13
> How do I use the -noxdamage argument on Windows VNC Viewer?


Would like to know the same

---

