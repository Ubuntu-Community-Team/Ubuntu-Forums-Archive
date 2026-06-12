---
title: "HDD Spindown"
date: 2006-06-23
forum: General Help
---

### Post by Greeface on 2006-06-23
I was wondering how I would enable a spindown time on my computer in order to prolong the life of my drive (would this even help?) and I did a search but I didn't really find anything.  I know it must have something to do with hdparm, but I don't just want to go screwing around with it.

Thanks for any help

---

### Post by huygens on 2006-06-23
Hello,

I am not going to talk about whether you should tweak or not this parameter to save your disk life time. It has pros and cons, and mainly depends on your usage. So it is up to you to decide.

I know one easy way to do this. It is to use the laptop-mode! Don't be mislead by its name, it is working also for machine which are plugged directly to a power outlet. Now let's me explain you how to do this.

You first need to modify the /etc/default/acpi-support file to allow laptop mode: ENABLE_LAPTOP_MODE=true
Then you need to update /etc/laptop-mode/laptop-mode.conf
Maybe it is best to use laptop mode even when on AC power: ENABLE_LAPTOP_MODE_ON_AC=1. In this case, you should tweak the LM_AC_HD_IDLE_TIMEOUT_SECONDS parameter for your spindown timeout.
If you do not want to enable laptop mode even on AC power, then perhaps try only this parameter: NOLM_HD_IDLE_TIMEOUT_SECONDS

Finally run /etc/init.d/laptop_mode restart and you’re done.

Huygens

---

### Post by Greeface on 2006-06-27
Alright, thanks for the information, I will mess around with that this weekend.

---

### Post by jotagab on 2006-06-27
You should spindown your hard drive to improve your notebook battery efficiency, not your disk lifetime. Be careful if you have a desktop computer instead of a notebook/laptop because they usually have less spinups before failure.
Read the following for more info:
[http://www.xs4all.nl/~bsamwel/laptop_mode/tools/faq.html]("http://www.xs4all.nl/~bsamwel/laptop_mode/tools/faq.html")
Cheers!

---

### Post by Greeface on 2006-07-01
Ah, thank you, so I guess in the long run it would be best just to not have them spin down at all?  I have a desktop, so I will either leave it alone or have it spin down once every few hours or so.

---

