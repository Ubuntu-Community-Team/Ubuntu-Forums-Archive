---
title: "My volume control applet disappeared"
date: 2009-11-04
forum: General Help
---

### Post by eeter on 2009-11-04
Hi!
I've got a strange problem with Karmic. My volume control applet is gone after turning on my machine. And i can't find a way to get it back:S And anyway... It seems like things tend to disappear in Karmic :S During the short time I've used it the hamster-applet also stopped to show up and the desktop shows empty when I actually just had files there :S
But the volume control problem is the most weird because I cannot get it back from "Add to Panel..." and restarting the computer didn't help also.

Thanks in advance.
EeTeR

---

### Post by eeter on 2009-11-04
As it was really urgent for my work to get done and I didn't find any other solution neither from here or other forums I had to do a fresh installation.

---

### Post by dublued on 2009-11-05
i have the same problem.

i removed pulseaudio so i could use alsa and now volume applet is gone.  can't place it back on the panel because it's not in the list.

---

### Post by andrewharvey on 2009-11-21
System->Preferences->Startup Applications->Volume control should be at the bottom of the list, try toggling it.

---

### Post by Andreas1 on 2009-11-22
since karmic, volume control is no longer a panel applet, but an icon in the notification applet.

---

### Post by frisket on 2010-01-02
> **Andreas1 said:**
> since karmic, volume control is no longer a panel applet, but an icon in the notification applet.

So? I don't understand the implications of this. 

My volume control has also vanished from the panel. I'd just like to know how to get it back, and stop it from disappearing again.

---

### Post by Leppie on 2010-01-02
> **dublued said:**
> i removed pulseaudio so i could use alsa and now volume applet is gone.  can't place it back on the panel because it's not in the list.
and re-installing pulseaudio doesn't solve it?

---

### Post by jyrri on 2010-02-04
> **Andreas1 said:**
> since karmic, volume control is no longer a panel applet, but an icon in the notification applet.

I had a similar problem: both the volume control & for example Skype status icon disappeared. (Deleted by mistake when trying to delete something else...) I tried to add the volume control applet back there without success until I realised that it was actually the whole Notification Area that had disappeared.

So, I added the Notification Area (right clicking the panel, "add to panel", etc.) and both Skype icon & the volume control came back. (Using Ubuntu 9.10.)

---

### Post by Leppie on 2010-02-04
good it's working now.
i find the notification area actually to be quite nice.

---

### Post by ionospheric on 2010-02-05
> **andrewharvey said:**
> System->Preferences->Startup Applications->Volume control should be at the bottom of the list, try toggling it.

I tried this and the volume control was already enabled in startup applications, yet the icon was not in the notification area.

Then, I clicked on edit and copied the command to a shell, 

```
gnome-volume-control-applet
```

a low and behold, the icon appeared and worked!

So the problem seems to be more that the startup applications are not being run by the system?

---

### Post by Leppie on 2010-02-05
> **ionospheric said:**
> So the problem seems to be more that the startup applications are not being run by the system?
i wouldn't put it like that...
maybe on your machine the apps don't load at startup.

---

### Post by ionospheric on 2010-02-05
> **Leppie said:**
> i wouldn't put it like that...
maybe on your machine the apps don't load at startup.

Let's say I put it like
"on my machine the apps don't load at startup".

Then how do you suggest I get the apps to load at startup on my machine?

---

### Post by Leppie on 2010-02-05
is there any other apps in your the startup list that do not appear/aren't running after login?

---

### Post by ionospheric on 2010-02-05
> **Leppie said:**
> is there any other apps in your the startup list that do not appear/aren't running after login?

yes I know of at least three others that are enabled (checkbox) but do not run.

One of them is a script that I wrote myself, I disabled it and restarted but still no luck.

not sure what happened-I haven't really done anything extraordinary with the system, just regular updates..

I recently compiled and installed the driver for a Wacom tablet, but that's pretty much the most "extreme" change I have made to the system..

---

### Post by ionospheric on 2010-02-05
BTW: does startup applications refer to a system start or an x-session start? And what happened to good old CTRL-ALT-BKSP?

---

### Post by Leppie on 2010-02-05
> **ionospheric said:**
> BTW: does startup applications refer to a system start or an x-session start? And what happened to good old CTRL-ALT-BKSP?
i was referring to x-session startup.
CTRL-ALT-BKSP doesn't always work for me, rebooting does for sure start a completely new x-session.

and if you add a new application to the x-session startup list? just to see if the new one loads, you may just have to reset the launchers.

---

### Post by ionospheric on 2010-02-05
ok I figured out what the problem was:

the Gnome session was set to failsafe (which I did not notice, since I had not changed that myself, rather some program must have done that).

After I have set it to a regular session, all the startup programs are being executed again (I mean the ones set in System -> Preferences -> Startup Applications) including the ones that put the notification icons in place. Everything good now.

see this thread:

[http://ubuntuforums.org/showthread.php?t=1349651&highlight=startup+programs&page=2]("http://ubuntuforums.org/showthread.php?t=1349651&highlight=startup+programs&page=2")

---

### Post by Leppie on 2010-02-05
oh well, good it's working now ;)

---

