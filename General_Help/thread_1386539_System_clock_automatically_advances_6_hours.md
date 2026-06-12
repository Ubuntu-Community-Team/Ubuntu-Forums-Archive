---
title: "System clock automatically advances 6 hours"
date: 2010-01-20
forum: General Help
---

### Post by lereveur on 2010-01-20
Hi! :)

I've been frustrated with several problems I've been experiencing with Karmic Koala. The one I'll mention in this post is the fact that it randomly decides to adjust the system clock ahead 6 hours. I believe this began happening when I set the location for the system time that displays in the top panel. I'm guessing that the 6 hours is the fact that I'm in the US Central Time zone.

---

### Post by blueridgedog on 2010-01-20
Could it be that your hardware clock is off?

What is the output of 

```
date
```

and

```
sudo hwclock

```
(run close together to compare times).

You can set you hardware clock to the system clock with:

```
hwclock --systohc
```

---

### Post by lereveur on 2010-01-26
Thanks for your reply. I decided to re-install Ubuntu. I did have a boot problem that I hadn't finished fixing. I had also noticed that Fish Life in Facebook was running slowly. Perhaps it was a bug in Fish Life or maybe whatever was affecting my clock was affecting Fish Life. So far the new install isn't having the problem. This time I have the clock being updated via the Internet. I don't have all the apps installed that I had previously nor all the Firefox addons or Chrome addons. So we'll see. Fish Life is back to normal speed. I'll update if it happens again.

---

### Post by ajlec2000 on 2010-01-28
I have a similar problem. However my computer jumps 8 hours ahead. I'm in the Pacific time zone two hours difference from Central time. I'm using a dual boot with Puppy 4.31. Puppy was installed first along with Grub 1.97 two months before Karmic and during that time Puppy kept the time accurately. After 9.10 was installed both OSs jump ahead 8 hours.

---

### Post by llawwehttam on 2010-01-28
Just wondering if you guys are using ntp servers to set your system clocks. If you have bad settings somewhere you may get problems. Personally I have never seen this problem.

---

