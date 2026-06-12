---
title: "Sudden problem in karmic koala - blank screen at bootup (not installation)"
date: 2012-02-29
forum: General Help
---

### Post by kismul on 2012-02-29
I have an oldish dual boot desktop PC (eMachines P4, 256kRAM), with Windows XP and Karmic Koala.  It's always (mostly) worked fine.

On Tuesday night, it was working fine when I closed down.  On Wednesday, when I switched on, I got problems.  The menu comes up, where I can choose either to boot into windows or ubuntu.  When I choose Ubuntu, I first get the small ubuntu logo in mid screen, then nothing.  A dark blank screen.  I have left it for a while (more than an hour) but nothing happens.  I have top reboot by switching off and back on.

I've tried Windows and it boots up fine, which perhaps suggests to me that it's not a hardware problem.  Anyone got any ideas  on what could cause such a sudden and unexplained problem?  And how to solve it, of course. :(

---

### Post by kismul on 2012-02-29
Just had a thought.  Tried rebooting in alternative mode (where you see the boot code).  The booting sequence always stops at the same place.

I took a photo of the screen (attached) which shows the sequence of commands - hopefully, this will mean something to someone.  I'd be grateful for any advice.

(PS I'm currently accessing this from a live 10.0 distro), which seems to boot up quite happily).

---

### Post by kismul on 2012-03-02
> **kismul said:**
> Just had a thought.  Tried rebooting in alternative mode (where you see the boot code).  The booting sequence always stops at the same place.

I took a photo of the screen (attached) which shows the sequence of commands - hopefully, this will mean something to someone.  I'd be grateful for any advice.

(PS I'm currently accessing this from a live 10.0 distro), which seems to boot up quite happily).


Still haven't managed to resolve this so ANY help would be gratefully received.

---

### Post by raja.genupula on 2012-03-02
I have got something for you

[http://ubuntuforums.org/showthread.php?p=9863783](http://ubuntuforums.org/showthread.php?p=9863783)

---

### Post by kismul on 2012-03-02
> **raja.genupula said:**
> I have got something for you

[http://ubuntuforums.org/showthread.php?p=9863783](http://ubuntuforums.org/showthread.php?p=9863783)

Thanks for the suggestion.  I'll follow it up this evening and see if it resolves the problem.

---

### Post by kismul on 2012-03-03
> **raja.genupula said:**
> I have got something for you

[http://ubuntuforums.org/showthread.php?p=9863783](http://ubuntuforums.org/showthread.php?p=9863783)


Well, I followed the instructions in the thread you linked to and it, after a few false starts, it worked and I'm back and working.   Seems it was a kernel problem, though why it should have happened is a mystery.  

Many many thanks for your help.

For anyone else with the same problem in the future, note that you need to be in root and you should start with "su" to get you there.  First time I tried it, I hadn't done this and couldn't get anything to work.

---

### Post by raja.genupula on 2012-03-03
Thanks for appending some more useful information.

---

