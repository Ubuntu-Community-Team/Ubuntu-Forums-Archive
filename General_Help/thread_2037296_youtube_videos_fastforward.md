---
title: "youtube videos fastforward"
date: 2012-08-04
forum: General Help
---

### Post by micahpage on 2012-08-04
Within the last week or two, I have noticed that when i watch youtube videos...the audio and video, look and sound like they are fast forwarding. Only after about 20 seconds, they go back to normal again. So I have to wait it out until it goes normal, before actually watching the video.

I dont recall messing around with something in flash or whatever, so i am not sure why it would be doing this?

Has anyone else had this problem and/or knows of how to fix it.

ubuntu 12.04
gnome 3 desktop

---

### Post by aylovey on 2012-08-27
Had the exact same problem and was sick of having to restart my computer as a way of "fixing" it. Run 'top' and find the PID of pulseaudio. Run kill -s 9 <PID> replacing <PID> with that PID. Voila! It fixed the video fast forwarding problem.

---

### Post by Szor3n on 2012-08-27
Isn't it fun that the sound driver controls the flow of the video? Thanks flash! (happens on windows and OSX too)

---

### Post by drmrgd on 2012-08-28
It also seems to be Google Chrome related as I have not seen this happen once since I've switched back to Firefox.  I think it has something to do with how Google is implementing Pepper Flash.

---

### Post by micahpage on 2012-08-28
I eventually came up with the conclusion that it was a youtube only thing and their problem, except no one else seemed to have the problem...untill i read your posts.

I would agree that it is a google chrome thing, but just yesterday I had it happen with VLC also. I fixed the problem by just using another media player. Today I go back to VLC and its working fine. You tube is also currently working fine at the moment.

It's kind of odd as it happens 1/20 times with youtube and rarely happens with VLC. 

I cannot quite point my finger to the culprit.

> Had the exact same problem and was sick of having to restart my computer as a way of "fixing" it. Run 'top' and find the PID of pulseaudio. Run kill -s 9 <PID> replacing <PID> with that PID. Voila! It fixed the video fast forwarding problem.
Is this a permanent fix or a one time thing. REgardless next time it happens I will try this

---

### Post by aylovey on 2012-08-29
Ever since I did that I haven't had the problem again. Granted it was less than a week ago but it's a better solution than constantly restarting.

---

### Post by micahpage on 2012-08-29
I actually never restarted the system to specifically fix this problem. Over a course of an hour or two it fixes itself without me doing anything. 

It ones of those things I'm like: "whatever"

---

