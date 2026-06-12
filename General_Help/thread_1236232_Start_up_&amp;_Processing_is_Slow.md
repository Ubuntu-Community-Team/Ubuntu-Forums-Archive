---
title: "Start up &amp; Processing is Slow"
date: 2009-08-10
forum: General Help
---

### Post by rawfool on 2009-08-10
I'm using Ubuntu 9.04 Jaunty Jackalope (dual-boot with Vista), these days the processing/performance (esp., Firefox 3) and start up in  Ubuntu is very slow. I've been installing all the updates available as I don't know which ones to select. But my friend told me that my start up has many applications and also I've installed many applications which aren't necessary. Please help me with this. Thanx.

---

### Post by zkriesse on 2009-08-10
I don't see why your start up and processing is that slow...mine is quite fast....but I am running Ubuntu Jaunty on my system only...but I have quite a few apps on here so....it might be because of the dual boot w/ Vista....can you give me a time frame of how long it takes to finish booting and or just opening Firefox?

---

### Post by rawfool on 2009-08-10
Thnks for ur reply. I don't think it's because of Dual-boot. Because I'm running Ubuntu for quite a few months. Also I've upgraded to 9.04 just after it's release. But these days I've got many updates more than 50MB and installed all of them. Every time I get updates, I'll install them all. I'm pretty sure that my start-up has become slow, may be 4 to 5 seconds than earlier. Is there any way that I can select my start up objects. Thanks again.

---

### Post by callumacrae on 2009-08-10
Has vista got any slower?

Try Applications -> Preferences -> Startup Applications

I'm running UNR so that could be inaccurate.


Hope it helps,
~Callum

---

### Post by martinbaselier on 2009-08-10
If you upgraded your version, it's wise to profile your boot. When in grub (the bootmenu), press e to edit, e again on the second line (the one beginning with kernel) Then add profile to the end of the line (preceded with a space). First boot will take longer, next boot normally will be faster.

---

### Post by rawfool on 2009-08-11
Thanks for all your replies.
> **martinbaselier said:**
> If you upgraded your version, it's wise to profile your boot. When in grub (the bootmenu), press e to edit, e again on the second line (the one beginning with kernel) Then add profile to the end of the line (preceded with a space). First boot will take longer, next boot normally will be faster.

Adding profile: I gave a space and typed my username. Did I correctly "profile my Boot"? 
I am looking for something which cleans up my system like registry cleaner in windows. Thanx again.

---

### Post by Barafu Albino Cheetah on 2009-08-11
No, you had to add a keyword "profile" at the end of the line starting with word  "kernel". And reboot twice. You should do it every time you change your kernel. Diffrence is very big on multicore CPU. 
If you have installed many apps, especially system-level, you boot will become longer for 5 seconds. It is absolutely normal. Calm yourself - if you install as much applications on Vista it will boot 5 minutes longer.

---

### Post by rawfool on 2009-08-11
**@Barafu Albino -** I've added my username there. Will it do anything wrong? And you say reboot twice, should I type "*Profile*" for each of two reboots or only first? Thnk you very much.

---

