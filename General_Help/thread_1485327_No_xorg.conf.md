---
title: "No xorg.conf"
date: 2010-05-16
forum: General Help
---

### Post by ezm on 2010-05-16
I have noticed something rather strange: there is no xorg.conf file in me /etc/X11 directory.  There's a back-story here.  I had messed up my X11 configuration when I tried to install nvidia drivers--a mistake because I don't have an nvidia card; I have an intel card.  I was having trouble getting the configuration to return to its previous state, so I booted to the root and purged xserver-xorg with apt-get; then reinstalled.  This has seemed to fix my problem.  I can't boot smoothly now--whereas before I was getting a message saying that no driver was found--and I can also enable the enhanced desktop features in the "Appearance" settings.  So in fact everything is working ok at the moment, but I find it very strange that X11 is working without a configuration file.  How can I provoke it to create a xorg.conf file?

---

### Post by juniper1982 on 2010-05-16
from the console (ctrl-alt-f1 say) log in and type

sudo X -configure

that should do it.

---

### Post by scouser73 on 2010-05-16
Edited.

---

### Post by quadproc on 2010-05-16
> **ezm said:**
> I have noticed something rather strange: there is no xorg.conf file in me /etc/X11 directory. ...
The reason why you don't have an xorg.conf file is that that file is now optional.  If the X server doesn't find one then it inspects the hardware and attempts to do what makes sense.

If the X server does find the file then it will use it so you can get as much control over your graphics as you want.

quadproc

---

### Post by ezm on 2010-05-16
I'm hesitant to take these steps because I got in trouble in the first place by setting up the computer with nvidia software.  I don't have an nvidia card.  I have an Intel GM965/GL960 Integrated Graphics Controller (on a Lenovo t61).  Can you give me some more info or an explanation as to why setting up nvidia configuration is the right way to go?

---

### Post by ezm on 2010-05-16
> **quadproc said:**
> The reason why you don't have an xorg.conf file is that that file is now optional.  If the X server doesn't find one then it inspects the hardware and attempts to do what makes sense.

If the X server does find the file then it will use it so you can get as much control over your graphics as you want.

quadproc

But say I want to have an xorg.conf fil so that I can have the control that you speak of, how would I cause it to create an xorg.conf file?

---

### Post by ryan858 on 2010-05-16
I believe juniper told you how... (first post after yours)

---

### Post by ezm on 2010-05-16
> **ryan858 said:**
> I believe juniper told you how... (first post after yours)

I tried juniper's recommendation; it didn't work.  I got a message hat read like this:

[INDENT]
Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.
[/INDENT]

---

### Post by ryan858 on 2010-05-16
Yeah, I just tried it myself and got the same message. Apparently, we need to close the X session first... Can someone explain how to do that? The *X --help* didn't help me much...

**# rm -f /tmp/.X0-lock**
didn't work, just a different error saying X is running.

Neither did
[B]$ X :0 -terminate
[/B]
Also: how do we get back into our X session after dropping to console? *startx* complains about X already running, I had to reboot. Actually this is the same issue as above... How do we close X?


Edit: OK, we can get back into an existing X session by pressing *Ctrl+Alt+F7*... still no clue how to stop one. I tried */etc/init.d/gdm stop*, *serivce gdm stop*, and* stop gdm...* no luck with any of them.

---

### Post by fragos on 2010-05-17
Xorg.conf is no longer required but still may be honored if it exists. You have an Intel GPU, an Nvidia driver won't work. The Intel driver is open source and should have been loaded automatically for you.

---

### Post by rnerwein on 2010-05-17
hi
try: dexconf - generate Xorg X server configuration file from debconf data
for further information see: man dexconf

ciao

---

### Post by juniper1982 on 2010-05-18
more detailed explanation...

logout out of your x-session.  i.e.  just logout normally.  you should now see the login screen.  then hit ctrl-alt-f1 (or f2 if you wish).  you should now see a command line prompt on a mainly black screen.  you can return to your login manager by typing ctrl-alt-f7 (sometimes it is on f8).  anyways, from f1 type

```
service gdm stop
```

that will stop your login manager.  if you go to ctrl-alt-f7 your login manager should no longer be there.  then type

```
X -configure
```

that should do it.

to start your login manager again type

```
service gdm start
```

---

