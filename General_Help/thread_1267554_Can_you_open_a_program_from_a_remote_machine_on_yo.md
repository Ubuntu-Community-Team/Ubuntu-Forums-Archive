---
title: "Can you open a program from a remote machine on yours?"
date: 2009-09-15
forum: General Help
---

### Post by The Switch Blade on 2009-09-15
For example, can I ssh into my other machine and run an instance of gedit/firefox/whatever and see it on this machine?

---

### Post by andrewc6l on 2009-09-15
The easy way is to install a VNC server on the remote machine, then install a VNC client on your local machine.

The hard way (if both machines run X Window System) is to set the permissions on the local machine to allow X connections from the remote machine, then ssh to the remote machine and set your DISPLAY environment variable to (name of local machine):0.0, then run X programs from the command line.

---

### Post by scrooge_74 on 2009-09-15
> **The Switch Blade said:**
> For example, can I ssh into my other machine and run an instance of gedit/firefox/whatever and see it on this machine?

Yup, you only need to do ssh -XC ip_of_server then you can launch firefox or something else (if you have X running in that server obviously)

I run Kb3, firefox, VirtualBox and a few other stuff


As for using a VNC server you can install vnc4server a little setting and you are on your way. As for a VNC client Gnome has one already installed check Apps > Internet > Terminal Server client 

You can use it for vnc protocol and for vrdp (for when using Virtual PCs)

Have fun!

---

### Post by juancarlospaco on 2009-09-15
Try this in your machine:

**ssh -X $USER@127.0.0.1 nautilus**

*in example is a loopback on yourself to run nautilus...*

---

### Post by CatKiller on 2009-09-15
> **scrooge_74 said:**
> Yup, you only need to do ssh -XC ip_of_server then you can launch firefox or something else (if you have X running in that server obviously)

As a heads-up, you don't necessarily need the -C option.
> 
**-C**  Requests compression of all data (including stdin, stdout,
           stderr, and data for forwarded X11 and TCP connections).  The
           compression algorithm is the same used by gzip(1), and the
           &#8220;level&#8221; can be controlled by the **CompressionLevel** option for pro&#8208;
           tocol version 1.  Compression is desirable on modem lines and
           other slow connections, but will only slow down things on fast
           networks.  The default value can be set on a host-by-host basis
           in the configuration files; see the **Compression** option.

---

### Post by scrooge_74 on 2009-09-15
> **CatKiller said:**
> As a heads-up, you don't necessarily need the -C option.

-C option good if using stuff over wifi or over long distance into a slow network compressing data never killed anyone ;)

---

### Post by CatKiller on 2009-09-15
> **scrooge_74 said:**
> -C option good if using stuff over wifi or over long distance into a slow network compressing data never killed anyone ;)

Of course. That was my point. Where your bandwidth is limited, it makes sense to use compression. When your bandwidth isn't limited - over a local network, say - the compression/decompression steps just slows the transfer.

---

### Post by scrooge_74 on 2009-09-16
Yup I tried not using the -C but if I try to run virtual machines over wifi from server is better to use it

---

### Post by XCan on 2009-09-16
Actually, I'm running X forwarding plenty. And I can say that it's very easy for me to max out our 100 Mbit network even in apps not considered to be graphics intensive without the -C flag. Some repeated scrolling up and down in an editor maxes it out for me. :( With graphics intensive apps, it can sit there for minutes to transfer the data as well.

---

### Post by 3rdalbum on 2009-09-16
> **scrooge_74 said:**
> Yup I tried not using the -C but if I try to run virtual machines over wifi from server is better to use it

I'll keep that in mind, I never knew of the -C option.

How does -XC differ from -Y? Apparently -Y works better than just -X.

---

### Post by The Cog on 2009-09-16
> **3rdalbum said:**
> How does -XC differ from -Y?

I was wondering that.

Note that when launching firefox over a tunneled X session, you may need to run **firefox --no-remote** or it might just open a new tab in your local firefox (if it's running) instead. Not quite sure how it manages to do that, but it does.

---

### Post by scrooge_74 on 2009-09-16
that last one hasnt happen to me yet, but it could be due to having firefox in server and iceweasel in laptop

---

### Post by avongil on 2009-09-16
I have not had any luck when running this command when logged into a Solaris OS machine.   

Any help would be appreciated. Works fine, when using eeebuntu 3.0 (practically the same thing!), but when using ubuntu 9.04, I don't get any display with GTK apps.  xClock and xEyes, however work great.

---

