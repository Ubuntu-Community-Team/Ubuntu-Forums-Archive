---
title: "Xorg 100% CPU after system update"
date: 2009-09-16
forum: General Help
---

### Post by pcorreia on 2009-09-16
Last night the Software Update popped up and I allowed the updates to run. I was prompted to reboot and almost immediately after rebooting my system ground to a halt. The UI would become unresponsive for minutes at a time, with only brief periods (a few seconds) when I could do anything. If I hard-rebooted the system, it seemed like I could get a few minutes of normal operation, but eventually it would become unresponsive again. I was able to run top in an SSH session and I could see that Xorg was taking most of the CPU time (it would consistently register in the 98-100% CPU range). Occasionally compiz.fusion would come up in top, so I used Synaptic Package Manager to remove all Compiz packages. This didn't seem to change the symptoms, even after reboot.

Tonight, I see that I can boot the system up and log into a non-X terminal and everything works fine. But logging in to the X session makes Xorg go to 100% CPU usage immediately, and it never goes down on its own; however, if I switch to another terminal (with Ctl-Alt-F2, for example), Xorg stops taking up CPU cycles and the system is perfectly responsive in the terminal session until I switch back (Ctl-Alt-F7).

While logged in to a non-X terminal, I examined /var/log/apt/term.log and found that the following packages were installed last night:

[LIST]
[*]libc6-i386 2.9-4ubuntu6.1
[*]libc6-dev 2.9-4ubuntu6.1
[*]tzdata-java 2009m-0ubuntu0.9.04
[*]libssl0.9.8 0.9.8g-15ubuntu3.3
[*]libopenexr6 1.6.1-3ubuntu1.9.04.1
[*]openssl 0.9.8g-15ubuntu3.3
[/LIST]

uname -a gives the following result:
```
Linux vega 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux
```

Does anyone have any idea whether there are issues with any of these packages, or can someone suggest any further investigation to do? I'm dreading the possibility of having to wipe and reinstall the operating system but I'm at my wits' end.

Thanks,
Patrick

---

### Post by P4man on 2009-09-17
can you try making a new user and logging in with that?

---

### Post by ubongo2008 on 2009-09-17
```
top
``` will tell you which process consumes the most

---

### Post by pcorreia on 2009-09-17
Thanks for the suggestions.

ubongo2008, top (in an SSH session) is how I identified that Xorg is the process that's taking 100% CPU.

P4man, I didn't think to try creating a new user. But I just logged into a non-X session, used the useradd command to create a new user, and then logged into an X session as that user. Within 2 minutes, Xorg had once again gone to 100% CPU utilization (and in fact the machine spontaneously rebooted shortly after that, which is something I haven't seen before).

---

### Post by shae on 2009-09-17
What video card/graphics driver are you using?

---

### Post by bagatonovic on 2009-09-20
I am having the same issue.  I am running 9.04 64bit.  I have 1.8ghz core2duo, 4GB ram.  If I use Fluxbox everything is fine.  It seems to be GTK stuff that causes the 100% CPU utilization, but I'm not 100% sure.  Also sometimes if I'm using a GTK file browser like Nautilus and delete a bunch of files my computer hard locks, and I have to kill the power. (no caps lock, cant switch to another console etc..)  I am considering trying a different distro, such as Fedora, because my Ubuntu system has become far less stable than Windows and all I have done is run regularly scheduled updates.  :(

---

### Post by martinreddy on 2009-10-08
I'm having the same problem - Xorg is running at 99-100% of my CPU whenever I run Firefox and several other programs (not just Gtk-based ones).

This only started happening after I accepted the recent software update. Like pcorreia, I am also running &#65279; 2.6.28-15-generic (i686). I have an NVIDIA Quadro FX 1700 card and the version 173 drivers.

This is really debilitating - I can't do work on this machine anymore. Is there a way to rollback a software update? Or is this an issue that's going to get fixed really soon?

---

### Post by martinreddy on 2009-10-08
After a bit more digging, it seemed likely that the update stomped on my display driver, so I reinstalled my NVIDIA drivers and the situation is much improved now. Just thought I'd mention it in case it helps anyone else out there seeing the same thing.

---

