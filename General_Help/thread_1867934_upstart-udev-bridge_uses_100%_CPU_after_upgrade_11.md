---
title: "upstart-udev-bridge uses 100% CPU after upgrade 11.04 -&gt; 11.10"
date: 2011-10-23
forum: General Help
---

### Post by mexp on 2011-10-23
The title says it all... I use Dell Latitude D620. Found this bug link: [https://bugs.launchpad.net/ubuntu/+bug/875242](https://bugs.launchpad.net/ubuntu/+bug/875242)

Any workarounds in the meantime?

Thanx!

---

### Post by mexp on 2011-10-25
Yes, a workaround is to remove the laptop battery, it actually says this on the bug report too... I did a fresh install, but the problem remains when the battery is connected.

---

### Post by neopium on 2011-10-27
> **mexp said:**
> Yes, a workaround is to remove the laptop battery, it actually says this on the bug report too... I did a fresh install, but the problem remains when the battery is connected.

Great workaround... but when you have a MacBook Pro, you can't remove the battery...

Is it dangerous to just kill the process?

---

### Post by mexp on 2011-10-27
I don't know if you could kill the process from command line with some extra --force options, but at least from the System Monitor Process list it's not possible - the process just won't die!

---

### Post by mexp on 2011-10-27
...hoping this bug will be fixed soon - I have a brand new battery and it lasts about 35 minutes when one of the CPU's is running on 100% all the time :(

---

### Post by neopium on 2011-10-30
> **mexp said:**
> I don't know if you could kill the process from command line with some extra --force options, but at least from the System Monitor Process list it's not possible - the process just won't die!

That doesn't surprise me. The process is a root process, it can only be killed by a root user (using su or sudo).

I haven't tried killing it as I don't know what the consequence may be for my battery. I don't want to break my hardware...

So for now I don't use ubuntu, I keep using OS X. Too bad...

---

### Post by johnneebee on 2011-10-30
I have had the same problem since i upgraded to 11.10. I was able to "idle" the process once i found it's pid in terminal. Technically it's still running but it no longer gobbles all my cpu cycles:

$ ps -aux
 
then after looking for its PID in the list:

$ sudo kill -kill 280

That does it for me everytime but only till i log in again from booting, or suspending, or from idling. The command is running but at very very low cycle levels.

I am now trying without the battery and after suspending i was able to come up to a system running at only 6% CPU usage cause i have 8 tabs open in chrome and 3 terminals open and nautilus too.

Can't wait for the fix.



No witty quotes, I'm missing a few crucial neurons!!

---

### Post by mexp on 2011-11-06
I wonder if this would have anything to do with a replacement battery (instead of original Dell battery). Does this bug affect other kind of hardware combinations? Waiting for the fix... Killing the process as root helps :)

---

### Post by mexp on 2011-11-11
Well, this is really annoying, as even if I kill the process, it will start using 100% CPU after a while again... Please someone, please! Would not want to revert to 11.04 :(

---

### Post by mexp on 2011-11-17
So this seems to me that it's a problem with the replacement battery. I went to a store where they sell old laptops, and tested my system with an *original* Dell battery - and this process doesn't hang. I did this two, three times, every time same result.

Perhaps someone else could confirm this? And I wouldn't mind having this fixed anyway, original Dell batteries are twice the price of the replacement batteries.

---

### Post by mexp on 2011-11-17
So this seems to me that it's a problem with the replacement battery. I went to a store where they sell old laptops, and tested my system with an *original* Dell battery - and this process doesn't hang. I did this two, three times, every time same result.

Perhaps someone else could confirm this? And I wouldn't mind having this fixed anyway, original Dell batteries are twice the price of the replacement batteries.

---

### Post by pivert on 2012-01-23
There seems to be a fix :

[http://areyoueye.net/?p=143](http://areyoueye.net/?p=143)

---

### Post by mexp on 2012-01-26
Hallelujah!!!!! It worked! I'm so glad I didn't yet get a new, original Dell battery, costing roughly 130 €... 

Thanks for help.

---

