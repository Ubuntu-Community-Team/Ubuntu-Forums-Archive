---
title: "server - sftp - ssh ?? so confused"
date: 2009-12-28
forum: General Help
---

### Post by mr_gourami on 2009-12-28
ok so i have trying to google all this and im confused. 
I just got a netbook with a small HDD. I am looking to do two things.

1. access files from my desktop and use them
-access an open office .doc and mess with it
-play an .avi

2. store files to home computer
-for travel, load it to netbook then copy/backup on home desktop

so i know what i want to do. not sure how. there is also all that cloud computing. am i better off with that? And for remote access would you first have to download the file and then use it or can it like "stream" the file? when on google i have seen home servers, sftp, ssh and cloud computing. not sure if i understand the differences between them or how they work.

---

### Post by t0p on 2009-12-28
The simplest thing to do is to install **openssh-server** on the desktop machine.  Once that's done, and your netbook is connected to the desktop, go to **Places > Connect to server** on your netbook and type in the details of the desktop's IP address or hostname, username and password, etc.  A window will open, representing the desktop computer.  Now you can drag files from one computer to the other.

If you want to be able to log into the desktop from the netbook, you'll need to install a program such as **FreeNX** on the desktop, and an NX client on the netbook.  There's an NX client for Ubuntu at [www.nomachine.com]("http://www.nomachine.com").

---

### Post by Portmanteaufu on 2009-12-28
Just a couple of clarification questions to help our responses:

What OS do you have on your netbook? 
What about your desktop at home? 
Is your desktop at home on a broadband connection? How fast (if you know)?

All of those technologies are solutions, but knowing your situation will help in determining which would be the best to use in this case.

---

### Post by mr_gourami on 2009-12-28
i run ubuntu on everything.

---

### Post by doas777 on 2009-12-28
gotta agree with t0p. just install the ssh package on the desktop. then from the laptop, open a nautilus window, and put this in the addressbar
```
ssh://<desktopNameOrIP>
``` and it will open a window to the desktops /.

---

### Post by mr_gourami on 2009-12-28
wow its that simple? and im guessing that means i would copy/download a file to the netbook and mess with it or is it live access?

---

### Post by doas777 on 2009-12-28
> **mr_gourami said:**
> wow its that simple? and im guessing that means i would copy/download a file to the netbook and mess with it or is it live access?

if you are going to be away from your home network, I would just copy the files to the netbook (or viceversa). if you are on your network however, you could just open a file live, just like from any other network source (like samba or whatever). 

I was suprised at how easy it was myself when I first figured out that nautilus could deal with ssh/sftp location. kewl eh?

---

### Post by Portmanteaufu on 2009-12-28
> **doas777 said:**
> gotta agree with t0p. just install the ssh package on the desktop. then from the laptop, open a nautilus window, and put this in the addressbar
```
ssh://<desktopNameOrIP>
``` and it will open a window to the desktops /.

That's probably the easiest solution, yup. Keep in mind, though, if you're out and about and you have your netbook on a network that isn't your home network, you'll have to connect to the IP address assigned to your router by your service provider and forward the SSH port on your router to your desktop.

To find out your external IP address (the router's), you can go to a number of sites. I use [IP Chicken]("www.ipchicken.com") out of habit.

To figure out how to forward your SSH port (22 by default) from your router to your desktop to handle outside connections, visit [Port Forward]("http://portforward.com/"). It'll walk you through the process.

---

### Post by doas777 on 2009-12-28
> **Portmanteaufu said:**
> That's probably the easiest solution, yup. Keep in mind, though, if you're out and about and you have your netbook on a network that isn't your home network, you'll have to connect to the IP address assigned to your router by your service provider and forward the SSH port on your router to your desktop.

To find out your external IP address (the router's), you can go to a number of sites. I use [IP Chicken]("http://www.ipchicken.com") out of habit.

To figure out how to forward your SSH port (22 by default) from your router to your desktop to handle outside connections, visit [Port Forward]("http://portforward.com/"). It'll walk you through the process.

agreed, Internet connectivity is another animal entirely. my suggestion is great for interal, but is incomplete if OP wants to expose ssh to teh public web.

---

