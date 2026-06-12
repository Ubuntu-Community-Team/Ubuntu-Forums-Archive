---
title: "Files get truncated on write when no space left"
date: 2010-08-03
forum: General Help
---

### Post by Umkus on 2010-08-03
Hello everyone.

The trouble is:
If I run low on free space, and I/system need to write something, then the files are just truncated. With no way to revert to their previous content.

First I installed the Windows on the VirtualBox, it sucked up all free space, so I couldn't even login to the system afterwards.

Then I, once again, silently ran out of free space, and my php editor broke. Later I discovered that it tried to write its config files, but failed, truncating them all. I lost a half a year of configurations, custom color scheme and custom code snippets.

Then one day the system just froze. Later I understood, there wasn't enough free space for it to run. 

Today I was working on my php script, for like the second day, when, again, free space ran out, so with another file-save, I got a wonderfully impressing blank php-file. It was auto-reloaded from the external change, which was failure to write to file, obviously, so no ctrl-z worked, leaving me with two days work wasted and an urge to [COLOR="Red"]hit the monitor[/COLOR] ](*,)

My questions are:
1 How can this be fixed? Besides the obvious awesome fix "watch your free space, buddy".
2 Could somebody explain why these sorts of things happen, just so I know why the ultra-safe and durable 'nix operating system wants to destroy itself sometimes?
3 Anyone else encountered this issue?

And thank you all who would participate in this thread in any way.

---

### Post by chopinhauer on 2010-08-03
> **Umkus said:**
> 
My questions are:
1 How can this be fixed? Besides the obvious awesome fix "watch your free space, buddy".
2 Could somebody explain why these sorts of things happen, just so I know why the ultra-safe and durable 'nix operating system wants to destroy itself sometimes?
3 Anyone else encountered this issue?


It happens, that's why traditionally the /var and /home filesystems where put on separate devices. And that's why the ext[234] filesystem reserves some 5% of space to the root user, so that users cannot mess the system up too badly.

This event, however, is rare enough that many developers don't take it into account when writing their software. I am not even sure if 'gzip' deals with this event correctly.

---

### Post by Umkus on 2010-08-07
Ah... Well then, it seems that the only fix available is the one I mentioned :D I'll have to be careful next time.
Thanks for the reply.

---

### Post by Umkus on 2010-08-13
Just to keep people posted on the dangers of a full hard drive -- today I've lost all of my Nautilus file browser bookmarks, local and external (ftp,sftp). Also my custom system UI colors got mixed-up a bit. I've re-broke my partitions to give ubuntu an extra space. But that looks like Ubuntu runs me, instead of me running Ubuntu :D

---

