---
title: "gnome-settings-daemon crashing/ slowing down"
date: 2010-11-27
forum: General Help
---

### Post by wasiliy on 2010-11-27
Hello, 

about every second time when I start up my Ubuntu 10.4, my hard drive starts to work heavily. While it's doing so I see in the system monitor that the gnome-settings-daemon has the status 'uninterruptible'. After about 3 minutes the hard drive calms down and the status of gnome-settings-daemon switches to 'sleeping'. so from that I guess the heavy working of the hard drive is somehow related to that process. 
Sometimes gnome-settings-daemon seems to crash completely so that my theme is gone.

So is there a solution to that? because it's annoying that it slows down the system for about 3 minutes after start up.

On the net I've found some old threads from 2004 and 2006 which describe crashing of gnome-settings-daemon. But there didn't seem to be a solution. Did I miss anything?

---

### Post by Nabo00o on 2011-06-22
Sorry for the late response, but I have this exact problem too.  Not only is there heavy cpu usage, all gnome related operation take much longer time to finish, and even worse, key shortcuts that I made for things like the terminal will not work at all until the daemon is finished with whatever it is doing! And at the exact time it is done, the terminal pops up if I had pressed the shortcut before....    Really irritating. And now I do also quite regularly experience that gnome crashes and auto restarts itself. It wouldn't have been such a problem as the process is done in a matter of seconds, but it happens so often...    The weirdest thing of all is when my theme sometimes changes. It happens exclusively when I'm using WINE, and it actually looks like WINE is trying to force some old windows theme on the entire gnome system... It might be some X theme standard though I'm not sure...  Julian    Edit: Yeah I'm using Lucid (10.04) too.

---

### Post by cherep on 2011-07-16
I have the same problem. Disk usage by gnome-settings-daemon is high just after the start-up. Nothing related to GNOME is working. I use Ubuntu 10.10 + GNOME 2.32

One can try this:
[https://bugzilla.gnome.org/show_bug.cgi?id=625609#c6](https://bugzilla.gnome.org/show_bug.cgi?id=625609#c6)

Hagen Fürstenau 2011-07-04 07:40:51 UTC

workaround: start gconf-editor and untick

/apps/gnome_settings_daemon/plugins/housekeeping/active

Apparently this will also disable the low disk space check and warning (and
maybe something else as well?), but I guess this isn't essential...

---

### Post by k1w1 on 2011-08-15
Hello and Thanks for the suggestions here which have solved the same problem I've had since Karmic.

My computer would become almost unusable starting just over 2 minutes from login and the hard drive light was constantly on.  This continuous hard drive activity would last for another 4-5 minutes. It was coming to the point of switching to Kubuntu to see if that had the same problem, when I saw a suggestion to try htop to see what may have been causing the continuous hard drive activity.
I recently installed htop to observe what was happening when this activity started and found gnome-settings-daemon at the top of the list during that time.  And after a bit of searching via google, as the forum search wouldn't accept "gnome-settings-daemon", found this thread.

Have disabled the housekeeping/active setting as in cherep's post, and the computer is now usable from startup! (after over 2 years).

So it appears this problem may come with having an encrypted home directory and having many images stored within that directory. Please correct me is this is incorrect.

I'm using Ubuntu 10.04 with Gnome 2.30

---

