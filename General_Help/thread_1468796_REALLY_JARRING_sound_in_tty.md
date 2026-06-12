---
title: "REALLY JARRING sound in tty"
date: 2010-05-01
forum: General Help
---

### Post by vik_2010 on 2010-05-01
Whenever I open a tty, if I push backspace at an empty prompt or tab to auto-complete an unfinished word, my computer makes the most excruciating sound - like nails rending a blackboard, or something being ripped apart violently - and loudly.

What the hell is this, and how do I get rid of it? It doesn't occur in psuedo-terminals - only in the main ttys.

Thanks

---

### Post by vik_2010 on 2010-05-01
I just discovered that the sound is also produced when I restart the computer.

To clarify, it is a harsh, metallic sound emitted for about 1/4th of a second, like a trombone suddenly blown in ones ears.

Thanks.

---

### Post by WorMzy on 2010-05-01
Is it coming from your speakers, or from inside your PC chassis? If it's from inside the chassis, it's probably your internal speaker (primarily used for reporting error codes in the event of a display problem), you might be able to disable that in your BIOS, although it might be better to figure out what the problem is, and fix it. I can offer no advice on that matter, since my PC don't have an internal speaker, so I've never had problems with one.

---

### Post by vik_2010 on 2010-05-01
It's a laptop without separate speakers, so it's kind of hard to tell. But it certainly doesn't sound like it's been produced by moving parts grating against each other or anything - more like an error sound - like you would hear on a game show if someone gave a wrong answer, except harsher.

---

### Post by vik_2010 on 2010-05-02
I've read around, and I think the sound is from the pcspkr. But the things I've tried haven't gotten ride of it.

The advice I've read says to add "blacklist pcskr" to a file blacklist.conf (which I created) in my /etc/modprobe.d directory. I also typed in 'sudo initramfs -u' to make that change permanent. But I still have the sound. 

Anyone know how to solve this?

---

### Post by vik_2010 on 2010-05-02
I just solved this. I had turned on pcspkr in alsamixer.

---

