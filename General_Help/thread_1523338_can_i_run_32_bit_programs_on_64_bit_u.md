---
title: "can i run 32 bit programs on 64 bit u?"
date: 2010-07-03
forum: General Help
---

### Post by itsjoshgrant on 2010-07-03
ok i think im gonna buy a 64 bit laptop.
my old 32 bit laptop is dying.
i heard programs in 64 bit linux can run
in 32 bit... is this true
if so i dont think there is any reason
to stick with 32 (if so tell me please!)

thanks!

---

### Post by Lolpanda on 2010-07-03
for 90% of the apps, yes.

Certain Apps won't work, or have a little lower preformance (Adobe Flash) if you use 32 on a 64. Wine comes to mind, since Wine64 is kinda sorta not finished but they get around it by forcing Wine to use 32bit Commands and not 64bit. Drivers have 64bit versions, so no issues there. 

For the most part, because of how ubuntu ships release to release, you should be fine with 64bit

---

### Post by pbrane on 2010-07-03
Yes you can run some 32-bit programs in 64-bit Ubuntu. You will need to install some 32-bit libraries. I am running 64 bit Ubuntu and have not needed any 32-bit programs/libraries. Occasionally there will be a third party app the won't be available as 64 bit, e.g. google-earth.

The decision is yours of course. If you have a 32-bit app that is not available as a 64-bit app then you should be able to run it in 64-bit Ubuntu.

Also I am using 64-bit Flash and I haven't noticed any performance issues.

---

### Post by WorMzy on 2010-07-03
You can install the 32-bit libraries and run some 32-bit programs where necessary. Most have a 64-bit version available nowadays though.

If you have less that 4GB of RAM, or you don't have a 64-bit compatible processor, then you should stick with 32-bit. Also, if you're using a wireless device that needs a Windows driver and NDISwrapper to run, then make sure there's a 64-bit Windows driver for it before you make the switch, or else you'll run into a brick wall as there's no way of running a 32-bit Windows driver with 64-bit NDISwrapper.

---

### Post by itsjoshgrant on 2010-07-03
> **WorMzy said:**
> You can install the 32-bit libraries and run some 32-bit programs where necessary. Most have a 64-bit version available nowadays though.

If you have less that 4GB of RAM, or you don't have a 64-bit compatible processor, then you should stick with 32-bit. Also, if you're using a wireless device that needs a Windows driver and NDISwrapper to run, then make sure there's a 64-bit Windows driver for it before you make the switch, or else you'll run into a brick wall as there's no way of running a 32-bit Windows driver with 64-bit NDISwrapper.

what if the laptop has exactly 4gb of ram
should i just stick to 32 bit?

---

### Post by WorMzy on 2010-07-03
How much RAM does your graphics card have? Because that counts too. Also if you ever find that you're using ~90% of the available RAM, and can run 64-bit, then switching would be advisable.

---

### Post by Lolpanda on 2010-07-03
> **pbrane said:**
> Also I am using 64-bit Flash and I haven't noticed any performance issues.


The latest issue with Flash isn't so much preformance, as security, there is a critical vulnerability in the last 64bit version of Linux Flash that got released. Its fixed as of the newest release  (10.1 I believe), but 64bit Linux flash has been dumped (for the time being) so you are essentially allowing a known, known to be exploited, platform independant exploit to run on your comp =P

All 64 Bit Linux Flash downloads as of now have that vulnerability, Only Linux 32 is safe from it

---

### Post by Seanlol on 2010-07-03
> **Lolpanda said:**
> The latest issue with Flash isn't so much preformance, as security, there is a critical vulnerability in the last 64bit version of Linux Flash that got released. Its fixed as of the newest release  (10.1 I believe), but 64bit Linux flash has been dumped (for the time being) so you are essentially allowing a known, known to be exploited, platform independant exploit to run on your comp =P

All 64 Bit Linux Flash downloads as of now have that vulnerability, Only Linux 32 is safe from it

Hm. I'm using 64 bit Ubuntu, how do I check which flash I have? I'm pretty sure you can do it from within firefox, but I've never had to check that.

---

### Post by Vaphell on 2010-07-03
**about:[b]**plugins[/b] in the address bar
if you installed it automatically via apt it will be wrapped up 32 bit version, 64bit had to be installed manually
also you can try **locate libflashplayer** in terminal - if you get only libflashplayer.so with no sign of wrapper, you got 64bit version

---

### Post by Seanlol on 2010-07-03
> **Vaphell said:**
> **about:plugins** in the address bar
if you installed it automatically via apt it will be wrapped up 32 bit version, 64bit had to be installed manually
also you can try **locate libflashplayer** in terminal - if you get only libflashplayer.so with no sign of wrapper, you got 64bit version

Ah, thanks. The wrapper is there, it must be the wrapped 32 bit version. Thanks.

---

### Post by pbrane on 2010-07-03
> **Lolpanda said:**
> The latest issue with Flash isn't so much preformance, as security, ....

Thanks! Where have I been? I didn't know that. I deleted the plugin, I manually installed it in ~/.mozilla/plugins.

I sure hate to have to install all those 32-bits libs to run a plugin though. Maybe I'll do without for now.

---

