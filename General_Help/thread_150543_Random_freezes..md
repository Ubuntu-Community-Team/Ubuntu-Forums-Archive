---
title: "Random freezes."
date: 2006-03-26
forum: General Help
---

### Post by Randomskk on 2006-03-26
Heya
I'm running Ubuntu 5.10, upgraded to Kubuntu with kubuntu-desktop, and betas of some apps - Konversation, amaroK and a few others.

Starting today, I've had two random freezes now - seemingly nothing's prompted them, and I've looked in /var/log to no avail (couldn't see anything applicable)

The freeze just COMPLETELY freezes the system, and it doesn't respond to anything (music stops dead, not just loops a few seconds worth over and over).

I've no idea what causes it, but it needs a hard restart - and I noticed that the disk doesn't get checked on boot, either, as though I shut down instead of crashed.
Any ideas what's starting it/how to stop it happening/how to find out what's causing it?

Thanks

---

### Post by eriefisher on 2006-03-26
I've been trying to figure this out as well. My problem seems similar but sometimes everything just disappears and I'm left with my desktop wallpaper.
I can't find any errors anywhere. I'm starting to think this is a bug with KDE.

eriefisher

---

### Post by Randomskk on 2006-03-26
I should mention I'm on KDE 3.5.1, I upgraded using a guide in the forums.

---

### Post by eriefisher on 2006-03-26
Same here. But I used Kubuntu-desktop and Kde in synaptic. Everything shows as 3.5.1.

---

### Post by CyberRaven on 2006-04-05
Have any of you guys had any luck figuring this out? I'm experiencing the same symptoms as described by **Randomskk**. I'm running Kubuntu 5.10 too, but with KDE 3.5.2.

Any tips would be greatly appreciated!

/CyberRaven

---

### Post by Randomskk on 2006-04-05
Funny - after I upgraded to KDE 3.5.2, the freezes seem to have stopped. Still not sure what was causing them.

I'd check you're fully upgraded - *just* before going to 3.5.2 I got a new kernal and a load of other updates via apt, so run apt-get update, upgrade to check you're fully updated.

---

### Post by Asraniel on 2006-04-05
a friend of mine has exactly that problem with current dapper. full upgrades. which log messages should i check to find out whats causing it?

---

### Post by enfield on 2006-04-05
I've had the same problem recently.  I made a change today and, if it fixes the problem, I'll share it with you.  Fingers crossed!:)

---

### Post by EisenPM on 2006-04-10
same problem here. with kde 3.5.1 and 3.5.2. all updates done with adept updater. but it seems as if it only happens when amarok is playing music. no matter which version.

do your freezes also appear when there's no amarok running?

---

### Post by Randomskk on 2006-04-10
That's true - mine only happened with amaroK loaded, but I have amaroK loaded all the time.
My amaroK 1.4beta3 doesn't seem to crash, though, and I haven't experienced any crashes recently (KDE 3.5.2, latest kernal, amaroK 1.4beta3, ATI's latest drivers)

---

