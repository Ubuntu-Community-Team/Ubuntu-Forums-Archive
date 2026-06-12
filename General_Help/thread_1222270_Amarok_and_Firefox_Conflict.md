---
title: "Amarok and Firefox Conflict?"
date: 2009-07-24
forum: General Help
---

### Post by dharvell on 2009-07-24
I've had a problem with Firefox crashing, ever since I switched from Vista to Kubuntu, about a month ago.  I used Firefox in Vista, without error, so imagine my disappointment when my favourite browser seemed to crash constantly with Kubuntu.

Hoping the latest, greatest version of Firefox would cure the problem, I downloaded and installed Shiretoko, version 3.5 of Firefox.  Sadly, the problem persisted.

Over the course of the past several weeks, I believe that I have discovered a connection between Amarok and Firefox.  It seems that, whenever I have Amarok open, Firefox crashes.  With Amarok closed (completely... not even in the system tray), Firefox seems to be extremely stable.

Has anybody else experienced this issue?  If so, is there a workaround, as I would love to be able to listen to music and browse the Internet, simultaneously.

Any and all assistance will be very much appreciated!

+dharvell

---

### Post by dharvell on 2009-07-24
Nobody has experienced this, then?

If you need additional information, just ask.  I'll try to give you what you need.

---

### Post by CatKiller on 2009-07-25
> **dharvell said:**
> Has anybody else experienced this issue?

'Fraid not. Firefox (3.0 & 3.5) have both been perfectly stable for me, and I often have Amarok open and playing music while I'm surfing t'Internet.

Running firefox (or firefox-3.5) from a Terminal will give you stderr output, which may help you diagnose what's causing your crash.

---

### Post by dharvell on 2009-07-27
Thanks.  I'll give it a shot.  

Another Amarok/Firefox conflict that I notice is, when Amarok is open, I lose all sound abilities in Firefox.  Conversely, when Firefox is open, Amarok does not play sound.  When one is closed, the other starts to work.

---

### Post by dharvell on 2009-07-27
UPDATE:  Opened Firefox from the console.  Nothing was output to the console when Firefox crashed, so that method of troubleshooting is a dead end.  Any other suggestions to solve this issue?

Thanks for the reply, CatKiller.  It was a good place to start!

---

### Post by ctalbertma on 2009-07-27
I have similar experiences. Firefox (3.0.12) running, and plays a YouTube video with sound. Amarok wouldn't work any more. Both crash; have to use force quit or kill to end them. Sometimes, the entire Hardy would have to be restarted...sometimes Hardy would not even shut down.

As long as they don't run simultaneously, firefox and amarok seem quite stable.

---

### Post by Vaphell on 2009-07-27
> **dharvell said:**
> Thanks.  I'll give it a shot.  

Another Amarok/Firefox conflict that I notice is, when Amarok is open, I lose all sound abilities in Firefox.  Conversely, when Firefox is open, Amarok does not play sound.  When one is closed, the other starts to work.

no sound as in youtube videos and such?
my bet would be flash conflicting with pulseaudio or something like that
I had such problem (no crashes though) with totem/rythmbox/vlc + FF but installing libflashsupport package fixed it. This fixes some issues with flash+pulse.
I use 8.04 and don't know if my guess is of any help in your case

---

### Post by ManyBeers on 2009-07-28
> **dharvell said:**
> Thanks.  I'll give it a shot.  

Another Amarok/Firefox conflict that I notice is, when Amarok is open, I lose all sound abilities in Firefox.  Conversely, when Firefox is open, Amarok does not play sound.  When one is closed, the other starts to work. This happened to me with Firefox and Rhythmbox. Try this Pulseaudio guide which fixes the problem:
[http://ubuntuforums.org/showthread.php?t=843012&highlight=markbuntu+pulse+audio]("http://ubuntuforums.org/showthread.php?t=843012&highlight=markbuntu+pulse+audio")

---

### Post by N0L3R on 2009-09-25
Hi there,
 I think that the solution lies by going to Computer --> System Settings then Multimedia and select Pulseaudio as the most preferred.

---

### Post by matyasfalvi on 2010-02-14
> **N0L3R said:**
> Hi there,
 I think that the solution lies by going to Computer --> System Settings then Multimedia and select Pulseaudio as the most preferred.

This worked for me! Thank You!

---

