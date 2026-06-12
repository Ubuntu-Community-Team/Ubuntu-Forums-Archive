---
title: "Need help with timing. Sound problems."
date: 2006-02-22
forum: General Help
---

### Post by Fred Doolie on 2006-02-22
I'm having a problem with sound in my browser (Firefox) when I click on a streaming media link. Right now I'm using the sound extension that plays a liitle sound when you click on a link, when downloads finish and when a popup gets blocked. The problem is when the sounds are off the media plays fine. When the sounds are on the mediaplayer comes up just a hair before the click sound finishes and I get no media sound. It's like the system  is saying "The sound card is busy. You can't have it." How can I fix that besides not playing sounds in the browser?  The problem seems to be universal. If any sound is playing and another thing starts up the second thing will be silent or the system will lock-up.

Linux isn't suppose to lock-up I thought.

---

### Post by Fred Doolie on 2006-02-22
Oop. I ended too soon. With sound in the browser off everything plays fine. So I think it's a sound setup timing problem perhaps.

I tried "killall esd" but then I lose system sounds.

I tried
[esd]
auto_spawn=0
spawn_options=-terminate -nobeeps -as 2
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options= -terminate -nobeeps -as 2 

but it didn't make any difference.

---

### Post by drop_d33 on 2006-02-22
yeah i noticed that same problem too. when i play audio files on xmms and on a certain coincidence when a track ends and by the fate of luck a sound from some other program comes up, xmms wont be able to play the next track, saying  that another program is using the sound card. im pretty much annoyed by this problem. any solution to this anyone?

---

