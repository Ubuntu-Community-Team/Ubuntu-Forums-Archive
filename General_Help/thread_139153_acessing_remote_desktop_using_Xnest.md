---
title: "acessing remote desktop using Xnest"
date: 2006-03-03
forum: General Help
---

### Post by bernardfrancois on 2006-03-03
Hi,

I'm trying to acces my faster desktop computer trough a slower laptop computer.
I installed Xnest on the faster computer.

What I executed on the slow computer to bring up the fast one's desktop:
```

ssh -X ber@192.168.1.100
Xnest :1 &
export DISPLAY=:1
nautilus --no-default-window &
gnome-panel &
metacity &

```

A screenshot of this:
[http://ubuntuforums.org/gallery/displayimage.php?imageid=2141&original=1](http://ubuntuforums.org/gallery/displayimage.php?imageid=2141&original=1)

Now I have two questions/problems:
[LIST=1]
[*]How do I show the session (with all opened applications etc) of the user 'ber' which is already logged on to the faster computer? Now I can only start an 'empty' gnome session.
[*]When I close the Xnest window, I don't seem to be able to start it again. I get the following error when I try to do so:
[i]Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running[/i]
[/LIST]

---

### Post by clearscreen on 2006-03-03
I think you need to show the :0 thread of the xserver but I'm not sure.. I recall something like this when I was setting up vnc :)

---

### Post by AndyCooll on 2006-03-03
Being logged on to the fast computer is irrelevent. Xnest (or more to the point XDCMP) actually works as by logging on to the remote pc.

Have you got XDCMP enabled (you can check via administration-->login screen)?

What about installing and using FreeNX? That has a better compression rate.

:cool:

---

### Post by bernardfrancois on 2006-03-03
[QUOTE=AndyCooll]Being logged on to the fast computer is irrelevent. Xnest (or more to the point XDCMP) actually works as by logging on to the remote pc.
[/QUOTE]
You mean I don't need to open an ssh connection? How do I access Xnest on the faster computer then?

> Have you got XDCMP enabled (you can check via administration-->login screen)?
Nope, it's not enabled. What will happen exactly if I enable it?

> 
What about installing and using FreeNX? That has a better compression rate.

I was just playing around with Xnest... Maybe later I'll try FreeNX.

---

### Post by ttague on 2006-03-03
Bernard:

Here's what I would do:

1) On the Desktop machine login screen setup you want to enable XDMCP to allow a remote login screen. 

2) On the laptop you want to issue a simple command: Xnest -query desktopname :2 -geometry whateverxwhatever (e.g. 1024x768)

This will allow you to get a login screen on Desktop from Laptop. No need to start any session on Desktop ahead of time - in fact it can be (as mine are) headless, keyboardless and located several hundred feet away.

Good luck

TT

---

### Post by KermitJr on 2006-03-07
I finally got it to work.

I opened synaptic and did "Complete removal" of:

kdm
kdebase-bin

Then:
```
apt-get install kubuntu-desktop
```
This uninstalled and re-installed a large amount of programs and one prompted to overwrite the kdmrc file with an updated one.  I said yes and continued.

At the end end, I edited ```
/etc/kde3/kdm/kdmrc
``` to ```
[Xdmcp] enable=true
``` and restarted kdm via: ```
sudo /etc/init.d/kdm restart
```
Voila! now  ```
Xnest -query localhost :1
``` gives me a kdm login screen.

I'm not sure why simply trying to update didn't rewrite that kdmrc file, but the newer version is significantly different from the older version.

(PS: Don't forget to change the /etc/kde3/kdm/Xaccess file line #*     to *   )

---

### Post by frobroj on 2006-03-31
Anyone use Xnest to connect to a solaris box? I am getting some wierd results. First if I resize the window to make it larger the window grows as I specified but the viewable space for the window doesnt. So in other words the right side of the window disappears. Really wierd. Second I have problems with the keyboard working. The curor flashes when I hit keys but no characters come out. Its the same through tsclient which uses Xnest to connect via XDMCP.

Thanks
JM

---

