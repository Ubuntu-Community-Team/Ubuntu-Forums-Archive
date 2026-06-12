---
title: "How do I switch to the audio support that was in 9.04"
date: 2010-09-29
forum: General Help
---

### Post by ki4jgt on 2010-09-29
10.04 doesn't support my father's computer. I always have to switch between 4.1 surround sound and 5.1. After I change a song, or watch another video, it only plays static, then I have to go into sound preferences and change it again, until the next song. I didn't have this trouble in 9.04 on his computer. The problem now is, he actually replaced windows with Ubuntu this time, so he wants everything to work. So what software was installed in 9.04 and how do I get it to 10.04?

---

### Post by NT4usB on 2010-09-29
iirc, 9.04 uses alsa and 10.04 uses pulse.
I've read many posts about uninstalling pulse and inatalling alsa, usually preceeded by posts about how hateful pulse is to work with.
I'm going to try this (some day) to try and solve an mplayer issue...
ymmv. Suggest more reading first, unless you're experienced or just a 'go for it' type (like me...)

---

### Post by ki4jgt on 2010-09-30
I'm the go for it type while I'm reading how to do it. My cousin used to be the go for it guy, who never payed attention to what he was doing and never read anything. He never got anything done. He always told me instructions were for idiots.

---

### Post by P4man on 2010-09-30
What audio card is in that machine? Perhaps post the output of lspci or aplay -l.
And is it actually a 4.1 audio setup?


BTW, dont go trying to using old alsa drivers on a new kernel, or even disabling pulse audio before having made a proper attempt at solving it. You will likely introduce a whole new range of problems, and perhaps its trivial to fix it.

---

### Post by NT4usB on 2010-09-30
In support of the *try and fix it first, then throw it out* crowd... *g*

Spotted in the Ubuntu newsgroup. May or may not be related:
> 

I'm running Ubuntu 10.04 on a Mac Mini and I had to add the line

options snd-hda-intel model=imac24

to `/etc/modprobe.d/alsa-base.conf'. In your case it would be

options snd-hda-intel model=hp

For more info, have a look at

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)


/August 

---

