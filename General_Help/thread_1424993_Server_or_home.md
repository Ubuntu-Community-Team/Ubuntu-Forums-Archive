---
title: "Server or home?"
date: 2010-03-08
forum: General Help
---

### Post by archeryrob on 2010-03-08
OK, I got Ubuntu Server installed as I was looking to make a file and media server for my house. Then I saw there is no GUI and just stared at the monitor for a few moments. :oops: 

I have no intentions of working with text strings. I don't need a blazing fast server, just one that will do the job, save files stream music or videos.

So, can I use the home version and load software to make it work like a server in terminal mode? Auto boot if power is lost with out a monitor or keyboard. after setup of course.

Thanks, I'll take my beating now.:lolflag:

---

### Post by 110686 on 2010-03-08
Probably you can do this with the gnome desktop, but you still have to edit (most of) the config files manually. You can set up a file server with samba, and there are perfect tutorials for editing those config files. Even without a desktop. Just google for it!

Btw: My first problem with the command line was how to shut the machine down. :rolleyes:

---

### Post by archeryrob on 2010-03-08
Can I just use Ubuntu desktop and add server stuff like Samba to it?

I got to make this clear. I want to have a server, BUT I have no desire to learn text string commands to get it all done. I want a GUI plain and simple weather added to Server or using Home as a server.

---

### Post by isaacobezo on 2010-03-08
personally, I try to keep my server's as headless as possible. All of the protocols like SAMBA, NFS, SSHFS, can all be installed from a standard home setup through apt-get. The server provides more features, that for myself, I never use ... plus my poor little file server can not handle the overhead of all those processes.

---

### Post by lykwydchykyn on 2010-03-08
> **archeryrob said:**
> Can I just use Ubuntu desktop and add server stuff like Samba to it?

I got to make this clear. I want to have a server, BUT I have no desire to learn text string commands to get it all done. I want a GUI plain and simple weather added to Server or using Home as a server.

The only difference between regular ubuntu and ubuntu server is the default selection of packages.  You can install any of the server packages on regular Ubuntu and vice versa.

GNOME is a bit heavy on a server, but if it's what you're comfortable with go ahead and use it. Personally I prefer LXDE if I need to put a GUI on a server, which will be available with the Lubuntu distribution when Lucid Lynx is released next month.

Depending on what all you want to do with this server, it may be unavoidable to do at least some command line work to accomplish it.  File serving won't be difficult, but I have no experience with setting up a media server so I can't say for that case.

---

### Post by archeryrob on 2010-03-08
Well, as a media server it is really only acting as a file server. Itunes, real player or some other application on another client is going to call to stream that file to it.

I think I am going to start with home and see what I can do. Anyone know about setting it up in terminal mode? I don't want to have a KVM or a monitor for the computer/server and just access it remote over the network.

---

### Post by lykwydchykyn on 2010-03-08
The traditional option is VNC:

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

It can be a little slow in some cases though. 

NXserver from [www.nomachine.com](www.nomachine.com) is a good third-party option which I've used for working over a WAN.  Quite speedy and encrypted.

The other approach is to forgo the "remote desktop" approach and use a web-based administration tool.  I personally use webmin ([www.webmin.com](www.webmin.com)), though ebox is in the repositories and some people recommend that as well.

In many ways using a web-based tool is better than "remote desktop" type solutions because even once you get a desktop, there aren't always GUI tools to do what you want to accomplish.  The web based solutions provide a GUI and remote access in one fell swoop.

---

### Post by archeryrob on 2010-03-11
How do you tell what version of perl you have? From what I read it needs to be up to 5.005 or better.

I am just using a home LAN and not leaving the router.

---

### Post by lykwydchykyn on 2010-03-11
> **archeryrob said:**
> It says webadmin is for non-windows machines and has limited capabilities when installed on one. my other computers are windows machines. What is the best way to remote in to Ubuntu from one of them?

I am just using a home LAN and not leaving the router.

You're mixed up here.

You install webmin on the Ubuntu server.  You access if from your other computers through a web-browser.  It doesn't matter what the other machines are running, as long as they have a web browser.

You can install webmin on a Windows *server*, and that's the scenario where it has limited functionality.  That's not the situation you're in.

---

### Post by archeryrob on 2010-03-11
I got it in and working, a little harder to understand, but it works. I liked I could find that Perl was 5.10 and I could not find it on the desk top. Just confused so far on folder setup and sharing in webmin, but I can search it out.

Thanks, :-D

---

### Post by asmoore82 on 2010-03-11
This might interest you:
[[COLOR="Blue"]HOWTO: Perfect Headless Server Setup with Secure VNC and RDP.[/COLOR]]("http://ubuntuforums.org/showthread.php?p=8913391#post8913391")

---

