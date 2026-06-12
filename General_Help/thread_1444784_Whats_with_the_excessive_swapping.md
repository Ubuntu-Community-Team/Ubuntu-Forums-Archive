---
title: "Whats with the excessive swapping?"
date: 2010-04-01
forum: General Help
---

### Post by windowswithdrawalsyndrome on 2010-04-01
Ubuntu 10.04 is using 18% of my 2 GB of RAM. Why is it using over 200MB of swap file? 

Is my RAM not good enough for it? Is ubuntu snobby? Do I have to dress up or something?

And is there an easy way being developed to make ubuntu put more things in RAM so that I can show off to people how fast my menus open on my PC?

Also, do I pronounce it Linux or Linux? I mean linnux or line-ux?

Also, is it true that linux developers do not see the world as other people do but there right eye is actually seeing the world through a terminal and if they type exit it is like taking the red pill in the matrix?

Also, is it true that I will burn on average 15 more calories per day using a terminal instead of a GUI and that I'll feel 15 times smarter than those around me?

Is it true that each linux distribution is actually running a customized military strategy that infects the users in a mass conspiracy to attack Microsoft by deleting all the semi-colons from their C++ code?

---

### Post by stoneage on 2010-04-01
It is true that Lucid is a beta release and won't be considered stable until the end of April, so all Lucid posts for now should go here:-
[http://ubuntuforums.org/forumdisplay.php?s=&daysprune=-1&f=377](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=-1&f=377) where you are more likely to get useful help.

---

### Post by Cracauer on 2010-04-01
Please don't post questions like this without even saying how much RAM you have and what's running on the box.

In general, as the Linux kernel develops it gets more and more aggressive about freeing RAM. That includes both dropping readonly page and moving read/write pages to swapspace. Also, for all we know somebody in Ubuntu might have tuned swappyness.

---

### Post by windowswithdrawalsyndrome on 2010-04-01
> **windowswithdrawalsyndrome said:**
> Ubuntu 10.04 is using 18% of my 2 GB of RAM.

2GB. Not tweaked anything but I did clean the coffee stain off the keyboard. I'm running firefox and the CPU is generally having an easy time.

---

### Post by Cracauer on 2010-04-01
Oh I mistook that for using 18% of 2 GB swapspace.

Ignore the "free RAM" number, it's useless.

If you want more advice as to why swapspace is used you will have to do better than your keyboard story on what kind of workload you have on there. Or even easier - do you observe an actual performance problem?

---

### Post by windowswithdrawalsyndrome on 2010-04-01
Not sure how to get a nice list of the processes running to paste in here. I've only had two coffees today so the workload has been light. I don't observe an actual performance problem, especially since I got a newer hard drive that is so quiet I thought it was shy at first. Just wanting linux to be all you can be. Or is that the marines?

Knoppix was pretty sweet running from RAM and was hoping ubuntu could do similar things.

---

### Post by Ancanus on 2010-04-01
Hello WWS,

Take a look at this document: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
Particularly, read the part about **swappiness**.

---

### Post by windowswithdrawalsyndrome on 2010-04-01
Genius. My swap file is 0 bytes and more of my RAM is being used. I'm happy. Just wish I could put more of stuff in the RAM so that things went as fast as it can do. It is amazing the difference in speed between windows XP on my PC with bloatware compared to ubuntu.

May the caffeine be with you.

---

### Post by Cracauer on 2010-04-01
> **windowswithdrawalsyndrome said:**
> Genius. My swap file is 0 bytes and more of my RAM is being used. I'm happy. Just wish I could put more of stuff in the RAM so that things went as fast as it can do. It is amazing the difference in speed between windows XP on my PC with bloatware compared to ubuntu.

May the caffeine be with you.

But now you will lose when starting new programs and/or when existing programs need more memory.

Also, the default was there for a reason. If you messes with swappyness until your swapfile use turned 0 then you start dropping readonly pages at a high pace now.

---

### Post by 3rdalbum on 2010-04-02
> **Cracauer said:**
> But now you will lose when starting new programs and/or when existing programs need more memory.

Meh, I've never hit 2 GiB of active memory use, even with swapoff. I don't think there's anything to worry about.

[Linus Torvalds on how to pronounce Linux]("http://www.jx90.com/linux.html")

Basically, it's pronounced "Lin-ux".

---

### Post by JoelOl75 on 2010-04-02
[QUOTE=3rdalbum;9063560]Meh, I've never hit 2 GiB of active memory use, even with swapoff. I don't think there's anything to worry about.


There's a way to preload libraries into RAM to decrease startup time at the expense of RAM.

sudo apt-get install preload

---

### Post by Cracauer on 2010-04-02
> **3rdalbum said:**
> Meh, I've never hit 2 GiB of active memory use, even with swapoff.

That's because your system now effectively doesn't cache anything that's mapped readonly anymore. It's full of read-write mapped pages and they are they for the duration.

This will usually not turn out to be a performance win unless you are very narrowly single-application oriented (e.g. a game might run better this way if you don't care about anything else but the game).

---

