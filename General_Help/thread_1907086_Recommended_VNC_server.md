---
title: "Recommended VNC server?"
date: 2012-01-10
forum: General Help
---

### Post by woodyg on 2012-01-10
I would like to set up a VNC server on my Lubuntu, so that I can access it from my main machine, a Xubuntu. So far I have tried with tightvncserver, but no luck. I cannot get it running/working. I suppose it doesn't help that there doesn't seem to be a lot of documentation on how to install and run it.
[B]
Can you recommend a VNC server[/B] that is easy to use and install on lxde + being fairly lightweight?

---

### Post by imachavel on 2012-01-10
please post some configuration settings. such as ports opened, port you are rdp'ing from, etc. Also, OS and version on host machine and machine you are trying to rdp into. And, is either a server with dhcp configured? I'll step out and let the experts help you though

---

### Post by woodyg on 2012-01-10
Sorry, but half of what you asked for I don't know what it means and the other half I wouldn't know where to look for. I do know that the remote server is running Lubuntu 11.10 and that the other one, from which I'd like to access my Lubuntu machine, is a Xubuntu 11.10. I just want a fairly straightforward solution that does not require spending half a day googling installation details or too much command line. Simplicity is the keyword in this case. A GUI would be great.

---

### Post by Dangertux on 2012-01-10
Seriously, SSH. Don't use VNC, you're going to be back here saying you got cracked. If you must vnc4server :-/

---

### Post by BertN45 on 2012-01-10
Do not use VNC, try xrdp for the host. For me it worked out of the box and it works much faster then VNC. For the client you can use e.g. Remmina Remote Desktop. All available through the Ubuntu software center.

---

### Post by CharlesA on 2012-01-10
> **Dangertux said:**
> Seriously, SSH. Don't use VNC, you're going to be back here saying you got cracked. If you must vnc4server :-/
This x 9000.

I wonder if FreeNX worked with LXDE.

---

### Post by marinara on 2012-01-10
[https://wiki.edubuntu.org/Lubuntu/RemoteDesktop](https://wiki.edubuntu.org/Lubuntu/RemoteDesktop)

should work ok

---

### Post by bodhi.zazen on 2012-01-10
Use ssh 

```
ssh -X
``` where at all possible.

If you need an X server on Windows , use Xming

If you must use a VNC server I advise FreeNX. It is faster and more secure then any other VNC server.

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

[https://help.ubuntu.com/community/NomachineNX](https://help.ubuntu.com/community/NomachineNX)

---

### Post by HermanAB on 2012-01-11
Howdy,

Do yourself a favour and read the snailbook at snailbook.org.  Don't use VNC, it is pretty much the only way in which Ubuntu machines gets hacked successfully and it seems to work every time...

---

### Post by woodyg on 2012-01-11
> **marinara said:**
> [https://wiki.edubuntu.org/Lubuntu/RemoteDesktop](https://wiki.edubuntu.org/Lubuntu/RemoteDesktop)

should work ok

Thanks for the link. Proper easy to follow instructions... unfortunately I got stuck at the very last step. I have described my problem in another thread: **[COLOR=Blue][http://ubuntuforums.org/showthread.php?p=11603393](http://ubuntuforums.org/showthread.php?p=11603393)[/COLOR]**

---

### Post by vivideo on 2012-08-21
> **woodyg said:**
> Thanks for the link. Proper easy to follow instructions... unfortunately I got stuck at the very last step. I have described my problem in another thread: **[COLOR=Blue][http://ubuntuforums.org/showthread.php?p=11603393](http://ubuntuforums.org/showthread.php?p=11603393)[/COLOR]**
I run Lubuntu (Linux 3.2.0-29-generic #46-Ubuntu SMP). Vino refuses to display the vino-preferences (when entered in terminal). It gives the error message: "(vino-preferences:2020): Gtk-WARNING **: cannot open display:" (Note that the four digits after vino-preferences:xxxx seem random.)

For me, only the openssh-server should fit my needs, but I seriously would like to know a proper & safe alternative to vnc, also for use outside my LAN. I use several machines in my network, but Lubuntu is my server.

I didn't see an answer to the question whether FreeNX / NoMachine should run on Lubuntu or not.

Hope

---

### Post by CharlesA on 2012-08-21
FreeNX should be able to run ok, but you might have to configure it to use lxde instead of gnome.

---

### Post by bodhi.zazen on 2012-08-21
> **vivideo said:**
> I run Lubuntu (Linux 3.2.0-29-generic #46-Ubuntu SMP). Vino refuses to display the vino-preferences (when entered in terminal). It gives the error message: "(vino-preferences:2020): Gtk-WARNING **: cannot open display:" (Note that the four digits after vino-preferences:xxxx seem random.)

For me, only the openssh-server should fit my needs, but I seriously would like to know a proper & safe alternative to vnc, also for use outside my LAN. I use several machines in my network, but Lubuntu is my server.

I didn't see an answer to the question whether FreeNX / NoMachine should run on Lubuntu or not.

Hope

FreeNX is by far the most secure and fastest option.

Second choice would be to tunnel VNC over ssh, which will be slower.

What is wrong with ssh -X ?

---

### Post by vivideo on 2012-08-21
OK, thanx! I'll give FreeNX a try. 

But so far Putty is OK to control my server :)

---

