---
title: "I can't adjust my Monitor refresh rate"
date: 2011-10-22
forum: General Help
---

### Post by GPmatic on 2011-10-22
I'm running Xubuntu 11.04 and everything thing is working fine apart from the fact that I can't adjust the refresh rate of my monitor at all. I have an Acer X163w. The resolution is no problem but I see no option in my "Display" settings to change my refresh rate. I'm still a bit new so I don't really know my way around this OS yet.

---

### Post by gsmanners on 2011-10-22
Really? That's been a feature in the Settings / Display for at least since Xfce 4.6 (in between Resolution and Rotation).

---

### Post by GPmatic on 2011-10-22
> **gsmanners said:**
> Really? That's been a feature in the Settings / Display for at least since Xfce 4.6 (in between Resolution and Rotation).
I know but there is no option to lower or increase the refresh rate. I have attached a photo to show what I mean. 
[http://twitpic.com/74bzg4](http://twitpic.com/74bzg4)

---

### Post by gsmanners on 2011-10-22
Hmm... What does this return?

```
lspci | grep VGA
```

---

### Post by GPmatic on 2011-10-22
> **gsmanners said:**
> Hmm... What does this return?

```
lspci | grep VGA
```
When I typed the code that you gave me in the terminal I got this message

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

what does it mean?

---

### Post by gsmanners on 2011-10-22
Integrated Intel video. It basically means you have a nice card for anything but serious 3D apps or games. I'm not sure how good the driver is for stuff like supporting varying refresh rates.

---

### Post by GPmatic on 2011-10-23
> **gsmanners said:**
> Integrated Intel video. It basically means you have a nice card for anything but serious 3D apps or games. I'm not sure how good the driver is for stuff like supporting varying refresh rates.
Oh I see, just to point it out, I'm not experiencing any problems concerning video playback or any other video card related problems. I just found it weird that I wasn't able to change my refresh rate, but I will still accept any help I can get. Thank you for you help sir.

---

### Post by gsmanners on 2011-10-23
Sorry, I couldn't help you out, but refresh rate is not something you need to worry about nowadays. Maybe ten to twenty years ago, but...

---

### Post by GPmatic on 2011-10-23
> **gsmanners said:**
> Sorry, I couldn't help you out, but refresh rate is not something you need to worry about nowadays. Maybe ten to twenty years ago, but...
Thanks anyway, have a good one.

---

