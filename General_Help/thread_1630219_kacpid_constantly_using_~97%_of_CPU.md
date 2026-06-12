---
title: "kacpid constantly using ~97% of CPU"
date: 2010-11-24
forum: General Help
---

### Post by dEXm on 2010-11-24
Kacpid is taking up a ridiculous percentage of my CPU. I've seen screens of other people's top process list and it seems that this is absolutely not normal. 

Here's an image of top:
[http://img221.imageshack.us/img221/7074/screenshot1wy.png]("http://img221.imageshack.us/img221/7074/screenshot1wy.png")
Kacpid is at the top there.

I've got Ubuntu 10.10 (installed using Wubi). 
This issue starts as soon as startup; it's not triggered by me running any specific events, plugging in devices, etc. and I've been experiencing this since installation.

I'm running it in 64 bit, though I think it's unrelated to the issue at hand. Then again, might as well mention it. You never know.

Load across all CPUs:
[http://img3.imageshack.us/img3/4227/screenshot2nph.png]("http://img3.imageshack.us/img3/4227/screenshot2nph.png")
CPU 1 constantly fluctuates between 80% to about 95%.

If anyone could help me that would be greatly appreciated :)

---

### Post by cgroza on 2010-11-24
Ever tried killing it?

---

### Post by dEXm on 2010-11-24
How would I go about doing that?
It doesn't appear in System Monitor.
A permanent fix is preferred, naturally :P

edit:

It says that the operation is not permitted.

---

### Post by dEXm on 2010-11-26
Sorry for the bump, but I'd really like to get this fixed.
Any ideas at all? (apart from kill process)

---

### Post by _Duhhh on 2010-11-29
I had the same problem on my HP 8740w. [This]("http://www.connect-utb.com/index.php?option=com_content&view=article&id=488:kacpid-eating-up-your-cpu-on-one-thread-fix-here&catid=45:linux-news") post solved the problem for me.

I hope it works for you!

---

### Post by dEXm on 2010-11-29
> **_Duhhh said:**
> I had the same problem on my HP 8740w. [This]("http://www.connect-utb.com/index.php?option=com_content&view=article&id=488:kacpid-eating-up-your-cpu-on-one-thread-fix-here&catid=45:linux-news") post solved the problem for me.

I hope it works for you!

I've got an HP 8540w, so it's a BIOS problem after all.
I added that line to rc.local but it doesn't seem to be changing anything. Is there a specific place I need to add it to in the file, do I also need to add a '#' in front of it?

In any way, thanks for the info, now I at least know where the root of the problem is :)

edit: I performed the change described here: [http://maltekueppers.de/wp/?p=1475]("http://maltekueppers.de/wp/?p=1475") 
Now everything is working perfectly :D I found that guide via the website you linked me _Duhhh so thanks a lot man!

---

### Post by Ruesca on 2010-12-17
Thx a lot, this link was very helpfull!

An other page that helped me a lot to work around bugs (dimming, suspending) of a HP Elitebook 8540w was:[ http://www.linlap.com/wiki/hp+elitebook+8540w]("http://www.linlap.com/wiki/hp+elitebook+8540w")

- cheers

---

