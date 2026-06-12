---
title: "Audio Hiss in Ubuntu 9.10"
date: 2009-11-28
forum: General Help
---

### Post by nalencer on 2009-11-28
Hi all.

I just did a fresh install of Karmic over my old installation of 9.04. Everything works great thus far, except that there is an annoying, persistent audio hiss in the system sound. I have a surround system, and I've tried all of the different hardware options in the sound preferences with no luck. I'm dual-booting with Vista, the speakers sound fine when it's running, so I know it's not the sound system itself.

I'm kind of at a loss here. I've been reading about PulseAudio causing a lot of problems, but I'm not sure if it causes this type of problem as much as lagging sound, sound not working with certain apps, etc. Would it be worthwhile to try uninstalling PulseAudio? If so, what should it be replaced with? Does anyone have any other ideas as to what could be causing this issue?

Thanks in advance for any help.

---

### Post by nalencer on 2009-11-28
Anyone?

---

### Post by nyxerebos on 2009-11-28
I'm getting this too, along with annoying loud pops uring startup (2) / shutdown (1).

Just upgraded to 9.10 and am having more serious problems (gnome hangs intermittently) Will look into it and post solution if I find one, must get machine usable first.

---

### Post by NoaHall on 2009-11-28
WEll, the way to solve this to remove Pulseaudio... I have made a guide, but you shouldn't really move pulseaudio, as skype uses it.

---

### Post by nalencer on 2009-11-28
Well, if it's a choice between having terrible sound and not being able to use Skype (which I really don't use anyway), I'll take the latter. Can you post a link to your guide?

---

### Post by NoaHall on 2009-11-28
[http://usefulsoftwaregamesandknowledge.blogspot.com/2009/11/how-to-fix-sound-on-ubuntu-910karmic.html](http://usefulsoftwaregamesandknowledge.blogspot.com/2009/11/how-to-fix-sound-on-ubuntu-910karmic.html)

Note, the little sound volume thing won't be displayed on the task bar any more.

---

### Post by nalencer on 2009-11-28
Thanks, that did it. It may not be the most elegant solution, but until there's a choice whether to use PA out of the box I guess it's as good as it's going to get. Alsamixer makes life much easier after this. Thanks again.

---

### Post by NoaHall on 2009-11-28
Chances are, it'll break with a update soon, so when that happens, I'll post how to fix it too.

---

