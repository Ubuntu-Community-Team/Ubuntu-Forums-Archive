---
title: "Startup Disk Check Frequency - GUI Control?"
date: 2010-12-17
forum: General Help
---

### Post by 2CV67 on 2010-12-17
I had it in mind that Ubuntu ran disk checks every 30 boots, but mine are more frequent - running between 10 & 25, which is an irritation.
Records show checks after: 12-21-10-20-10-20-13-25-16-21 boots.
Should I worry about either the frequency or the variability?

I found threads suggesting how to change the frequency using tune2fs, so I suppose I can try that to stretch the interval to maybe 50 or weekly?
Will it have any effect, since there is so much variation already?

Is there a GUI for setting this frequency, instead of fiddling in terminal, which I strongly dislike (sorry!)?

Thanks!

---

### Post by dcstar on 2010-12-17
> **2CV67 said:**
> I had it in mind that Ubuntu ran disk checks **every 30 boots**, but mine are more frequent - running between 10 & 25, which is an irritation.
Records show checks after: 12-21-10-20-10-20-13-25-16-21 boots.
Should I worry about either the frequency or the variability?

I found threads suggesting how to change the frequency using tune2fs, so I suppose I can try that to stretch the interval to maybe 50 or weekly?
Will it have any effect, since there is so much variation already?
........

[LIST=1]
[*]It is not "boots", it is every n "mounts" or every n "time" (day, weeks, months).
[*]There is no GUI AFAIK, but you may want to look into things like Ubuntu-tweak.
[/LIST]

---

### Post by 2CV67 on 2010-12-18
> **dcstar said:**
> It is not "boots", it is every n "mounts" or every n "time" (day, weeks, months).

Thanks for the detail correction!
In my case it comes to about the same thing, as I don't unmount my partitions between boots (at least, I don't think I do...).

I got a bit further with understanding why I get checks more than once per 30.
I have a separate /home partition.
tune2fs tells me the / partition has max count 37 & current count 19.
The /home partition has max count 36 & current count 8.
So the 2 partitions are being checked separately at varying intervals.
I feel better now I have understood that!

This is actually mentioned in man_tune2fs.
I suppose it could be desirable to avoid one huge mega-check, but for me, I would rather have less-frequent slow boots.
So I am thinking of resetting tune2fs to check both partitions just once per month (instead of every couple of days typically now).
Is that unreasonable?

Since there seems to be no GUI - what exactly do I need to do to get there?
As far as I can see, I need > $ sudo tune2fs -c 0  -i 28d /dev/sda3 & > $ sudo tune2fs -c 0  -i 28d /dev/sda5
Should that produce simultaneous checks every 4 weeks?

Is the information shown by tune2fs visible in a readable file anywhere?

Thanks!

---

