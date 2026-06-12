---
title: "Remote Desktop problem"
date: 2009-12-30
forum: General Help
---

### Post by loco1 on 2009-12-30
Hi - new here, converting from a windows environment

Installed Ubuntu - great, smooth, fast boot and ready to use.

I need to access this desktop remotely from another windows desktop in the same building on a local network.

The Ubuntu box has remote desktop enabled - no problems.

The box I access it from is a windows box running realvnc viewer. (also tried tightvnc - identical problem)

Here is the problem, I open realvnc viewer, type the local ip and pass - the viewer opens up with the Ubuntu box desktop initial screen draw and then that's it - it freezes on the viewer, the mouse actions on the viewer are emulating on the ubuntu box - but the visual result on the viewer (windows box) remains frozen on the intial screen draw- sending screen refresh commands still do nothing, the only fix is, reloading the viewer to see what action you happened to accidentally click on- or running upstairs to the unbuntu box to see what went fubar.

I have to do it this way with the remote desktop to access constant emails received on the unbuntu box that are not permitted to be on the windows dedicated mysql box.

I would rather not have to buy a new box to replace the ubuntu - just so that remote desktop works, as it was working fine in a windows to windows with real vnc.
I got the Ubuntu installed by convincing them that a brand spanking new windows unit was a useless spend when Ubuntu could do the job faster and with less problems.


Tips please, thanks in advance

---

### Post by junapp on 2009-12-30
I've seen that behaviour with windows to windows using tightvnc (or maybe ultra vnc) but never with plain old realvnc. On the second load of the viewer, however, things work correctly - it was like I needed to connect twice. Interesting to see it happening on a Ubuntu machine - I have a nearly identical setup here, with a Ubuntu machine headless, and remote to it from Windows all the time with realvnc without issue. 

Not really a solution, but it can work, so hang tight, I'm sure someone will have a solution. I assume you are using a password, and not requiring the local user to acknowledge the request.

You could try FreeNX which is supposed to be great (I've yet to try it out)
[http://freenx.berlios.de/](http://freenx.berlios.de/)

---

### Post by howefield on 2009-12-30
> **loco1 said:**
> ...the viewer opens up with the Ubuntu box desktop initial screen draw and then that's it - it freezes on the viewer, the mouse actions on the viewer are emulating on the ubuntu box - but the visual result on the viewer (windows box) remains frozen on the intial screen draw...

Are you running compiz on the Ubuntu machine ? If so, press alt +F2 keys and type

```
metacity --replace
```

This will stop compiz and most likely sort you out.

Although the thought of you constantly running up and down stairs to check on progress appeals to me more, lol.

---

### Post by loco1 on 2009-12-30
> **howefield said:**
> Are you running compiz on the Ubuntu machine ? If so, press alt +F2 keys and type

```
metacity --replace
```This will stop compiz and most likely sort you out.

Although the thought of you constantly running up and down stairs to check on progress appeals to me more, lol.


not when you are disabled (running was a bad wording)

compiz is?? No, unless it runs by default from fresh install of x86 32bit, then no I am not running it.

Will type the command tomorrow though and see.

---

### Post by howefield on 2009-12-30
> **loco1 said:**
> not when you are disabled (running was a bad wording)

Either way, t'was intended as a joke. I didn't really mean, fit or not, for someone to be going to so much bother to check something so trivial ;)

> compiz is?? No, unless it runs by default from fresh install of x86 32bit, then no I am not running it.

> Compiz Fusion aims to provide an easy and fun-to-use windowed environment, allowing use of the graphics hardware to render each individual window and the entire screen, to provide some impressive effects, speed and usefulness.

It is installed by default but I don't think it will run without you having activated it in some way, so it sounds like this isn't what is causing your issue.

It fixed mine which had the exact symptoms you described.

---

### Post by loco1 on 2010-01-05
well this theory didn't work.

checking other postings from other threads it seems people are having a common issue with this.
First screen render and then either disconnect or screen locking on first draw.

restarting vnc give you the next screen, but then you have to constantly rerun vnc viewer to get each action you took.

---

### Post by loco1 on 2011-02-05
Final reply to this problem.  Accessing Ubuntu 9 and onwards from a Windows based machine with vnc constant results in screen freeze on first screen image draw.  Solution, disable "effects" in appearances on Ubuntu. (the feature in appearances tab for extra visual effects from ubuntu graphics)  o/

---

### Post by Krytarik on 2011-02-12
I stumbled across this thread upon searching about another, mouse click related, vnc issue.

Unfortunately I can't be sure if the same is true for a connection from Windows (viewer) to Ubuntu (server), since I'm always running the viewer on Ubuntu, to either also Ubuntu or Windows7. I'm running x11vnc as server and RealVNC Enterprise Edition as viewer.

The Ubuntu desktop I control via vnc has Compiz enabled, and it works. I believe it's more about the used bandwith, meaning wether encryption is activated and the chosen color depth.

---

