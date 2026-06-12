---
title: "UBUNTU BROKE WINDOWS!!  (not a pun.)  EVEN SAFE MODE!  HELP!"
date: 2009-08-12
forum: General Help
---

### Post by triplesick on 2009-08-12
EDIT: New details!  Ignore the below, unless you're curious.  The problem seems to be this: the disk thinks that one partition is actually two partitions.  I don't understand computers so I don't know what it means, but look at the attached screenshot.  It thinks there are two MEDIADIRECT partitions.  Or something.  I am certain this is the problem because I found this thread with the same problem, but the prognosis is not good--he completely destroyed his computer.
[http://ubuntuforums.org/showthread.php?t=935950&page=2](http://ubuntuforums.org/showthread.php?t=935950&page=2)

I installed Jaunty as a dual-boot alongside WindowsXP and everything was working fine, until 10 minutes ago.  Now, when I try to boot into Windows, even if I try to boot into safe mode, I get a blue screen of death, something to the effect of 'Plug and Play driver isn't working properly, shutting down to avoid damage to your system.'

Here's what preceded it:
1. I mounted the drive in linux via the GUI.  IE, I just double-clicked 103.0GB MEDIA and typed in my password.

2. I tried to watch a DVD, but couldn't.

3. I turned off my computer and booted up with Dell's "MediaDirect," something I've never messed with before even though I've had the computer for a year.  This MediaDirect thing is supposed to let you watch DVD without loading windows.  I think it runs from its own partition, with OS titled "Windows XP Embedded."

4. MediaDirect gave me the blue screen of death.  I tried to boot regularly into XP, got the blue screen.  Tried safe mode, same thing.  But Ubuntu works fine.

WHAT SHOULD I DO GUYZ???  PLEASE!!

---

### Post by triplesick on 2009-08-12
also, i found the same problem the other guy found.  see new screenshot.

what can I do?

EDIT: even more details.  gparted reports all the space on my hard drive as being unallocated.

---

### Post by XxionxX on 2009-08-13
I sure hope that you have a windows disk handy because the only thing that I can think of is to do a clean windows(or Ubuntu) install. I also think that you should re-read the thread that you posted in your edit because it is [SOLVED] and his computer is fine and you seem to be under the impression that all is lost.

---

### Post by triplesick on 2009-08-13
> **XxionxX said:**
> I sure hope that you have a windows disk handy because the only thing that I can think of is to do a clean windows(or Ubuntu) install. I also think that you should re-read the thread that you posted in your edit because it is [SOLVED] and his computer is fine and you seem to be under the impression that all is lost.

Thank you for replying.  I've solved the problem.  I actually got out the Windows disk, and my computer was so fscked up that even the Windows disk crashed.  The guy in that thread didn't really solve it--he just sort of cut his losses and decided to just use Ubuntu.  But I've solved it.  The solution doesn't make any sense, but it's really easy:

1. Turn off computer.
2. Press the MediaDirect button again.
3. Blue screen of death.
4. Turn off computer.
5. Press MediaDirect button.
6. The bootmenu appears superimposed over the MediaDirect application.  Choose to boot to windows.  Magically, Windows works fine, and MediaDirect has cleaned up its mess.
7. Never press the button again.

Further, I don't think I'm ever going to turn my computer off again.  Or look at pornography again.  Or use bad words again.  And I'll go to church every Sunday, and help old women across the street.  Man, I'm so glad.

---

### Post by XxionxX on 2009-08-17
I hope that your computer never does that again!

---

### Post by triplesick on 2009-08-21
Thank you for the support XxionxX!

---

