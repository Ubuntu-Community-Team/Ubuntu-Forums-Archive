---
title: "Login to x from Windows"
date: 2006-03-01
forum: General Help
---

### Post by fergus.b on 2006-03-01
Hi everyone

Does anyone know of a program I can use to login to my Ubuntu desktop from Windows? Any advise on how best to do this would be great!

Thanks

---

### Post by seankann on 2006-03-01
Use Remote Desktop on your Linux PC. Under Administration put in a password and make sure that you don't have ask for your permission to take control

Program to connect to it. I use TightVNC [www.tighvnc.com](www.tighvnc.com) 

For the display use 192.168.1.111:0

Shouldn't have any probs then

---

### Post by fergus.b on 2006-03-01
Thanks! I'm busy downloading tightvnc now and I'll let you know how it goes.

---

### Post by mlind on 2006-03-01
yeah, tighVNC rocks!

You can even do it the other way around, from Linux to Windows.

---

### Post by Fred Doolie on 2006-03-01
<Gasps>
Please explain this concept to a Noobee.  Are these two seperate computers that are physically (or wirelessly)  networked together?  Like your Win system is the desktop in the office and the Ubuntu is your laptop outside in the back yard?

Can this "Remote Desktop" be done from outside the network through the Intenet? I'm imagining being out somwhere and being able to use my Ubuntu system from where I am as if I were at home. Is the Remote Desktop graphical? Can it be accessed through a web browser?

Enquiring minds want to know.

---

### Post by fergus.b on 2006-03-01
[QUOTE=Fred Doolie]<Gasps>
Please explain this concept to a Noobee.  [/QUOTE]
Yeah, you've got it pretty right. Its similar to Remote Desktop Connection in Windows XP. You connect to a second pc from yours and get a full graphical desktop with full control. It could be done over the internet but would probably be insecure unless you're using ssh. This isn't browser based. You need a special client. tightvnc seems to be a good one and it works Linux and Windows.

seankann I have it working now. I just needed to add the connecting pc to my allowed hosts in firestarter. Thanks a ton for the help :KS

---

### Post by hw-tph on 2006-03-01
[Cygwin](http://www.cygwin.com) provides an X server which means you can get a real X desktop on your Windows system. Or start a Cygwin bash shell, and connect to a remote host running Linux using **ssh -X user@host** and start Firefox. It will be displayed on your local Windows screen. Very neat.


Håkan

---

### Post by fergus.b on 2006-03-01
[QUOTE=hw-tph][Cygwin](http://www.cygwin.com) provides an X server which means you can get a real X desktop on your Windows system. Or start a Cygwin bash shell, and connect to a remote host running Linux using **ssh -X user@host** and start Firefox. It will be displayed on your local Windows screen. Very neat.


Håkan[/QUOTE]
Will this give better performance than using a client like tightvnc?

---

### Post by hw-tph on 2006-03-02
[QUOTE=fergus.b]Will this give better performance than using a client like tightvnc?[/QUOTE]

Sometimes, yes. It has the upside that you can display only the application you're using instead of the full desktop. In low bandwidth situations it still works pretty well.


Håkan

---

