---
title: "Setting up a Ubuntu server (x64)"
date: 2011-01-06
forum: General Help
---

### Post by LetsMugSanta on 2011-01-06
I have tried (attempted) to set up a server in the past and wasn't used to the mainly terminal part of the OS. Does anyone know of any great setup guides for the latest version (10.10)?

Also is there a command to send it from the terminal like mode into a GUI mode like Backtrack 4 has? Normally in backtrack you enter your password into the console and then type startx to get to the desktop. Is there a command like that for Ubuntu server?

Any help is appreciated as my newbness in servers is showing dramatically.

---

### Post by lrgmmc on 2011-01-06
to get a gui you would first have to install it. then yes startx.

---

### Post by LetsMugSanta on 2011-01-06
How would I do that exactly? I'm a total newb when it comes to servers.

---

### Post by seawolf167 on 2011-01-06
Take a look at this article

[ServerGUI]("https://help.ubuntu.com/community/ServerGUI")

---

### Post by LetsMugSanta on 2011-01-06
Alright since it is not really recommended to use a GUI for a server my new question is this. 
I only wish to use a server to run the server based program phpbms (google it). Would it be better to run it as a virtual machine or on a small server system. Or would I be able to install that on my desktop edition of Ubuntu and it would work fine. There is not much documentation on installing phpbms so I was a little confused.

---

### Post by seawolf167 on 2011-01-06
I'm assuming this will not be a heavily loaded server (only a couple users and a small amount of file requests), in that case, you can install a GUI or even use the Ubuntu Desktop edition without problems. Or simply install a web admin interface.

For example, in a corporate environment where there are hundreds or thousands of devices connecting to your servers and you have mail, web, and other applications/services running, a GUI is a pain to deal with especially when there is a constantly high load.

EDIT: There's no time to learn to use the server version like the present!

---

### Post by LetsMugSanta on 2011-01-06
Your assumption is correct. I do not plan on having any more than 5 users (IF THAT EVEN). I mainly just want to be able to use the program and it said I needed a server so thats where this post came from. I mainly just want to use it for myself so I can have professional looking forms and an easy interface to work with for my very very teeny tiny business that I want to start so I can make a little extra on the side. The program will be mainly for me and maybe another 2 users in the future depending on how much business I get.

---

### Post by bodhi.zazen on 2011-01-06
A GUI or desktop interface such as gnome / KDE / XFCE / openbox is both a security risk and a complete waste of time on a dedicated server.

The vast majority of server management is installing applications, editing text files, and/or starting / stopping services all of which can be done easily from the command line and over ssh with tools such as nano or vim or similar.

Even if you install gnome, the vast majority of your work will be done in a terminal or perhaps with gedit, lol.

If you still feel you need a graphical interface, use tools similar to webmin or phpmyadmin.

Yes there is a bit of a learning curve learning to run a server, but gnome/kde/xfce etc do not really help.

---

### Post by seawolf167 on 2011-01-06
With <3 users and such a small database (only being used to show off professional looking forms), I very highly doubt you'll notice a difference from the external side whether you use a GUI or even the desktop version to host phpbms.

---

### Post by LetsMugSanta on 2011-01-06
Yeah that's why I chose mainly not to go through with the GUI. Do you know of any good documentation with setting up servers with the command line then? Especially installing programs. I am still very newbish with the terminal. Also How would I install the program that I mentioned earlier? And connecting to the server through a different machine?

Is it also possible to make a virtual machine of a server just to use that program and connect to it through the web interface on the same computer?

I know that many of these questions may not be specifically related to Ubuntu but I appreciate all of the help.

---

### Post by seawolf167 on 2011-01-06
Learning ubuntu:

Click the link "linuxcommands" in my sig for a starting point. You can also read the [Ubuntu Pocket Guide ]("http://www.ubuntupocketguide.com/index_main.html")(it was written for an older version 8.04, but most of the non-configuration entries are the same)

To access the server from a remote location you'll want to use ssh (tons of info through this forum or google on setting up ssh)

Your program has its own [documentation ]("http://www.phpbms.org/wiki/PhpbmsGuide")on its website.

Here is an older [serverguide for Ubuntu 6.10 ]("https://help.ubuntu.com/6.10/pdf/ubuntu/C/serverguide.pdf")server. There is probably a new one out there, I just didn't spend much time looking for one.

As always, Google can help you answer or find just about anything.

EDIT: here is the new [server guide for 10.04]("https://help.ubuntu.com/10.04/serverguide/C/serverguide.pdf")

---

### Post by bodhi.zazen on 2011-01-06
[https://help.ubuntu.com/10.04/serverguide/C/](https://help.ubuntu.com/10.04/serverguide/C/)

If you are using Fedora, or Centos they  have similar guides.

---

### Post by LetsMugSanta on 2011-01-06
Thanks for the documentation, I appreciate it. I know this sounds retarded but would I be able to set up the server within a virtual machine, while running it on my desktop machine and connect to the web program from the desktop one?

---

### Post by lrgmmc on 2011-01-06
yes. that can be done through virtualbox. it's in the repos as well.

---

### Post by peedeeramone on 2011-01-06
> **LetsMugSanta said:**
> Thanks for the documentation, I appreciate it. I know this sounds retarded but would I be able to set up the server within a virtual machine, while running it on my desktop machine and connect to the web program from the desktop one?

i went through something similar as you a while back. if you install via virtualbox you just have to play with the virtualbox settings to get it to work the way you want it. the main thing is that you will want to assign it a static (not changing) ip on the network so that you dont have to search for it if you are on the local network and also so that you can easily forward your applicable ports to it (ssh, ftp etc). another good tip for you would be to use dyndns or another similar service to give you a easy way to reach your server from the internet like mugsanta.dyndns.com also note that you will need to set your router to update them with your wan ip so your name can follow you. hopefully i havent confused you, just offering some useful advice. you can find all this info in better detail thru google.

---

