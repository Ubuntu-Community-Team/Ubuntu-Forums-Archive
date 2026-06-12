---
title: "How to prevent one app from swapping?"
date: 2011-11-20
forum: General Help
---

### Post by SoWhat.lv on 2011-11-20
Hello!

When I start my laptop, everything is working fast. Then after few hours of browsing internet with Chromium,everything gets extremely slow. 

I think that it is because Chromium stores too many data in swap. Is there a way to prevent this?

---

### Post by Paddy Landau on 2011-11-20
When it starts to go slow, is it only Chromium that is slow, or do all apps go slow?

What happens if you close Chromium and open it again; does your computer speed up again?

It may be that Chromium has something called a "memory leak". If that is the case (but I'm not sure that it is), closing and reopening it should work. If it is another application causing the problem, the easiest is to log out and in again.

---

### Post by oldos2er on 2011-11-20
How much RAM do you have?

You can change swappiness by adding a line to /etc/sysctl.conf ```
vm.swappiness=5
``` Reboot, or run ```
sudo sysctl -p
```
Acceptable values are from 0 to 100, 0 being essentially the same as turning off swap. I think the default value is 60.

[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

---

### Post by SoWhat.lv on 2011-11-21
> **Paddy Landau said:**
> When it starts to go slow, is it only Chromium that is slow, or do all apps go slow?

All apps become slow. 
> **Paddy Landau said:**
> What happens if you close Chromium and open it again; does your computer speed up again?

As I remember- no. But since I changed vm.swappiness to 5, my laptop works much better. 

[QUOTE=oldos2er]
How much RAM do you have?
[/QUOTE]
I have 512MB.

Anyway, I wanted to know - is there a way to control which apps are allowed to store stuff in swap and which aren't? 
I would like to allow Chromium, mouse (and their linked components) to use only RAM, but all other apps, like Skype, Update managers etc. to use only swap.

---

### Post by Paddy Landau on 2011-11-21
> **SoWhat.lv said:**
> But since I changed vm.swappiness to 5, my laptop works much better.
Excellent news.

> **SoWhat.lv said:**
> I would like to allow Chromium, mouse (and  their linked components) to use only RAM, but all other apps, like  Skype, Update managers etc. to use only swap.
I don't know if there is a way, but restricting Skype etc. to only swap  will make them ridiculously slow as they thrash in and out of RAM.

You don't say what version of Ubuntu you are using. For Ubuntu, 512Mb is a bit low. You could try using [Lubuntu]("https://wiki.ubuntu.com/Lubuntu") instead, which is optimised for low-spec computers.

---

### Post by SoWhat.lv on 2011-11-21
I am already using latest Lubuntu and I like it :)

---

### Post by SoWhat.lv on 2011-11-21
I found out when exactly system becomes extremely slow - when I open Chromium with more than 5 tabs and Skype in the same time. It becomes almost impossible to close Chromium, because everything works really slow. After pressing X button, I was waiting 30min, only then it closed and everything started working fast again.

      Paddy Landau, can you tell more about memory leaking?

PS. FF works much better than Chrome.

---

### Post by Paddy Landau on 2011-11-22
Gosh, that's interesting. Chromium is supposed to be more lightweight than Firefox. Is your machine fully up-to-date? (Run Update Manager and install all updates.)

By the way, which version of Lubuntu are you running -- 11.10?

A memory leak is where a program uses some memory for something, and then "forgets" to let it go when it is finished with it. Thus, it uses more and more memory until it is closed. These days, memory leaks tend to be found quite quickly, so that probably is *not* your problem.

512Mb is not all that much for a modern system. You may find that Skype + more than 5 tabs is taking too much RAM, and so you need the swappiness. Does Chromium (with more than 5 tabs and Skype) take 30 minutes to close when you revert your swappiness to the default? The whole point about swapping is that it is used only when the RAM fills up (or when you hibernate), so it's not necessarily a good idea to reduce the swappiness.

EDIT: Skype is not likely to swap out much, because it stays constantly connected to the Internet checking for communication.

---

