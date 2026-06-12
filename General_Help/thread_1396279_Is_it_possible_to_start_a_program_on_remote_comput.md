---
title: "Is it possible to start a program on remote computer in graphical mode?"
date: 2010-02-01
forum: General Help
---

### Post by MockY on 2010-02-01
Sometimes I would like to start XBMC on my media center using my laptop. I manage this system fully via SSH, but there is one thing that I don't know how to do, or know if it is even possible.
I would like to start XBMC from my laptop so that I don't have to reboot the machine in order to do that (XBMC launches upon boot).
Is it even possible to launch a GUI on a remote computer using SSH, and if so, how?

---

### Post by stinkeye on 2010-02-02
> **MockY said:**
> Sometimes I would like to start XBMC on my media center using my laptop. I manage this system fully via SSH, but there is one thing that I don't know how to do, or know if it is even possible.
I would like to start XBMC from my laptop so that I don't have to reboot the machine in order to do that (XBMC launches upon boot).
Is it even possible to launch a GUI on a remote computer using SSH, and if so, how?
I used this tutorial to control a remote desktop and it works perfectly.
[_**[COLOR="DarkRed"]Connect to a remote Linux desktop with x11vnc and Gtk VNC[/COLOR]**_]("http://www.ghacks.net/2010/01/24/connect-to-a-remote-linux-desktop-with-x11vnc-and-gtk-vnc/")

---

### Post by MockY on 2010-02-02
Sure, I can use VNC and similar methods, but I would like to be able to do it via SSH.

---

### Post by J V on 2010-02-02
Create a shell script and attach it to a button on your menu.

---

### Post by MockY on 2010-02-02
> **J V said:**
> Create a shell script and attach it to a button on your menu.
And what would this shell script contain? I mean, I'm already logged in to the remote system, so why not just launch it while I'm there?

---

### Post by stinkeye on 2010-02-02
If I connect with ```
ssh -Y
```
I get a gui on my current computer of a program I start via the ssh login.
I've no idea of security issues though.
I've only just started playing around with ssh, connecting to a second computer on my local network.

---

### Post by tacutu on 2010-02-02
Should work if you change the DISPLAY variable on the remote computer:

```
export DISPLAY=":0.0"
```

or something like that

---

### Post by jamesman on 2010-02-02
Try:  ssh -XC [email]username@192.168.x.xxx[/email]
enter password
You will have to start programs from command line.  Xchat, seamonkey, etc work for me.

---

### Post by HermanAB on 2010-02-02
$ ssh -X -C -c blowfish user@server "gedit /etc/fstab"

or even:
$ ssh -X -C -c blowfish user@server gnome-panel

and then you can go click happy.

---

### Post by nothingspecial on 2010-02-02
> **MockY said:**
> 
I would like to start XBMC from my laptop so that I don't have to reboot the machine in order to do that (XBMC launches upon boot).


via ssh

```
sudo service xbmc-live start 
```

or it might just be ```
sudo service xbmc start
```

or restart if you just want to restart it.

---

### Post by MockY on 2010-02-02
> **nothingspecial said:**
> 
```
sudo service xbmc-live start 
sudo service xbmc start
```


XBMC does not have a service running. The actual program that is running is xbmc.bin.

> All responses suggesting -X
I don't want to run the program on the computer that I am connecting with. I've used the -X flag in the past (though that option is extremely slow unless you are within the LAN) when I'm lazy and don't want to go upstairs to my desktop in order to check my email via Thunderbird.
What I want to do is start XBMC with my laptop via SSH on my mediacenter so that I don't have to physically hook up a mouse to the machine and click the XBMC icon from the menu in case XBMC crashed or if I accidentally choose "shutdown" with my remote within XBMC.

---

### Post by nothingspecial on 2010-02-02
> **MockY said:**
> XBMC does not have a service running. The actual program that is running is xbmc.bin.


So where/how does it start.

And when?

---

### Post by MockY on 2010-02-02
> **nothingspecial said:**
> So where/how does it start.
And when?
 I have a headless machine in my living room that is hooked up to my DLP TV, so in a sense the TV is acting like a monitor, but no keyboard or mouse is hooked up. The only thing that's on it is Ubuntu with XBMC installed. XBMC is added to Startup Applications so that it launches when this machine is booting up so that I don't have to manually start it once Ubuntu is booted.
The unfortunate truth is that XBMC from time to time freezes the system, or simply crashes. This is a very rare occurrence but it does happen. And sometimes I simply just want to manually stop and start XBMC due to some testing. But how do you start a program on a machine without a keyboard or mouse physically attached without going through the hassle of using VNC? Right now I have to restart the machine in order for XBMC to start again since it does so when Ubuntu boots.

So what I simply wondered was if there is a way to start XBMC on a headless mediacenter remotely with another computer via SSH. Since I am already administrating the mediacenter via SSH (updates, installs, and so forth), I would like to be able to start a GUI application as well. I would not think that there is a way but I was curious to see if there actually was a way.

If not, then VNC is the only option, but it would be nice to not having to resort to that.

---

### Post by hopugop on 2010-05-16
> **tacutu said:**
> Should work if you change the DISPLAY variable on the remote computer:

```
export DISPLAY=":0.0"
```

or something like that

Yes! That works perfectly for me! But I still have to type it in EVERY time I log on. 

**Is there a way to create a Shell Script to run when I log in via SSH? That would be just perfect!**

---

