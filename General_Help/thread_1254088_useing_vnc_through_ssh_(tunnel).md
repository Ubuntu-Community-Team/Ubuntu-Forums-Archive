---
title: "useing vnc through ssh (tunnel)"
date: 2009-08-30
forum: General Help
---

### Post by flyingsliverfin on 2009-08-30
i have no idea about this stuff, so could someone explain this?
in an ancient post i saw that somepoeple were talking about using ssh and vnc together (something about tunneling) to make it secure so u dont have to set up a firewall...

first i need to know how to sset up a vnc server, then i would like to figure out how to do that ^^^ up there

thx

---

### Post by XCan on 2009-08-31
You can "setup" your vnc server by going to system -> preferences -> remote desktop. Be sure to select a strong password if you don't block your VNC server off the internet (I strongly recommend this). 

Next, first connect to your machine using ssh ```
 ssh -L 5900:localhost:5900 user@your.server.ip 
``` Once the tunnel is established, you can start up a vnc client of choice and connect to localhost:5900.

---

### Post by fluffman86 on 2009-08-31
> **XCan said:**
> You can "setup" your vnc server by going to system -> preferences -> remote desktop. Be sure to select a strong password if you don't block your VNC server off the internet (I strongly recommend this). 

Next, first connect to your machine using ssh ```
 ssh -L 5900:localhost:5900 user@your.server.ip 
``` Once the tunnel is established, you can start up a vnc client of choice and connect to localhost:5900.

I don't think I've had any luck with that on a Linux to Linux connection, but it works when connecting from Windows to Linux.

Here's how I do it:
First, set up an ssh server on the machine you want to connect to:
```
sudo apt-get install openssh-server
```
Your standard username and password are what you use to connect.

Go ahead and test this connection from another computer with:
```
ssh username@192.168.1.103
```
Where the IP is the IP or URL of the machine you want to connect to.

If that works, then while you are already connected to the machine via ssh, install a VNC server:
```
sudo apt-get install tightvncserver
```
And then set up your VNC server on an unused X display:
```
vncserver :86
```
the "86" can be any unused X display; typically Ubuntu only uses 0 or 1.  

Now exit your SSH session (type "exit") and you will return to your local shell.  Open a VNC window with:
```
vncviewer -via username@192.168.1.103 localhost:86
```
First, that will establish a secure SSH connection just like before (with the "-via" part) and then it opens the local display that you created before.

Once you're done using VNC, you can just close the window that you opened.  To stop running display 86, just ssh back into the server, and run:
```
vncserver -kill :86
```

More information:
[http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html](http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html)
It's kinda old and based on red hat, but it still mostly works.

---

### Post by XCan on 2009-08-31
I use linux to linux all the time and it works fine. :)

---

### Post by asmoore82 on 2009-08-31
I tunnel into my box at home all the time(Linux to Linux)
and I turn on the built in vnc server on the fly so it's only on when I want to use it...

```
**[localhost]$** ssh -Y -L 5901:*remotehost*:5900 *remotehost*
**[remotehost]$** vino-preferences

```
^edit vino settings and close the settings window, but
you have to leave that terminal open for the tunnel to stay open.

Then, use "Apps -> Net -> Remote Desktop" -OR- in another terminal:
```
**[localhost]$** vncviewer localhost::5901
```

---

### Post by wefojoij on 2009-09-01
How does one close vnc to all except localhost?

---

### Post by XCan on 2009-09-02
I find that with the built-in vnc-server, the easiests was to simply install UFW and enabling it.

---

### Post by flyingsliverfin on 2009-09-06
> **asmoore82 said:**
> 
```
**[localhost]$** vncviewer localhost::5901
```

I've always wondered what does the ::5901 do?
i already had a ssh server running on the machine i want to set up a vnc server on. apart from that i installed the 'tight vnc' thing directly, not through a ssh connection ie i was physically on the computer that i wanted  to install the server on, shouldn't make a difference right?

will a firestarter firewall do anything to the ssh-ing (first time ive got a ssh server and a firewall together) and the vnc server? I have one...

PS im stuck behind a router :(

lol everything i add is making it more complicated!

---

