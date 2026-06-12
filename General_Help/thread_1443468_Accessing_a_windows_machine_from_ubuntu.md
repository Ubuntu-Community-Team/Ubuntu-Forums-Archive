---
title: "Accessing a windows machine from ubuntu"
date: 2010-03-31
forum: General Help
---

### Post by Myth123 on 2010-03-31
Hi,
    I have some friends who use Windows. Sometimes I need to help them. so I need to "view" their desktop screen. On windows its possible using a software called as teamviewer. As i don't use windows anymore on my machine, is there similar alternative for ubuntu?. Basically I don't want to log into their system, but control/ view screen.
--
Mithun

---

### Post by brain!ac on 2010-03-31
Use Team-viewer from Wine .

---

### Post by Myth123 on 2010-03-31
Does it works on wine? 
Isn't there any FOSS alternative? Its surprising if there isn't.

---

### Post by brain!ac on 2010-04-02
It should work on wine ,and if does not ,than use Winetricks to install some Video Filters like DirectX DirectPlay ,change from GDI to OpenGL disable GLSL Direct 3d Multisampling use pbuffer etc.

That what i would do for my self .

---

### Post by JoelOl75 on 2010-04-02
the rdesktop program works really well when setup correctly.  Even sending Windows sound events to the linux box.

Check some of the options of rdesktop or the Gnome version grdesktop you may find it does exatly what you need, although I prefer Nomachines NX as the compression over slow connections is much better.  I think even VNC is more bandwidth friendly.

---

### Post by HermanAB on 2010-04-02
Rdesktop is best if you need to take over a remote machine and you have control over all the routers.

Otherwise, have a look for 'One click VNC' or 'Single click VNC' or 'Reverse VNC' with Google.

The only problem with a reverse VNC connection is that it leaves *your* machine vulnerable to VNC attacks - which are very commmon.

---

### Post by Myth123 on 2010-04-07
Actually I am bit confused about remote desktop.
I have used it (tsc actually) to log in to remote pc (windows xp ).
But when I do that, It automatically logs out user working on that machine.
What i want is to "see" what user is doing and assist him.

---

### Post by wanna_try on 2010-04-29
Hi
several weeks ago there was announcing of TeamViewer version for linux, you could install it

---

### Post by 2hot6ft2 on 2010-04-29
[Teamviewer for ubuntu]("http://www.teamviewer.com/download/index.aspx?os=linux")
:popcorn:
EDIT: Just noticed this thread had been sleeping for 3 weeks before it got woken back up.

---

### Post by Myth123 on 2010-04-29
Thanks for the updates.

---

### Post by Deeday on 2010-05-01
Hey Myth123, did  it work?
Funny that my dad asked me a minute ago to remotely help him and I'm exactly in the same situation as you (Ubuntu here, Win XP there), then I stumbled on this thread. Any feedback will be much appreciated.

EDIT: do I have to install Wine, in order to use TeamViewer for Ubuntu? Cheers.

---

### Post by Myth123 on 2010-05-01
Deeday,
Have u tried installing deb file of team viewer?
Unfortunately I was busy with some other problem and didn't tried team viewer for Linux. Meantime I also come to know that VNC does the similar thing, You can try that also ([www.tightvnc.com]("http://www.tightvnc.com")).

EDIT: Just downloaded deb package. After looking at included files in it, I can say that wine is included.

---

### Post by Deeday on 2010-05-03
Thnx Myth123. I've installed the deb package; yes, Wine is included and TeamViewer works a treat. Just tested it connecting to a remote Windows machine (Win 7) and it performed flawlessly.

---

