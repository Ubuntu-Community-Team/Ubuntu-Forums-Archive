---
title: "ticking sound in ubuntu 9.10"
date: 2009-11-01
forum: General Help
---

### Post by fouadk on 2009-11-01
hi everyone...

i have installed a fresh copy of ubuntu 9.10..
im having a single problem which i never had in previous ubuntu releases which is the following...everytime i try to play an mp3 file or anything that generates sound, i hear a ticking sound before and after the sound...

the ticking sound also appears sometimes for no specific reason even though music or warning tone is being played.

my machine is an hp pavillion dv6500

please help
thanks in advance.

---

### Post by zzzBrett on 2009-11-01
> **fouadk said:**
> hi everyone...

i have installed a fresh copy of ubuntu 9.10..
im having a single problem which i never had in previous ubuntu releases which is the following...everytime i try to play an mp3 file or anything that generates sound, i hear a ticking sound before and after the sound...

the ticking sound also appears sometimes for no specific reason even though music or warning tone is being played.

my machine is an hp pavillion dv6500

please help
thanks in advance.
I also hear a tick sound before (maybe after) the speakers play any kind of sound.  Especially noticeable when the new email sound plays.

---

### Post by peculiar penguin on 2009-11-01
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008239.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008239.html)

You could try setting the power_save option mentioned to 0, which should disable this behaviour.

---

### Post by fouadk on 2009-11-01
thanks a lot peculiar penguin but setting power_save to 0 did not fix it....and i am pretty sure its not the ticking sound of new emails...

amy other suggestions ?

---

### Post by zzzBrett on 2009-11-02
peculiar penguin: worked perfectly for me, thanks.

fouadk: It wasn't the sound of new emails, it was the sound of the speaker amp starting up whenever a sound was about to play, more like a 'tick' as you described.

Maybe you have a different problem, though.

---

### Post by fouadk on 2009-11-02
what kinda machine you have zzzBrett ???

---

### Post by alanrr_sr on 2009-11-02
Try this thread and reboot.
[http://ubuntuforums.org/showthread.php?t=1311206&highlight=power_save](http://ubuntuforums.org/showthread.php?t=1311206&highlight=power_save)

---

### Post by fouadk on 2009-11-02
weird...that fixed it even though i tried this solution before....thanks a lot anyway

---

### Post by zzzBrett on 2009-11-02
I guess its not relevant anymore, but its a machine I built, no particular manufacturer.  Glad you got it working. Don't forget to mark as solved.

---

