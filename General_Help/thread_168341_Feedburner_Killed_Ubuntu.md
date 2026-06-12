---
title: "Feedburner Killed Ubuntu"
date: 2006-04-30
forum: General Help
---

### Post by joshua neff on 2006-04-30
This is on my laptop (Dell Inspiron 1100).

I went to Feedburner this morning to check on the stats on my blogs. When I clicked to log in, it tied Firefox up completely (which has happened before with Feedburner). But it also tied up the rest of the system--one of my Open-Office documents closed when I tried to maximize it, I couldn't get any of the taskbar icons or menus to work. Then, the Gnome taskbar crashed. Then, the entire system suddenly rebooted, but without the taskbar. I couldn't get anything--including the terminal--to open. So, I did a cold shut down and then turned my laptop back on. Then, I got error messages that the GUI wouldn't run. I restarted again, and now when it's loading, I get this message:

UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY
(i.e., without -a or-p options)

fsck failed Please repair manually and reboot. Please note that the root file system is currently mounted read-only. To remount it read-write:

#mount -n -o remount,rw /

CONTROL-D will exit from this shell and REBOOT the system.

bash: lesspipe: command not found
bash: dircolors: command not found

And then there's a prompt for root.

I'll admit, my knowledge of Ubuntu is nowhere near good enough to know what happened or what this message means.

Can anyone help me here?

---

### Post by joshua neff on 2006-04-30
Okay, nevermind. I ran fsck, I clicked yes on everything it asked me, and my system seems to be fine again.

*phew*

---

### Post by cilynx on 2006-04-30
Your system crashed in the middle of a write operation on the hard drive, leaving it in a somewhat broken state of being.  Generally, a fsck with <y> to everything will fix it.  As an aside: saying <y> to everything without thinking about it isn't really a good idea, but unless you have an intimate knowledge of filesystems, it's about all you can do.

---

### Post by joshua neff on 2006-04-30
[QUOTE=cilynx]Your system crashed in the middle of a write operation on the hard drive, leaving it in a somewhat broken state of being.[/quote]

Wow. Huh. Okay, thanks.

[QUOTE=cilynx]Generally, a fsck with <y> to everything will fix it.  As an aside: saying <y> to everything without thinking about it isn't really a good idea,[/quote]

Yeah, I was very wary about doing that. My heart was in my chest as I did it.

[QUOTE=cilynx]but unless you have an intimate knowledge of filesystems, it's about all you can do.[/QUOTE]

That's me all over. Like I said, I wasn't sure I should do it at all, but my knowledge of the inner workings of Ubuntu Linux is not good at all.

That being said, the fact that it did work out makes me think Ubuntu is even better for Linux newbies than I had thought.

Anyway, thanks.

---

