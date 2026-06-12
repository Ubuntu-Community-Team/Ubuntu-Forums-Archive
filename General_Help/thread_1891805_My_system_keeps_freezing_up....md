---
title: "My system keeps freezing up..."
date: 2011-12-06
forum: General Help
---

### Post by Valkyr333 on 2011-12-06
Hi,

I'm running Kubuntu 10.04.2 and my system keeps freezing. This seems to only happen when I'm using Firefox. I'm not sure if it's because of the number of tabs, but although I'm used to running three or four at once, even having one or two open seems to produce the same result intermittently. In any case, the system freezes and I can't perform any actions aside from moving around the cursor. No matter how long I leave it sitting, it never catches up with itself and resumes functioning, and I just end up having to force-reboot.

Some other things I've been noticing that may possibly be relevant:


[LIST]
[*]I've installed KDE Desktop and uninstalled Gnome. However, upon trying to re-install Gnome, I get a message saying there was a problem with package dependencies and that the action couldn't be performed.
[*]Booting up the computer shows me kind of a warped Plymouth theme, which consists of the default purple Ubuntu Plymouth between two screwy-looking jolts of the display with lots of static and jagged white bars across the screen.
[*]I had to do an OS reinstall earlier because of what seemed to be a memory problem. Ubuntu/Kubuntu kept forgetting about my installed applications (but keeping any saved data from them at the same time) and requiring me to re-install the applications. Dolphin was crashing whenever I tried to use right-click and the system's stability just seemed to be irreversibly deteriorating. I didn't know what else to do but wipe it clean and start over.
[*]I'm using the default noveau driver instead of the recommended proprietary graphics driver with that computer, since the proprietary makes the screen all screwy and chopped up. The default driver won't let me do much in the way of desktop effects, but at least it's better than the left and right halves of the display being switched with one another. I don't know what the graphics card or drivers would have to do with this, but I thought it was worth listing in case it might indicate something that could be related.
[*]The computer on which I'm running Ubuntu/Kubuntu is a Sony VAIO with 64-bit architecture. I've been warned that a VAIO is more or less no place to run Linux, but that was after I'd already bought it so I'm just trying to make the best of it.
[/LIST]

If anybody can help, I'd really appreciate it. I ditched Windows because I just couldn't deal with it anymore, but I'm just now starting to learn about computer programming and I don't feel like I can fix it on my own.

Thanks for reading, and responding if you do.

---

### Post by oldtimer7777 on 2011-12-06
> **Valkyr333 said:**
> Hi,

I'm running Kubuntu 10.04.2 and my system keeps freezing. This seems to only happen when I'm using Firefox. I'm not sure if it's because of the number of tabs, but although I'm used to running three or four at once, even having one or two open seems to produce the same result intermittently. In any case, the system freezes and I can't perform any actions aside from moving around the cursor. No matter how long I leave it sitting, it never catches up with itself and resumes functioning, and I just end up having to force-reboot.

When you have performance issues, the first step I use to diagnose something like this is throughly clean out the system:

[https://debianhelp.wordpress.com/2011/08/02/how-to-maximize-system-performance-in-ubuntu/](https://debianhelp.wordpress.com/2011/08/02/how-to-maximize-system-performance-in-ubuntu/)

And I install and use HTop to monitor which apps are running and if any seem to be causing issues and go from there. And also keep a good eye on your logs.

---

### Post by Valkyr333 on 2011-12-06
> And I install and use HTop to monitor which apps are running and if any seem to be causing issues and go from there.

So HTop is kind of like a Linux equivalent of Task-Manager in Windows?

I've looked at the logs before (or tried) and they seem very difficult to understand/interpret. I recognize patterns like dates, but a lot of it seems like one huge mass of jumbled characters. Is there a "trick" to understanding it? Or, is it more like a language you have to learn to "speak"?

Thanks for your reply, and I'll be studying the link you gave me. =)

---

### Post by linuxrev on 2011-12-06
You've installed KDE, uninstalled GNOME, and then partly re-installed GNOME. To me it seems somewhere your graphics configuration got confused. In a case like that (and assuming you have kept proper backups) I would just opt for the lazy way: clean new installation of KDE.

---

### Post by Valkyr333 on 2011-12-06
> In a case like that (and assuming you have kept proper backups) I would  just opt for the lazy way: clean new installation of KDE. 	

Do you mean reinstall the entire OS, or just go into Synaptic and mark KDE for re-installation? Or, 'other'?

---

