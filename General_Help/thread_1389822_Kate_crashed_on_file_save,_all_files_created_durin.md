---
title: "Kate crashed on file save, all files created during session lost"
date: 2010-01-24
forum: General Help
---

### Post by lizajane999 on 2010-01-24
I'm running Karmic 64-bit and Kate 3.3.90

I have been splitting up a very large (16,000 lines) text file  by copy/pasting bits of it into smaller files. I had about 40 of these smaller files loaded into a session along with the large file. About 20 were from a previous day of editing and about 20 had been added (and saved) today. 

I tried to save the file I currently had open and Kate crashed. I didn't think it was that big a deal until I reopened Kate and all of the files I had added today were gone!!

I've looked in the folder and even the backup files that should have been there for files I'd saved more than once are not there. :'(

What happened?? Is there any way to recover those files?

---

### Post by tgalati4 on 2010-01-24
Did Kate really crash or did KDE desktop crash taking all applications with it?

Check the log files in /var/log.  Also check dmesg for any hardware/disk errors.

---

### Post by lizajane999 on 2010-01-25
I'm running Gnome desktop not KDE. I had Okular up also and it didn't crash.

The Kate crash reporter came up but I dismissed it thinking it was just a minor thing. :-/

I can't find anything out of place in the log files in /var/log. 

Is there a specific file that would be especially relevant?

---

### Post by tgalati4 on 2010-01-25
The crash reporter creates a log file.  Unless you dimiss it.  Sounds like a serious bug or a hardware hiccup.

Run kate in a terminal:

kate --debug

Watch for errors as you open large files.

---

### Post by lizajane999 on 2010-01-25
I tried to crash it for an hour with 15 large files, plus the 20 I still have from my project all open at once with several unsaved. Did copy/pasting etc. No crashes or error in the terminal...

When I think about it more, it seems that something besides Kate crashed because the file icons on my desktop disappeared too right after Kate did. ??

I'll continue to use Kate for my project and will run it from the command line in the future in case it happens again. Right now, I'm hoping it was just a one time weirdness that won't happen again.

---

### Post by tgalati4 on 2010-01-25
If this is a desktop machine, I would clean it out, reseat the RAM, disks, all cables including power connector.

I had a loose power connector on a hard drive on a machine that had been up for a few years.  It had vibrated loose.  It would cause all sorts of strange disk errors--as if the disk was failing.

So, I'm guessing it was a hardware hiccup.  Most software problems leave a trace in the log files.  The hardware problems tend to freeze the kernel before any logs get written.

Keep running kate in a terminal until it freezes or some other randomness occurs.

Also run memtest for 30 cycles.  It will take overnight.

---

