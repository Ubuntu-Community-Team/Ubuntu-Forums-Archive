---
title: "Random, complete crashes, only in ubuntu, win7 works fine!!"
date: 2011-07-06
forum: General Help
---

### Post by StartedTheFire on 2011-07-06
I've been having this problem for a while now. This might get kind of long but please bear with me because I have no idea what to do.

I installed ubuntu a while ago on this computer, I think I started with 9.10, and it ran perfectly for over a year. But a few months ago it started randomly crashing, with no warnings or messages whatsoever. It behaves exactly as if it had simply been unplugged. When it does this, the power light starts blinking orange and i t refuses to turn on until I unplug it and plug it back in. Sometimes it will run fine for hours but once it starts doing this it will not stay up for more than 10 minutes at a time until left off overnight.

Sounds like it's just overheating, but it gets weirder. I started using lm-sensors and a frontend that runs in the panel. I found that my GPU was getting up to 82 degrees celsius so I got a new one. Now it stays below 50. But the problem persists, in exactly the same way (although my graphics are much better since it's no longer underclocking itself to avoid exploding.) I have since upgraded to 11.04 from 10.10 which I was too lazy to do before (I don't use unity) and even done a full reinstall, and it seems to have gotten a bit less frequent but the problem itself is still here.

But here's the REALLY WEIRD part. I dual-boot with Windows 7 and I have never, EVER experienced this problem running it. I haven't looked at the temps while running windows but before I got my new GPU I could play TF2 on it fine, without obvious underclocking and low FPS, which indicates that the GPU was remaining at a decent temp. That means that playing a modernish, fully 3D game under Windows stressed my GPU less than just viewing the desktop under Ubuntu!

Does Ubuntu just have poor hardware support for my computer? But if that's true then why did it start happening at a specific time after running fine under 10.10 for months?

Googling hasn't found anything much like my problem, but I have seen some people with sort of similar problems saying to run some memory testing program. But why would my memory- a piece of hardware- have gone bad for one OS but not for another?


Please help me guys. You're my only hope!

---

### Post by An Sanct on 2011-07-06
Well, what does ```
dmesg
``` give you? Have you checked what the logs say - it might be something concerning standby or suspend modes ... or anything, check the logs in the "log file viewer"

[The ram is utilized in a different way for Linux]("http://www.linuxatemyram.com/") ... IMHO check it ;)

---

### Post by StartedTheFire on 2011-07-06
How do I check the logs? Sorry but I just have no idea where this information would be.

---

### Post by Potters Son on 2011-07-06
Logs can be read from System > Administration > Log File Viewer

---

### Post by StartedTheFire on 2011-07-06
Jeez sorry but all I get is nonsense. All I see in the boot log and dmesg are repetitive listings of my hardware with hexidecimal addresses. I see no blaring lines that say "error" or anything.

---

### Post by StartedTheFire on 2011-07-17
Now I'm getting the same error on my new, COMPLETELY UNRELATED laptop. Maybe it has to do with the install disk? But it was happening under 10.10 too.

This is annoying!

---

### Post by wildmanne39 on 2011-07-17
> **StartedTheFire said:**
> Now I'm getting the same error on my new, COMPLETELY UNRELATED laptop. Maybe it has to do with the install disk? But it was happening under 10.10 too.

This is annoying!
Hi, ok give as some information so maybe we can help you.
```
sudo lshw
```
```
lsmod
```
```
lspci | grep VGA
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.

---

