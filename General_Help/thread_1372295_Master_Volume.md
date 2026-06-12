---
title: "Master Volume"
date: 2010-01-04
forum: General Help
---

### Post by warfacegod on 2010-01-04
I would like, if possible, to change the % that the Master Volume goes up by. For instance, if I hit the volume up button on my key board, it goes up by 6%. I would prefer it to be 1% or even .5%.

I tried posting this in Multimedia yesterday but didn't realize until today that it never actually posted. Is that a common thing? It's happened to me before.

---

### Post by Brandon Williams on 2010-01-04
> **warfacegod said:**
> I would like, if possible, to change the % that the Master Volume goes up by. For instance, if I hit the volume up button on my key board, it goes up by 6%. I would prefer it to be 1% or even .5%.

That's probably not possible. Most sound cards don't allow such fine granularity. But you can probably do better than 6%.

You can use amixer to figure out what granularity is possible.

```
$ amixer get Master
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 42 [57%] [-32.00dB] [on]
  Front Right: Playback 42 [57%] [-32.00dB] [on]
```

This shows me that the range for my sound card's Master channel is 0 to 74, which means that the best I can get is about 1.4% granularity. On another one of my computers, the range is half that. Before you spend much more time trying to figure out how to change the scale, make sure that your sound card really can do better.

As for getting better behavior, I use Xubuntu, but the way to do it in Xfce might be similar to Ubuntu. With Xfce, I open the settings editor (Xfce's equivalent of gconf-editor) and there is a setting for xfce4-mixer called volume-step-size. On my system, it defaults to 5, which means I'm getting about 7% granularity.

---

### Post by warfacegod on 2010-01-04
Thanks for replying.

```
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 63 [100%] [0.00dB] [on]
  Front Right: Playback 63 [100%] [0.00dB] [on]
```


This is what it gave me. Now what?

---

### Post by Mr Nemo on 2010-01-04
Bump for possible solution?

---

### Post by warfacegod on 2010-01-05
Bump. I feel like I'm so close but still so far away!

---

### Post by Leppie on 2010-01-05
open gconf-editor:
```
$gksudo gconf-editor
```
go to Apps –> gnome_settings_daemon –> volume_step

---

### Post by warfacegod on 2010-01-05
> go to Apps –> gnome_settings_daemon –> volume_step 

Thanks! for replying unfortunately, this didn't work.

---

### Post by warfacegod on 2010-01-05
Correction, it did work. On a hunch, I went into the config editor without root privileges, just under regular user mode, and the value hadn't changed. I changed it to 1 and it worked. I think what happened was using root privileges adjusted it for root and not me.

Thanks for the help. This has been irking me for years.

---

### Post by Leppie on 2010-01-05
haha, that sounds logical, hadn't thought of that. i'm a noob too...
well, good it's working now :)

---

### Post by warfacegod on 2010-01-05
> haha, that sounds logical, hadn't thought of that. i'm a noob too...

I disagree. I've seen many of your posts, the quality of your advice is far above noob level. Although, on some level, with Linux everyone's a noob. Keeps things fresh that way.

On an aside; why the *hell* does the spell check in the reply window insist that Ubuntu (see! it did it again!) is spelled incorrectly.

This is an Ubuntu site!

---

### Post by hariks0 on 2010-01-05
> **warfacegod said:**
> 

...why the *hell* does the spell check in the reply window insist that Ubuntu (see! it did it again!) is spelled incorrectly.

This is an Ubuntu site!

Because under Linux ubuntu is not Ubuntu. It is CaSe SeNsItIvE man !:P

---

### Post by warfacegod on 2010-01-05
If it's so case sensitive, then why does _*ubuntu*_ also comes up incorrect? Huh?

---

### Post by Leppie on 2010-01-05
> **warfacegod said:**
> I disagree. I've seen many of your posts, the quality of your advice is far above noob level. Although, on some level, with Linux everyone's a noob. Keeps things fresh that way.
thanks for the compliment, hope some of it was useful for you as well. but really, i'm still a beginner in linux...

---

### Post by warfacegod on 2010-01-05
> hope some of it was useful for you as well.

Yeah! This one!

---

### Post by Leppie on 2010-01-05
> **warfacegod said:**
> Yeah! This one!
kewl :)

---

### Post by Mr Nemo on 2010-01-05
Thanks Leppie, i've been trying to figure this out for a while. Also thanks to Warfacegod for starting this thread.

---

### Post by hariks0 on 2010-01-05
> **warfacegod said:**
> If it's so case sensitive, then why does _*ubuntu*_ also comes up incorrect? Huh?

I was just joking. It is only a Firefox Dictionary entry. You have to right click on Ubuntu to add to dictionary of Firefox once. Then if you type _u_buntu it will red underline and _U_buntu will be accepted.

---

### Post by warfacegod on 2010-01-06
I was too. It didn't occur to me that it was fire fox not the site. Duh! I spell it with upper and lower case depending on how lazy I'm feeling so I'll add both. Thanks.

I love it. This isn't the first thread I've started where I get more responses after I solve it than before. Ha! Ha!

---

