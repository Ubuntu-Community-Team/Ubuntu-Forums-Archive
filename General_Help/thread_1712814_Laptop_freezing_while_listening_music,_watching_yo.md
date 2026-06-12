---
title: "Laptop freezing while listening music, watching youtube videos etc."
date: 2011-03-23
forum: General Help
---

### Post by pericd on 2011-03-23
Hello people,
as you can see I'm new here and I need a little bit of help, or unless an opinion.

My laptop configuration:
HP 6715s
2GB RAM
ATI X1250 graphic card
AMD 64-BIT processor
160GB HD
etc.

I'm using Ubuntu 10.10 (intensively) for few months and having issues with laptop freezing mostly when i'm listening music or watching youtube videos + doing other stuff (having few tabs opened in Chrome, some office document, programs like Eclipse etc). All in all, with all those processes I'm using max 800MB RAM and CPU is also under 40% of capacity.
Sometimes even works fine but when it starts to freezing, i must cancel even music or video and then it'll again work fine, like nothing happened.

I've tried to edit grub, adding noapic etc but no results.

I've also tried Linux Mint (I know it's very similar to Ubuntu) and OpenSuse but I've also had the same problems...

While I'm asking this, I'm also having one new issue:
I've made an update to Ubuntu 11.04 alpha 3 (never mind that now) and my laptop won't reboot or shutdown properly. If I send a reboot/shutdown signal from ubuntu, it'll start to shutdown and then it will freeze after "outro" screen. After that, cd drive it's just clicking like it's trying to load a CD and here is where I must power off manually.
Interesting thing is that when i power on laptop it will work and it will boot to ubuntu correctly, but as i said, when i send a shutdown/reboot signal directly from ubuntu, it won't work.

---

### Post by arif920629 on 2011-03-23
Do you have swapspace?

---

### Post by pericd on 2011-03-23
Yes...2GB I think (I'm not working on a laptop right now)

---

### Post by arif920629 on 2011-03-23
From what I know your swap space should be twice your RAM size. I'm also a noob to this forum =D

Edit: Also I think your RAM is not exactly 2GB as your GPU is using it as shared memory(256MB I think)

---

### Post by pericd on 2011-03-23
> **arif920629 said:**
> From what I know your swap space should be twice your RAM size. I'm also a noob to this forum =D

Hm...I hear about that for the first time. I'll try to find out more about that.

---

### Post by Mark Phelps on 2011-03-23
If you've upgraded to 11.04, you need to post your problem in the Natty --> Development forum, not here.  This forum is for Released versions of Ubuntu.

As to the freezing, while watching Youtube videos is understandable, unless you're streaming audio realtime, you should be able to listen to music without problems.

However, if you're streaming audion realtime, since both actions involve streaming across the Internet, I would suspect network problems.

---

### Post by pericd on 2011-03-23
> **Mark Phelps said:**
> If you've upgraded to 11.04, you need to post your problem in the Natty --> Development forum, not here.  This forum is for Released versions of Ubuntu.

As to the freezing, while watching Youtube videos is understandable, unless you're streaming audio realtime, you should be able to listen to music without problems.

Yes, normally, I would be able to listen without problems, I really don't know what's the point.

Now I'm again running 10.10, i've just tried 11.04 in hope that some of my problems will be fixed. 
I must mention that after reinstalling ubuntu I don't have anymore that issue with rebooting. Also, I must say I've increased my swap space to 4GB but it's still the same problem...

---

