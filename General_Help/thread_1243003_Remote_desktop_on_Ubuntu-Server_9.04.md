---
title: "Remote desktop on Ubuntu-Server 9.04"
date: 2009-08-17
forum: General Help
---

### Post by maledikt on 2009-08-17
Hi

I recently installed Ubuntu-Server 9.04 on a box at home. I installed X and am having trouble logging into the machine with the GUI.

I can log into the machine using PuTTY but when I type startx I just get an error.

```
xauth:  error in locking authority file /home/benedikt/.Xauthority
xauth:  error in locking authority file /home/benedikt/.Xauthority
xauth:  error in locking authority file /home/benedikt/.Xauthority
xauth:  error in locking authority file /home/benedikt/.Xauthority
X: warning; process set to priority -2 instead of requested priority 0

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.

 ddxSigGiveUp: Closing log
xinit:  Server error.
xauth:  error in locking authority file /home/benedikt/.Xauthority

```

I've read up on Tightvnc, I managed to install it but not sure how I use it.

---

### Post by maledikt on 2009-08-17
What I'm trying to do is very easy on the Windows Media Server 2003 but seems to be impossible with Ubuntu 9.04.

Is there any easy way to do this? Like: 
sudo apt-get install RemoteDesktop
and run TightVNC on windows box to the IP of the server

Would be great if there is.

---

### Post by maledikt on 2009-08-17
I've decided I'm going to start over, reformat the hard drive and reinstall ubuntu server and not do anything 'till I get some solid info about what I should do as I don't want to fill my hard drive with un-needed crap. (Only 10Gb)

