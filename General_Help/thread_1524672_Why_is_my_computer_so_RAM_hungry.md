---
title: "Why is my computer so RAM hungry?"
date: 2010-07-05
forum: General Help
---

### Post by Shadow12313 on 2010-07-05
I am currently running ubuntu with the LXDE interface which is supposed to be very efficient and fast but I am noticing a lot of my ram is being eaten up by other processes.  Here is a screenshot of me in xterm mode running htop.

[IMG]http://img189.imageshack.us/img189/7725/screenshotbj.png[/IMG] 

Why would it be using so much in xterm?
Thank-you all in advance :)

By the way I apologize for the image quality but it was using about 300mb.  If you want a better picture just ask.

---

### Post by Leppie on 2010-07-05
please post the screenshot as an attachment, like this it's of no use...

---

### Post by Shadow12313 on 2010-07-05
Very well, here is a picture of me running the LXDE.

---

### Post by happyhamster on 2010-07-05
Could you post the output of:

free -m

It will give more detailed info about RAM usage.

---

### Post by Leppie on 2010-07-05
it's because you've got compiz running.
compiz usually sucks up a lot of memory. try disabling it.

---

### Post by Shadow12313 on 2010-07-05
Here is the output of the command:



```
ben@T-850:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1507       1395        112          0         87        751
-/+ buffers/cache:        556        950
Swap:            0          0          0

```

---

### Post by Shadow12313 on 2010-07-05
I tried disabling compiz but it is still has 460mb of RAM.

---

### Post by happyhamster on 2010-07-05
Both screenshots you did appear to focus on the console-kit-daemon entries: don't worry about them. It would be more interesting to see the top of the htop output.

The console-kit stuff are threads, and the total amount of RAM they consume is small (~ 3MB total). It's not pretty having so many threads around, but it doesn't take up much RAM at all.

See: [https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/148454](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/148454)
(This 'bug' likely won't be fixed anytime soon.)

---

### Post by happyhamster on 2010-07-05
```
ben@T-850:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1507       1395        112          0         87        751
-/+ buffers/cache:        556        950
Swap:            0          0          0

```
That means 556MB is in use, and 950MB is free (most of which is used as a cache to improve the responsiveness of the desktop). Swap isn't used, which is great.

Which applications were running when you ran "free -m"?

---

### Post by Shadow12313 on 2010-07-05
Nothing I just logged on.  And by the way I think that was the top of the list.

---

### Post by askreet on 2010-07-05
560M of usage is pretty standard for Ubuntu 10.04, I think.  I currently am using 781M running PekWM with Chrome, X-Chat and Transmission.

---

### Post by Leppie on 2010-07-05
560 is not so standard for lxde...
i believe my xubuntu was somewhere around 150...

---

### Post by Shadow12313 on 2010-07-05
I've seen people use lxde with 60mb used!  What's with my computer?

---

### Post by happyhamster on 2010-07-05
> **Shadow12313 said:**
> Nothing I just logged on.  And by the way I think that was the top of the list.
Then it's likely this issue:
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)

---

### Post by Shadow12313 on 2010-07-05
Anyway to fix it should I back-up and reinstall?

---

### Post by kerry_s on 2010-07-05
it's just a linux thing. it caches as long as theres room, the benefit is speed.
why have lots of ram if you don't want to use it?

---

### Post by happyhamster on 2010-07-05
Aside from uninstalling ureadahead (which might not be safe), the original bugreporter has posted a fix here:
[http://ubuntuforums.org/showthread.php?t=1363165](http://ubuntuforums.org/showthread.php?t=1363165)

Before trying that, make sure you do see the exact same symptoms:

- Delete the file /var/lib/ureadahead/pack:

sudo rm /var/lib/ureadahead/pack

- Reboot: initial RAM usage should be high.

- Reboot again: RAM usage should be normal.

---

### Post by Shadow12313 on 2010-07-05
> **kerry_s said:**
> it's just a linux thing. it caches as long as theres room, the benefit is speed.
why have lots of ram if you don't want to use it?

But, I do need a lot of ram to run my virtual machines and games.

---

### Post by kerry_s on 2010-07-06
> **Shadow12313 said:**
> But, I do need a lot of ram to run my virtual machines and games.

& you can do that, most of it is cached, ram is released when needed by other programs. all you have to do is play your games or run your vm's, let the ram do what it's suppose to do.

if you want to watch it add the monitor, i got a panel with nothing but the monitor, i see memory go up & down all the time, especially when i'm watching movies or playing games, i see it get released after a period of time, like the memory is cleaning old cache.

---

### Post by Leppie on 2010-07-06
> **Shadow12313 said:**
> Here is the output of the command:



```
ben@T-850:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1507       1395        112          0         87        751
-/+ buffers/cache:        556        950
Swap:            0          0          0

```
the 556mb is the amount of memory in use by applications. the amount used by caching, is 1395 - 556 = 839mb.
what graphics card do you have and which drivers are you using?

---

### Post by kerry_s on 2010-07-06
Shadow12313,
i would also like to add, not having swap is a mistake. you have no fall back if you should ever use more then the amount of ram you have. 
1.5gb is a lot, but it is possible to use that, which would bring your system to a crawl or maybe even crash it.

i have 2gb ram & have 2gb of swap to match it.

mine:
```
owner@foxconn-2:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2004        872       1131          0         41        610
-/+ buffers/cache:        219       1784
Swap:         1951          0       1951
```

---

### Post by Leppie on 2010-07-06
> **kerry_s said:**
> Shadow12313,
i would also like to add, not having swap is a mistake.
i have swap, but i only have it so i can hibernate my machine.
under normal circumstances, the swap is never touched (i don't do video editing, 2d/3d rendering, etc.)

---

### Post by kerry_s on 2010-07-06
> **Leppie said:**
> i have swap, but i only have it so i can hibernate my machine.
under normal circumstances, the swap is never touched (i don't do video editing, 2d/3d rendering, etc.)

well better to have it & not need, then to not have it & need it. ;)

i don't hibernate, but i do suspend every now & then. most of the time i just leave the system on & turn off the screen.
i have managed to use the swap, when multi-tasking. i'll have a game paused in the background, maybe even a movie, several browsers with several tabs, music player, a few doc's, i use the calculator a lot, etc....

life gets crazy sometimes, you just never no what you'll be doing next. :lolflag:

---

### Post by Shadow12313 on 2010-07-06
I would like to point out that I do have 5gb of swap that just wasn't on.

---

### Post by Shadow12313 on 2010-07-06
> **Leppie said:**
> the 556mb is the amount of memory in use by applications. the amount used by caching, is 1395 - 556 = 839mb.
what graphics card do you have and which drivers are you using?

I have a Nvidia Geforce 9400GT.

---

