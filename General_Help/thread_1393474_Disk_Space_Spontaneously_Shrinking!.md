---
title: "Disk Space Spontaneously Shrinking!"
date: 2010-01-29
forum: General Help
---

### Post by LukeLinux on 2010-01-29
Ok, I'm officially done with photorec.  Some of you might have seen my thread a while back where photorec caused my disk to be filled up completely, so that within moments the free space shrunk down to 0 bytes free. The solution there was fairly easy; I just had to empty out the root trash and the problem was solved.  If you haven't guessed, I used photorec again, and again my disk space is down to 0 bytes free, but *this* time there's nothing in the root trash to fix the problem so easily. There's nothing in the non-root trash, either!  DUA isn't helping me this time, either. It reports: "Total filesystem capacity: 566.7GB" which is wrong; even if it's counting my hard drive, external hard drive, and USB devices, it's still wrong. And it also says that 248.2 GB of said filesystem is free...yet then it turns around and blames the 100% disk usage on Halo, which is only 1.4GB!  I deleted a few things just so that I could use gksudo nautilus and firefox, but I don't know how long it will be before it kicks me out of those and fills up that space too! HELP!

---

### Post by oldos2er on 2010-01-29
Can you post the output of **sudo fdisk -l** run in a terminal?

---

### Post by drs305 on 2010-01-29
See if this guide helps:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

It provides some troubleshooting tips/commands to help identify the problem and solutions to fix what you find.

---

### Post by LukeLinux on 2010-01-30
Hmm...today I booted up and suddenly my memory was back! It's not like that's the first time I've rebooted to see if that was all it needed...maybe it just finally decided to clear out some backups?? I'm kind of confused now...:confused:

---

