---
title: "Sudden problem with sound/soundcard"
date: 2006-02-27
forum: General Help
---

### Post by pppetter on 2006-02-27
Hi there everyone!

Just a few minutes ago, when I logged out and then in again, I suddenly couldn't play any sound. My soundcard is still in HAL. And I have tried to test with ESD, ALSA, OSS, Artsd. But nothing worked. I don't have a clue of whats wrong - or what info I should give you. The sound card also seem to have dissapeared from the sound preferences app. Maybe if I could add it there in some conf file or something. 

Help appreciated! :)

---

### Post by ironmaiden6669 on 2006-02-27
I don't know much about this stuff yet, but I read a command somewhere;
killall:artsd
Not sure if I got the syntax right but I think this kills the sound server.
Rebooting after that should start up the sound server again.
You'll want to run a search or something on this before you try it because I could be wrong.
:confused:

---

### Post by pppetter on 2006-02-27
that didn't help, since I don't really have such a process running. I have tried to restart my computer, and restart alsa-utils but neither helped. I don't really know what's wrong :(

---

