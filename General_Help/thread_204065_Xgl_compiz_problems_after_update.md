---
title: "Xgl compiz problems after update"
date: 2006-06-26
forum: General Help
---

### Post by tc211 on 2006-06-26
Anybody have problems with the latest updates? I updated this morning the following:

Upgraded the following packages:
compiz (0.0.13-0quinn3) to 0.0.13-0quinn4
compiz-gnome (0.0.13-0quinn3) to 0.0.13-0quinn4
gnupg (1.4.2.2-1ubuntu2) to 1.4.2.2-1ubuntu2.1
libdrm2 (2.0+cvs20060618) to 2.0+cvs20060625 
libgl1-mesa (6.5.1-0ubuntu18) to 6.5.1-0ubuntu19
libgl1-mesa-dri (6.5.1-0ubuntu18) to 6.5.1-0ubuntu19
libglu1-mesa (6.5.1-0ubuntu18) to 6.5.1-0ubuntu19
xserver-xgl (7.0.0-0ubuntu28) to 7.0.0+cvs20060625 

Now Compiz doesn't work, and when I try to go into default gnome Xgl cpu usage is crazy high.

---

### Post by flankker on 2006-06-26
[QUOTE=tc211]Anybody have problems with the latest updates? I updated this morning the following:

Upgraded the following packages:
compiz (0.0.13-0quinn3) to 0.0.13-0quinn4
compiz-gnome (0.0.13-0quinn3) to 0.0.13-0quinn4
gnupg (1.4.2.2-1ubuntu2) to 1.4.2.2-1ubuntu2.1
libdrm2 (2.0+cvs20060618) to 2.0+cvs20060625 
libgl1-mesa (6.5.1-0ubuntu18) to 6.5.1-0ubuntu19
libgl1-mesa-dri (6.5.1-0ubuntu18) to 6.5.1-0ubuntu19
libglu1-mesa (6.5.1-0ubuntu18) to 6.5.1-0ubuntu19
xserver-xgl (7.0.0-0ubuntu28) to 7.0.0+cvs20060625 

Now Compiz doesn't work, and when I try to go into default gnome Xgl cpu usage is crazy high.[/QUOTE]

those updates killed hardware acceleration for me and so no xgl/compiz. i hope an update fixes it, but it probably wont :(

---

### Post by tc211 on 2006-06-26
How can I fix this? What a pain in the butt...my laptop is virtually useless right now with 100% CPU utilization.

---

### Post by JoWilly on 2006-06-26
I had this problem 3 days ago on 64bit with packages from the raof repo, this was fixed with an update 2 days later.

Try to revert back to previous versions until new updates are released, you can do this in synaptic by selecting "force version" in the menu.

---

### Post by hornett on 2006-06-26
[QUOTE=flankker]those updates killed hardware acceleration for me and so no xgl/compiz. i hope an update fixes it, but it probably wont :([/QUOTE]

Hmm, I wonder if this is what has caused my problems... I have XGL setup as one of my available sessions from GDM, but it will not start - and leaves me with the following in .xsession-errors...

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "retro"
/etc/gdm/Xsession: Beginning session setup...
_XSERVTransSocketOpenCOTSServer: Unable to open socket for inet6
_XSERVTransOpen: transport open failed for inet6/d600:1
_XSERVTransMakeAllCOTSServerListeners: failed to open listener for inet6
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  1 (X_GLXRender)
  Serial number of failed request:  101
  Current serial number in output stream:  102

(gnome-session:4816): Gtk-WARNING **: cannot open display:  

```

I'm using the beerorkid repo and the radeon opensource Xorg drivers. It worked pretty well before this update.

---

### Post by tc211 on 2006-06-26
Yep I was using those repos with an ATI 9200 which was working fine until this morning when I updated. Totally hosed compiz and CPU was at 100% when running apps like firefox.

Hoping an update will fix this. What a pain...spent 5 hours trying to resurrect my computer and make it functional. Tried to revert back to the old libgl mesas but kept trying to remove ubuntu-desktop etc.

---

### Post by hornett on 2006-06-26
Also not sure if this is related but I now cannot get Xorg to start DRI no matter what I do... Again it was working AFAIK before this update... :(

---

### Post by Anduu on 2006-06-26
I am sure it will get sorted out...patience grasshoppers ;)

---

### Post by Stealth on 2006-06-27
Darn it, I shouldn't have updated :P Now my XGL is all funky...does Quinn have any older versions archived somewhere? I tried doing that version thing in synaptic, but the older ones are REALLY old, not the version before last...

---

### Post by Orval on 2006-06-28
My menu panel is missing, there are no window borders and I cannot switch workspaces. Well, it's experimental...

---

### Post by JoWilly on 2006-06-28
[quote=Orval]My menu panel is missing, there are no window borders and I cannot switch workspaces. Well, it's experimental...[/quote] 
This has nothing to do with beeing experimental. What is happening is that the people who are making the deb packages available, are "playing" with cvs checkouts. So, if you are making packages with the active development tree things like this happen.

There have been verified snapshots released by novell previously, an these were (and still are) working fine.

Usually, if you take the "risk" of doing a cvs checkout, you should at least check that it works properly. This was obviously not done. Go figure...

---

### Post by nmsmith on 2006-07-01
[QUOTE=JoWilly]Try to revert back to previous versions until new updates are released, you can do this in synaptic by selecting "force version" in the menu.[/QUOTE]

I have fixed the issue twice now by reinstalling the kernel headers and the fglrx drive as in the "fixing the MESA issue" thread. In order to prevent it happening again, is it possible to tell synaptic not to upgrade those packages again?

I remember an fglrx HOWTO somewhere that started by telling you to put "fglrx" into a config file which would, (I think) keep the version from upgrading. How would I do this with another package, or have I misunderstood what that config file was doing?

---