If there is any way to setup the Ubuntu Server to have a X window system which is available from boot to all those who know a username and password? (Is there a way to make the server usable by those who don't like using the command line?)
Also, the server is 64bit

---

### Post by maledikt on 2009-08-17
I've found a way to make it usable but not in the way I expected.
You need to type startx on the server (I moved a monitor and keyboard to it) and in X you can switch on Remote Desktop in the Preferences bar.

Now I can log in but don't have to type a username or password, so it's not what I was looking for and not really server-ish - just like a remote control on one account.

I will keep on hunting for the answer..

---

### Post by lukeiamyourfather on 2009-08-17
In order to run something like RDP or VNC you first need to have an X Server running with something like GNOME or KDE which by default most servers don't have. Ubuntu Server is probably not what you need. Download the Ubuntu Desktop installer and then install Samba to serve files instead of trying to use a system that was intended to be headless like Ubuntu Server. Typically a server installation is accessed only by SSH and there's never a GUI for an end user. Cheers!

---

### Post by maledikt on 2009-08-17
I have X installed on the Server. I want a Server since I'm trying to get a website hosted on it, with all the stuff servers use. Is there no way to remote login to desktop on ubuntu?

---

### Post by wojox on 2009-08-17
Install ubuntu-desktop-edition then install LAMP.

---

### Post by maledikt on 2009-08-17
> Install ubuntu-desktop-edition then install LAMP.

Will I be able to login to this setup remotely?
I've scoured the web vigorously and found a somewhat useful guide:
[http://blogs.koolwal.net/2009/04/28/connect-with-xdmcp-linux-remote-desktop/](http://blogs.koolwal.net/2009/04/28/connect-with-xdmcp-linux-remote-desktop/)
It only lacks a description on how to set up XDMCP via the terminal and how to make it start up on boot.
When I'm done with this I should make a guide on how I managed to do this, as this is quite the adventure - seemingly a place no one has gone before.

Edit:
I am currently downloading the ubuntu-desktop iso and I'm going to see if it allows remote login. Wish me luck.

---

### Post by theozzlives on 2009-08-17
With the Desktop Edition, you can run LAMP, SSH, DHCP, DNS, Mail, FTP servers and more. The Server edition is mainly for use on REAL servers.

I have LAMP, and SSH running on the Desktop I call a server.

---

### Post by maledikt on 2009-08-17
Thanks for the replies guys, but can the desktop version accept remote desktop connections? As my box doesn not normally have a monitor or anything attached to it, it needs to be remotely accessable.

---

### Post by HermanAB on 2009-08-17
Woah! There is a lot of mis-information in this thread.  Ignore most everything you read so far.

On the Windows client:
Install Xmingw and Putty.  Run Xmingw first, before you run Putty.   Xmingw is your X server that will display your Linux programs on Windows. Putty is the program that will connect to the Linux machine.

On the Linux server:
Run the SSH Server (sshd).  Open port 22/TCP in your firewall (if you have one).  Install Gnome on the server, but once installed, you need not run it.  You can leave the server in runlevel 3, with no X running.

Remote Log in:
You need to run Xmingw first, then Putty.  Using Putty, enable X Forwarding (somewhere in the setup), log in and launch a X program for example: gedit or gnome-panel.  It should display on Windows.

Gnome-panel will provide you the usual menu and then you can go click happy and transparently run Linux programs remotely on Windows.

Hope this helps!

---

### Post by maledikt on 2009-08-17
> **HermanAB said:**
> Install Xmingw and Putty.
Where can I find Xmingw? All I find is MinGW and their site doesn't have a huge download button like I'm used to :confused:

---

### Post by wojox on 2009-08-17
mis-information = gnome on a server

---

### Post by lukeiamyourfather on 2009-08-18
> **HermanAB said:**
> Woah! There is a lot of mis-information in this thread.  Ignore most everything you read so far.

On the Windows client:
Install Xmingw and Putty.  Run Xmingw first, before you run Putty.   Xmingw is your X server that will display your Linux programs on Windows. Putty is the program that will connect to the Linux machine.

On the Linux server:
Run the SSH Server (sshd).  Open port 22/TCP in your firewall (if you have one).  Install Gnome on the server, but once installed, you need not run it.  You can leave the server in runlevel 3, with no X running.

Remote Log in:
You need to run Xmingw first, then Putty.  Using Putty, enable X Forwarding (somewhere in the setup), log in and launch a X program for example: gedit or gnome-panel.  It should display on Windows.

Gnome-panel will provide you the usual menu and then you can go click happy and transparently run Linux programs remotely on Windows.

Hope this helps!

That Xmingw is pretty nifty, never seen that before. However its still the case that you can't run a VNC server without an X session running on the host. While Xmingw would give X forwarding on Windows its not the same as VNC. Thanks for the information!

---

### Post by maledikt on 2009-08-18
When I run Xming (without the w) and then PuTTY and try to run gedit I get:
```
PuTTY X11 proxy: wrong authentication protocol attempted
(gedit:4182): Gtk-WARNING **: cannot open display: localhost:10.0

```

I am now going to try all I can to get XDMCP to 'actually' work.

---

### Post by maledikt on 2009-08-18
3rd Ubuntu install now.
First was the Server, which didn't support GUI login. Scrapped that.
Second was the Desktop, didn't boot after install. Scrapped that.
Third is the Desktop again, now with all HDD's disconnected except the one I'm installing on (Don't want to risk losing the other data due to some random error)

Wish me luck!

---

### Post by maledikt on 2009-08-18
Ubuntu install worked.
I found a cheap way to do this, it's not Windows-XP-Smooth but I guess it works..
Allows for one user of the computer and has only a password, no users.

I would recommend using Windows Media Center instead of a Linux remote workstation but I am stuck with this one as I need ZNC, and ZNC doesn't run on Windows. Maybe I will change my mind in a year, who knows :)

---

### Post by mjwalfredo on 2009-08-18
I used to run XDMCP but once I found out about freenx, I switched and it blows XDMCP out of the water.  Especially when it comes to remoting into the machine over the Internet.

Freenx was super easy to set up once I got it added to my software sources.  I use Freenx mostly to connect to my main workstation which is upstairs where there is no air conditioning, from my laptop downstairs next to the A/C window unit.  It got over 92 degrees F today and I would have died of heat exhaustion without this setup.

---

### Post by bodhi.zazen on 2009-08-18
> **lukeiamyourfather said:**
> That Xmingw is pretty nifty, never seen that before. However its still the case that you can't run a VNC server without an X session running on the host. While Xmingw would give X forwarding on Windows its not the same as VNC. Thanks for the information!

That is not true. It depends on the VNC server.

Some VNC servers (the default one in gnome, vino and x11vn) share an X session. With a shared session you will not be able to connect unless somebody is logged into gnome (or KDE ore what have you).

vnc4server generates an separate x session. With vnc4server you can VNC in even if you are headless and no one is logged in.

If you are running a server, IMO still best to ssh -X or use a web based interface such as webmin. The problem with VNC is that it is easily cracked.

---

### Post by maledikt on 2009-08-18
> **bodhi.zazen said:**
> If you are running a server, IMO still best to ssh -X or use a web based interface such as webmin. The problem with VNC is that it is easily cracked.
If I ssh -x from a windows box I need to install cygwin, and it doesn't work out-of-the-box - and to a linux newbie this is unusable.

---

### Post by bodhi.zazen on 2009-08-18
> **maledikt said:**
> If I ssh -x from a windows box I need to install cygwin, and it doesn't work out-of-the-box - and to a linux newbie this is unusable.

It sounds as if you have not looked at putty and Xming.

both are available as a portable application, neither require installation to a hard drive, and both can be run from a USB or flash drive.

[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)

Xming comes with a portable version of putty if you like, I prefer putty.exe

---

### Post by stinger30au on 2009-08-18
remote help assist may interest u

[https://launchpad.net/remote-help-assistant](https://launchpad.net/remote-help-assistant)

---

### Post by maledikt on 2009-08-20
> **bodhi.zazen said:**
> It sounds as if you have not looked at putty and Xming.

both are available as a portable application, neither require installation to a hard drive, and both can be run from a USB or flash drive.

[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)

Xming comes with a portable version of putty if you like, I prefer putty.exe

I installed both, Xming won't connect to the XDMCP server and when I tried to open gedit through PuTTY with Xming open I just got an error.

As there is no tutorial with the package, could you care to indulge me? :D

---

### Post by bodhi.zazen on 2009-08-20
first start Xming. You have several options for how you wish to run it (separate windows or all in one). That is just personal preference and does not matter to basic functioning.

Then open Putty.

On the left, under Connection, under SSH, select X11

On the right select (check off) "Enable X forwarding".

You likely also have to edit the /etc/ssh/sshd_config to allow X forwarding, then re-start the server.

```
X11Forwarding yes
```You then connect via Putty and you type

```
gedit &
```

No need for XDMCP as you are logging in and authenticating over ssh.

If you want the entire desktop, type start X or , IMO better, ```
gnome-panel &
```

---

### Post by bferd on 2009-08-21
> **bodhi.zazen said:**
> first start Xming... 

> Then open Putty.

> Enable X forwarding

> X11Forwarding yes


Then when I try gnome-panel I get this error

```
brad@fileserver:~$ gnome-panel
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".

** (gnome-panel:4547): WARNING **: Cannot register the panel shell: cannot connect to the session bus.
```

What am I doing wrong?

---

### Post by okmat on 2009-08-21
Hello, as someone adviced before, try freeNX, it's a fast and secure way to connect to a remote desktop with full GUI.

Check my guide here: [http://www.redmezzanine.com/?p=160&lang=en]("http://www.redmezzanine.com/?p=160&lang=en")

Let me know if I can help with something.

---

### Post by bodhi.zazen on 2009-08-21
> **bferd said:**
> Then when I try gnome-panel I get this error

```
brad@fileserver:~$ gnome-panel
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".

** (gnome-panel:4547): WARNING **: Cannot register the panel shell: cannot connect to the session bus.
```What am I doing wrong?

The first few messages are "normal" your fonts may appear a tad ugly =)

The last message I have not seen not does google give me any answer. I would file a bug report.

With that said, hard to know if it is the panel or an applet you have on the panel.

What happens when you start an application ?

I test with xeyes :

```
xeyes
```

Other then than that things look fine (Display 10.0 means it is working).

---

### Post by bferd on 2009-08-21
Thanks i just followed okmat's advice and installed freeNX and it's exactly what I want and it works great.

I am having another problem though. I've posted about it here. [http://ubuntuforums.org/showthread.php?t=1246193]("http://ubuntuforums.org/showthread.php?t=1246193")

---

