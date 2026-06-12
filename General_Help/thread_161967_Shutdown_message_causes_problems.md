---
title: "Shutdown message causes problems?"
date: 2006-04-18
forum: General Help
---

### Post by louis_nichols on 2006-04-18
Hi everybody!

I'm a pretty curious guy when it comes to my Linux (I guess that's what makes some of us Linux users, right?) so I do all kind of changes all the time, without always keeping detailed track of them.

Anyways, at one point, I started noticing a new message at shutdown, without knowing when it showed up. It says:

```
/etc/dbus-1/event.d/20hal line4:kill (8193) - No such process
```

It was (is?... read along!) harmless enough. It wouldn't always show up, but most of times, then, at next boot, things were ok in any case. So I didn't give it much thought.

But today the weirdest thing happened. I booted my PC and X server wouldn't start. It was saying smth about the monitor, that it was found, but not usable (I was too mad to remember everything). I tried a few things, but the whole situation got back to normal only after I reinstalled the nvidia driver.

So... what I'm asking is: does anyone know what this message might mean? More importantly: could it have smth to do with the X server crashing today?  Other than this, I don't really care about that shutdown message. I took a peak in the file 20hal, but things there don't make much sense to me.

---

### Post by jamesdodd on 2006-04-18
I have a few "No such process" on my shutdowns

But this is only because the process was never started.

The appeared when I disabled a few of the startup things (bluetooth, PCMCIA and a few other things I didn't need).



Would I be right in thinking that your message started appearing after similar tweeks

---

### Post by louis_nichols on 2006-04-18
hm... :-k 

I installed the rest of kde base system at one point (I had been using kde apps anyways, so this wa s a minor step.)

It might be the bluetooth drivers, cuz I don't use bluetooth, but they are installed by default with kde. Although I didn't make any changes regarding bluetooth within kde. All I did, when I first installed Breezy, was to uninstall everything related to bluetooth that had come by default.

But is there a way to find out specifically which process it's talking about?

---

