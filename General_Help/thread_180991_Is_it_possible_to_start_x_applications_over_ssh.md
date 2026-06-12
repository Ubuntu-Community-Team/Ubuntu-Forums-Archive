---
title: "Is it possible to start x applications over ssh?"
date: 2006-05-23
forum: General Help
---

### Post by Dr_Deadmeat on 2006-05-23
I just want to know how I can start a X application on my laptop with ssh, like starting gaim on my home computer with my laptop on school... Is that possible?

---

### Post by MartinG on 2006-05-23
Yes, if you use the X switch, as "ssh -X n.n.n.n"

see the man page (type "man ssh" in a terminal) for more options etc.

---

### Post by Ramses de Norre on 2006-05-23
Or on windows machines you'll probably have the option to turn on x11 forwarding.

---

### Post by xtacocorex on 2006-05-23
If you do it from Windows, you'll need to have the X installed and that can get expensive with XWin32.

[http://xlivecd.indiana.edu/](http://xlivecd.indiana.edu/) is a cygwin based live cd that allows you to run xterm in Windows and you can then connect to a linux based host. As stated above, use the -X to allow X11 forwarding.

---

### Post by Ramses de Norre on 2006-05-23
You don't need to install X on windows, I use putty for windows ssh (free available on internet) and you just need to enable x11 forwarding in the settings. Your remote X server takes care of the graphics printed on the local (windows) screen then.

---

### Post by jreyst on 2006-05-23
I have Breezy on my main box and Dapper on my daughters. I ssh and run X-applications from one to the other just for amusement. I also have vmware on my main box and a Windows2000 vm that works on my main box. I want to try ssh-ing from my daughters pc to my main box and then run vmware(w2k sessio) remotely over X just to see how it runs. Then full screen it and voila my daughters pc is running Windows, over X remotely, from my pc, which is running in a virtual machine via VMware. No real reason, just again for my entertainment to see if its possible. I'm sure there might be something useful somehow that could be done with this but as I said, I just may do it to see if I can :)

---

### Post by Dr_Deadmeat on 2006-05-23
I am running Ubuntu 5.10, and 6.04 on my laptop, and I want to start up X applications on my laptop from my computer with 5.10 when someone borrow my laptop... Always funny to do a sudo killall amarok when they listen to music or a eject =D

EDIT: What I really want is the applications to pop up at the laptops X server, and not mine =)

---

### Post by xtacocorex on 2006-05-23
Ramses de Norre, I tried that in one of my school's computer labs a while ago and it didn't work. 

I'll have to try that again.

---

### Post by MartinG on 2006-05-23
[QUOTE=Dr_Deadmeat]EDIT: What I really want is the applications to pop up at the laptops X server, and not mine =)[/QUOTE]Ah, that's more tricky.  What you could try is remote desktop (krdc and krfb on a KDE system, I presume there's a Gnome equivalent), setting it up so that you can log on to the laptop without the user's active involvement.

---

### Post by Ramses de Norre on 2006-05-23
[QUOTE=xtacocorex]Ramses de Norre, I tried that in one of my school's computer labs a while ago and it didn't work. 

I'll have to try that again.[/QUOTE]
They may have been blocking the ports between 6000 and 6015 which are used for Xwindows forwarding.

---

### Post by Dr_Deadmeat on 2006-05-23
I don't realy want remote deskop as that is slow and not so fast... What I wanted was as I said a way to write a command in the terminal and the program will launch on the laptop, and not my personal computer... I have tried this
```

ssh -X <a ip or a hostname here>

```

But that only launched the GUI frontend of the program on my screen, but I'd got sound out of the laptop with launching amaroK with that method... So funny :D

---

### Post by simonn on 2006-05-23
[QUOTE=Dr_Deadmeat]I don't realy want remote deskop as that is slow and not so fast... What I wanted was as I said a way to write a command in the terminal and the program will launch on the laptop, and not my personal computer... I have tried this

But that only launched the GUI frontend of the program on my screen, but I'd got sound out of the laptop with launching amaroK with that method... So funny :D[/QUOTE]

For that, you need to use a network sound server, there is one for Linux, but cannot remember the name of it. ESD may have this capability?

Remember that the application is running on the server, not the client.

Remote mobile ringing...

1) At work, using webmin to my machine at home. 
2) Noticed my girlfriend, was using PC.
3) started mplayer with a very funky tune.
4) Seconds later my mobile rings.... 

" I don't know what I did, but music just started playing and I can't stop it."
"Hmm... like this?" [Change song] "or this? [change song]"

Snigger snigger.

[QUOTE=jreyst]I want to try ssh-ing from my daughters pc to my main box and then run vmware(w2k sessio) remotely over X just to see how it runs. [/QUOTE]

I have ssh'ed from my (PPC) iBook (OSX) to my Ubuntu desktop and run an XP VMware image. Had to giggle in a geeky fashion at seeing XP running (well... sort of) on a PPC. Quite handy as the only reason I need and have windows at all is to log in to work remotely.

---

### Post by xerxesdaphat on 2007-10-08
> **Dr_Deadmeat said:**
> I don't realy want remote deskop as that is slow and not so fast... What I wanted was as I said a way to write a command in the terminal and the program will launch on the laptop, and not my personal computer... I have tried this
```

ssh -X <a ip or a hostname here>

```

But that only launched the GUI frontend of the program on my screen, but I'd got sound out of the laptop with launching amaroK with that method... So funny :D

I too was looking for a way to do this, and this worked for me. You don't need X forwarding/remote desktop.

First of all, find out on your laptop what the display name is. You can do this by typing echo $DISPLAY . Mine was :0.0, I think most people's will be.

So then, ssh into the laptop, and $DISPLAY won't be set. Set it (export DISPLAY=:0.0). Then you can use nohup to launch the program -- e.g. nohup gedit &. Or you could just type gedit, but if you did that, you wouldn't be able to use the ssh connection as long as you left gedit open, and you'd have to leave the ssh connected for gedit to stay open. So you can use nohup and &, then disconnect from the laptop, and the program will stay open.

---

