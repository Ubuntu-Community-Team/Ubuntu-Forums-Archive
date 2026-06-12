---
title: "Program stealing my sound"
date: 2011-05-01
forum: General Help
---

### Post by mitk0o0o0 on 2011-05-01
I'm having a weird problem that i have only noticed RuneScape client causing it.

It's like this:
If I firstly run RuneScape client, then start a video on VLC, it won't have sound.
If i close RuneScape client the sound from VLC will come back.

A fix trick:
Run VLC first, then RuneScape client and i will have sound all the time no matter if restart VLC while RS client is on i still have sound.

It's like RS client somehow takes the spot. I don't remember making any changes, i just started my computer and i noticed this problem.

I wish i could try fixing this myself but when i open ALSA and PulseAudio i have absolutely no idea what to tweak.

Running Ubuntu 10.10 32bit, got GNOME Alsa Mixer installed also PulseAudio, but i had them for a long time before this started to happen so i doubt it's them.

Has anyone else encountered this?

---

### Post by mitk0o0o0 on 2011-05-02
bump

---

### Post by kostkon on 2011-05-02
Are you using Sun Java or OpenJDK to run Runescape?

---

### Post by mitk0o0o0 on 2011-05-02
> **kostkon said:**
> Are you using Sun Java or OpenJDK to run Runescape?I just checked Synaptic Package Manager and i seem to have both installed, i'm using their downloadable client so i think it's using OpenJDK or something.

---

### Post by kostkon on 2011-05-02
> **mitk0o0o0 said:**
> I just checked Synaptic Package Manager and i seem to have both installed, i'm using their downloadable client so i think it's using OpenJDK or something.
I'm asking this because Sun Java tends to take total control of the sound card and blocks the other software that tries to acccess it (dmix, pulseaudio, various applications).

This problem is especially prominent on systems with a sound card that doesn't have a hardware mixer.

---

### Post by mitk0o0o0 on 2011-05-05
> **kostkon said:**
> I'm asking this because Sun Java tends to take total control of the sound card and blocks the other software that tries to acccess it (dmix, pulseaudio, various applications).

This problem is especially prominent on systems with a sound card that doesn't have a hardware mixer.I see, but like i said, i still had both installed and was using the same client before this happened.

---

### Post by mitk0o0o0 on 2011-05-06
So any ideas for fixing this? I miss having my RuneScape sounds along with the others.

Weird thing is RuneScape doesn't have sound at all, yet it takes other application's.

---

### Post by mitk0o0o0 on 2011-05-07
Bump.

---

### Post by mitk0o0o0 on 2011-05-08
Anyone? This sucks. I've also tried the webclient through firefox and still, there's no sound.

---

### Post by markjensen on 2011-05-08
I had this happen when I upgraded from 10.10 to 11.4. The music in Runescape would sound, but not the normal game sounds (combat, spells, bank PIN, etc).

It is working on mine after doing two actions (and not sure which one was the fix, or if both were needed, as the kids had turned down my speakers - apparently they were using my computer last night).

First, on the Runescape main page, under "Play Now", you see "Java Options". Click that, and select "Force Sun Java", ignoring the "Internet Explorer Only" comment with it.

I also performed the steps from an existing UbuntuForums thread on this topic. Here is the post:
[http://ubuntuforums.org/showpost.php?p=9493360&postcount=6](http://ubuntuforums.org/showpost.php?p=9493360&postcount=6)

And it works.

---

### Post by mitk0o0o0 on 2011-05-08
> **markjensen said:**
> I had this happen when I upgraded from 10.10 to 11.4. The music in Runescape would sound, but not the normal game sounds (combat, spells, bank PIN, etc).

It is working on mine after doing two actions (and not sure which one was the fix, or if both were needed, as the kids had turned down my speakers - apparently they were using my computer last night).

First, on the Runescape main page, under "Play Now", you see "Java Options". Click that, and select "Force Sun Java", ignoring the "Internet Explorer Only" comment with it.

I also performed the steps from an existing UbuntuForums thread on this topic. Here is the post:
[http://ubuntuforums.org/showpost.php?p=9493360&postcount=6](http://ubuntuforums.org/showpost.php?p=9493360&postcount=6)

And it works.Oh finally! Thank you so much. :D

I first followed the instructions in the thread you mentioned, then before testing i also went on Firefox and chose "Force Sun Java" and when i started the client it now has sounds + it doesn't steal the other's sound anymore. :D

---

### Post by gylti on 2011-07-03
No sound effects in Runescape on natty or 10.10 on 2 different computers. Has anyone solved this? I thought I had but it stopped working as soon as I rebooted and wont work again now. 

Runescape music is awful and sound effects are essential to gameplay

---

### Post by mitk0o0o0 on 2011-07-20
Please help, i got an update for java and jdk and i clicked to update  them, i start the RuneScape client and again the same problem.

Followed the link markjensen gave me and the other steps but after that, no java application ever starts. I have re-installed sun-java and jdk and it's working now but no sound. 

Anyone got a new solution?

---

### Post by mitk0o0o0 on 2011-07-20
bump

---

### Post by mitk0o0o0 on 2011-07-21
Please, anyone? I almost died atleast 3 times cause of no sounds.. :/

---

