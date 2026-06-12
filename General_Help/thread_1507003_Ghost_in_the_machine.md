---
title: "Ghost in the machine"
date: 2010-06-11
forum: General Help
---

### Post by peragrate on 2010-06-11
Hi everyone. I'm having a little wierdness with Ubuntu right now. In general, it is not consistent. For example, empathy will log into my gmail account, but pidgin won't.

Sometimes I have to reboot to watch a video. Otherwise the video is opened and not played.

The latest stunt is with synaptic.  I have 750mb of residual config files. When I use apt-get autoremove, the applications are actually removed! Not just the install packages.

Ubuntu is also informing me that the Human theme is not installed. But I've checked and it is.

I'm not sure where to start with this or what information to provide you with, but I hope someone out there knows Ubuntu better than I do (which isn't very difficult.)

I can tell you that I downloaded Spri Linux 9.04 Juanty, which normally runs the icevm desktop. I installed the gnome desktop and removed icevm.

Spri seems to run faster than the official Ubuntu version.

I am also wondering if some hardware is making the system unstable, but I don't know how to track it down and figure it out.

Any help is most welcomed. I'm waiting for 10.04 to work out a few of the bugs and I'm also hoping to buy new hardware soon.

How can I get a hardware report to you?

Today I tried to use openoffice and it's like it just disappeared. I've completely removed it and reinstalled it and still no dice...

Strange stuff like that. The HDD is SATA2 and is brand new. So is the GB of memory I bought the other week.

Thanks in advance.

---

### Post by peragrate on 2010-06-11
OK. My mistake. The human theme wasn't installed after all. But all of the other problems are still there...

I'm trying to talk good about Ubuntu but it is getting embarrassing that I have to reinstall the whole OS every week or so.

People are starting to ask me, "If it's so great why do you keep having to reinstall it?"

I don't have a good answer for them...

---

### Post by captain22275 on 2010-06-11
when you come to reinstalling the OS do you use the same disc as previously?

---

### Post by WinterRain on 2010-06-11
Did you check the md5sum of the ubuntu iso and verify the burn before installing? Also, as someone who installs OS's for a living, I have found that a small % of computers are just not linux compatible. It's just the way it is.

---

### Post by captain22275 on 2010-06-11
have you tried one of the later releases like 10.04 try downloading that install it and see if the problem persists i believe it's a corrupt disc

---

### Post by ankspo71 on 2010-06-11
Hi,
> The latest stunt is with synaptic. I have 750mb of residual config files. When I use apt-get autoremove, the applications are actually removed! Not just the install packages.

I think you are confusing autoremove with autoclean, which is two different things. These quotes are from "man apt-get" in the terminal. if you run that command in the terminal, you will see alot of useful information about apt-get.

> autoclean
           Like clean, autoclean clears out the local repository of
           retrieved package files. The difference is that it only
           removes package files that can no longer be downloaded,
           and are largely useless. This allows a cache to be
           maintained over a long period without it growing out of
           control. The configuration option APT::Clean-Installed
           will prevent installed packages from being erased if it
           is set to off.

autoremove
           autoremove is used to remove packages that were
           automatically installed to satisfy dependencies for some
           package and that are no more needed.

I'm not sure about your other problems, but I suspect part of it could be due to missing dependencies, meaning applications that got removed but are still needed to run other applications. They could also be hardware issues like you are saying.

About Gnome on Spri being faster...
Which gnome package did you install? gnome, gnome-core, ubuntu-desktop? Gnome and gnome-core should be alot faster than ubuntu-desktop, because with ubuntu-desktop, the official ubuntu package, has alot more applications (not to mention more services that run in the background).

Try running this command in the terminal to see if it will reinstall your missing applications: NOTE: replace ubuntu-desktop with the gnome package you installed.
```
sudo apt-get install ubuntu-desktop --reinstall
```

Hope this helps.

---

