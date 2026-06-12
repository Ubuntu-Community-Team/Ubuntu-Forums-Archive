---
title: "How much RAM do I need for Firefox to never feel laggy?"
date: 2011-11-26
forum: General Help
---

### Post by brawnypandora0 on 2011-11-26
I currently have 512MB DDR and 1.0GHz. Whenever I have twenty tabs open with hundreds of photos in each tab, my computer feels very laggy.

How much more RAM do I need for it to not feel laggy? Is the CPU speed important too?

---

### Post by LinuxFan999 on 2011-11-26
What processor do you have?
 
If you want 20 or more tabs open, I would recommend 768MB or more.
 
EDIT: If you want no lag, use a dual-core processor and 1.5GB of RAM or More.

---

### Post by CryptAck on 2011-11-26
I must ask, is this a serious posting? :)

On a Core i7 w/4GB memory, I still experience lag from time to time when having multiple, resource extensive, tabs open.

---

### Post by brawnypandora0 on 2011-11-26
> **CryptAck said:**
> I must ask, is this a serious posting? :)

On a Core i7 w/4GB memory, I still experience lag from time to time when having multiple, resource extensive, tabs open.

If you upgraded to 8GB, would it still lag?

---

### Post by CryptAck on 2011-11-26
> **brawnypandora0 said:**
> If you upgraded to 8GB, would it still lag?

I'm planning a new system in the next few months with 16GB. My hypothesis is that latency will, unfortunately, still exist.

---

### Post by Redblade20XX on 2011-11-26
I think it's how firefox is written which causes such lag. The dude with the intel i7 still has lag even with such a powerful processor, more ram wouldn't make a difference if your cpu can't efficiently use it.

- Red

---

### Post by Telengard C64 on 2011-11-26
> **Redblade20XX said:**
> I think it's how firefox is written which causes such lag. The dude with the intel i7 still has lag even with such a powerful processor, more ram wouldn't make a difference if your cpu can't efficiently use it.

I've got an i7 with a few gigs of RAM, and Firefox is not lag-free. It is much smoother and faster than on my single core machine though.

Adding RAM won't fix it unless the lag is caused by swapping. Firefox can use quite a lot of memory, but I don't know what would make it lag. Unless you consider buggy plugins like Adobe flashplayer to be part of FF.

One of the things that changed from first release Firefox to modern FF is that now much of what makes up a profile is stored in a compact database. The database can be accessed at lower cost in resources than storing every kind of data in separate flat files (in theory anyway.)

So the Mozilla guys are trying to make FF faster. If it still isn't good enough for you then consider switching browsers. I've read that many Ubuntu users love Chrome (or Chromium or whatever), but I still use FF.

---

### Post by oldtimer7777 on 2011-11-26
> **brawnypandora0 said:**
> I currently have 512MB DDR and 1.0GHz. Whenever I have twenty tabs open with hundreds of photos in each tab, my computer feels very laggy.

How much more RAM do I need for it to not feel laggy? Is the CPU speed important too?

It isn't so much a memory issue but a hard drive RPM issue.  

Get a solid state HDD device. Pay the big money, and that should resolve this.

---

### Post by WorMzy on 2011-11-26
> **brawnypandora0 said:**
> I currently have 512MB DDR and 1.0GHz. Whenever I have twenty tabs open with hundreds of photos in each tab, my computer feels very laggy.

You don't say.

You can't possibly look at 2000+ photos simultaneously anyway, so why not try web browsing a little more sensibly?

Depending on the size of the photos, your RAM will be full, which means that a lot of swapping will be occurring, which means that your harddrive will be seeing a lot of action, which makes everything else feel sluggish; assuming, of course, that your swap partition is on the same disk as your Ubuntu partition.

More RAM would help, but a nice healthy dollop of common sense wouldn't go amiss.

---

### Post by pretty_whistle on 2011-11-26
> **brawnypandora0 said:**
> I currently have 512MB DDR and 1.0GHz. Whenever I have twenty tabs open with hundreds of photos in each tab, my computer feels very laggy.

How much more RAM do I need for it to not feel laggy? Is the CPU speed important too?
Here's a Firefox tweak to do to speed it up.  I've used this and it helps:

[http://www.ehow.com/how_2090761_speed-up-firefox.html](http://www.ehow.com/how_2090761_speed-up-firefox.html)

---

### Post by blueridgedog on 2011-11-26
> **CryptAck said:**
> I must ask, is this a serious posting? :)



My thoughts as well.  Quad core here with 8 gigs running 64 bit OS's (mac/linux/Windows) and an use chrome due to FF issues.

---

### Post by oldtimer7777 on 2011-11-26
> **blueridgedog said:**
> My thoughts as well.  Quad core here with 8 gigs running 64 bit OS's (mac/linux/Windows) and an use chrome due to FF issues.

If you have installed Ubuntu on a solid state HDD at 10x the speed of current standard HDD devices, this problem is resolved. Expect to pay big for a solid state hard drive.

---

### Post by brawnypandora0 on 2011-11-26
I hear Chrome is unsafe to use. Also, I don't like how there are no Bookmarks, Tools, Help, History, View, Edit, and File icons.

---

### Post by oldtimer7777 on 2011-11-27
> **brawnypandora0 said:**
> I hear Chrome is unsafe to use. Also, I don't like how there are no Bookmarks, Tools, Help, History, View, Edit, and File icons.

Chromium works very well.  I've never had a problem with it.  As for privacy, gee I don't really know.  I like Firefox. Opera too.  I don't like the latest version of Firefox, or how their release schedule has become more "frequent" lately too.

---

### Post by vasa1 on 2011-11-27
> **brawnypandora0 said:**
> I hear Chrome is unsafe to use....
FUD and OT.

---

### Post by brawnypandora0 on 2011-11-27
> **vasa1 said:**
> FUD and OT.

What can I do to make Chrome include Firefox's toolbars at the top left?

---

### Post by Corporation on 2011-11-27
I have an i7-720QM with 8GB DDR3 RAM and an SSD. Firefox lag persists with lots of tabs open, especially if some of them are things like Twitter or Facebook which makes a lot of ajax calls.

---

### Post by vasa1 on 2011-11-27
> **brawnypandora0 said:**
> What can I do to make Chrome include Firefox's toolbars at the top left?

The title of the thread mentions **Firefox** and **laggy**. Not Chrome. That's why I feel talk about Chrome here is off-topic.

Anyway, I'm pretty sure one can't change Chrome's *chrome* and that includes making toolbars appear.

---

### Post by brawnypandora0 on 2011-11-27
Is Chrome a better browser than FF for downloading? For example, say you're downloading something in the browser and suddenly your computer freezes. With FF, you'd have to restart the download from the beginning. Is it different with Chrome?

---

### Post by lovinglinux on 2011-11-27
> **vasa1 said:**
> The title of the thread mentions **Firefox** and **laggy**. Not Chrome. That's why I feel talk about Chrome here is off-topic.

Anyway, I'm pretty sure one can't change Chrome's *chrome* and that includes making toolbars appear.

Please let's focus on solving the OP problems with Firefox. If this thread turns into another browser war thread it will be closed or moved to recurring discussions.

> **brawnypandora0 said:**
> Is Chrome a better browser than FF for downloading? For example, say you're downloading something in the browser and suddenly your computer freezes. With FF, you'd have to restart the download from the beginning. Is it different with Chrome?

You can use Firefox [DownThemAll](https://addons.mozilla.org/en-US/firefox/addon/201/) extension, which has tons of improvement and features.

> **brawnypandora0 said:**
> I currently have 512MB DDR and 1.0GHz. Whenever I have twenty tabs open with hundreds of photos in each tab, my computer feels very laggy.

How much more RAM do I need for it to not feel laggy? Is the CPU speed important too?

You can't expect to load the entire web into memory and still have a smooth browser experience. With that amount of memory on your system, I would browse just a couple of tabs simultaneously without loading too much stuff on them, block flash elements with [Flashblock](https://addons.mozilla.org/en-US/firefox/addon/433/), block ads with [AdBlock Plus](https://addons.mozilla.org/en-US/firefox/addon/1865/), block tracking services with [Ghostery](https://addons.mozilla.org/en-US/firefox/addon/9609/) and control your FF cache with [Cache Status](https://addons.mozilla.org/en-US/firefox/addon/cache-status/). Also take a look at some optimizationg tips from [my tutorials](http://www.webgapps.org/tutorials/firefox/optimization).

---

### Post by LinuxFan999 on 2011-11-27
> **Corporation said:**
> I have an i7-720QM with 8GB DDR3 RAM and an SSD. Firefox lag persists with lots of tabs open, especially if some of them are things like **Twitter** or Facebook which makes a lot of ajax calls.
I agree, Twitter seems to slow down all browsers. For example, If I have a lot of tabs open, and I try to open a news article, but get redirected to twitter, in which a tweet with a link to the site appears, then the browser suddenly slows down a little. It seems to affect older computers more than newer ones.

---

### Post by MarjaE on 2011-11-27
It's the internet. It's always slow. I'm not sure more RAM or a faster CPU will change that.

Websites use more and more images, start relying on more and more videos and including less and less descriptive text. Eventually the connections start timing out faster than the sites can load. It's crazy.

---

### Post by brawnypandora0 on 2011-11-27
> **MarjaE said:**
> It's the internet. It's always slow. I'm not sure more RAM or a faster CPU will change that.

Websites use more and more images, start relying on more and more videos and including less and less descriptive text. Eventually the connections start timing out faster than the sites can load. It's crazy.

Wow, so the Internet is actually slower than it was say five years ago on an absolutely scale?

Which is more important for browsing--CPU or HD capacity/speed? Why would a quad core perform faster than a dual core if the clock rates are identical?

---

### Post by Habitual on 2011-11-27
> **MarjaE said:**
> It's the internet. It's always slow. ...

I disagree.
NOT like cable 10 years ago. It's a LOT better these days.

---

### Post by boast on 2011-11-27
you can try this (relocating cache and/or your profile to ramdisk):

[https://wiki.archlinux.org/index.php/Speed-up_Firefox_using_tmpfs](https://wiki.archlinux.org/index.php/Speed-up_Firefox_using_tmpfs)

---

### Post by oldtimer7777 on 2011-11-27
> **boast said:**
> you can try this (relocating cache and/or your profile to ramdisk):

[https://wiki.archlinux.org/index.php/Speed-up_Firefox_using_tmpfs](https://wiki.archlinux.org/index.php/Speed-up_Firefox_using_tmpfs)


Well, when you have multiple windows in your browser open, it will write that data to the hard drive in the form of a cache.  Not everything is in the RAM sticks.  Having a faster RPM spin up rate would help, or even better, solid state HDD.

---

### Post by vasa1 on 2011-11-27
> **LinuxFan999 said:**
> I agree, Twitter seems to slow down all browsers...
That's the price of being "social".

---

### Post by pqwoerituytrueiwoq on 2011-11-27
> **brawnypandora0 said:**
> Wow, so the Internet is actually slower than it was say five years ago on an absolutely scale?

Which is more important for browsing--CPU or HD capacity/speed? Why would a quad core perform faster than a dual core if the clock rates are identical?
clock speed and cores are not everything there is architecture
compare a 3 ghz i7 quad core and a athlon II 3ghz quad core 
the i7 will run circles around the athlon II
you can have a system with 8 cores/threads but there is very little software that will use more than once core/thread
some software that can use more than one includes some math ones/benchmarking software/some games (not over 3)/file converters (bulk jobs)

odds are the reason you hare having lag is adobe flash
[FONT=Courier New]pkill -f flashplayer[/FONT] that command will likely stop your lag and all flash objects will get a crashed error in the browser

look into ram disk if you are worried about hdd speed or get a ssd

---

### Post by brawnypandora0 on 2011-11-28
So why is Flash so slow? Is there a free non-Adobe version of Flash?

---

### Post by WorMzy on 2011-11-28
Yes, gnash. I wouldn't get your hopes up about it though, it rarely works as well as the official flash plugin.

---

### Post by Telengard C64 on 2011-11-29
> **MarjaE said:**
> Websites use more and more images, start relying on more and more videos and including less and less descriptive text. Eventually the connections start timing out faster than the sites can load. It's crazy.

There is data supporting this:
[http://royal.pingdom.com/2011/11/21/web-pages-getting-bloated-here-is-why/](http://royal.pingdom.com/2011/11/21/web-pages-getting-bloated-here-is-why/)

> **brawnypandora0 said:**
> So why is Flash so slow?

Only Adobe can answer that, unless they release source code for their plugin. Until then, we can only guess.

---

### Post by brawnypandora0 on 2011-11-29
So what's the guess?

---

### Post by Telengard C64 on 2011-11-29
> **brawnypandora0 said:**
> So what's the guess?

My guess is because it is a bloated, crufty, buggy, relic with security flaws that would make Microsoft blush. That's just my opinion though, and only a blind guess. For more guesses:

[http://google.com/search?q=why+flash+sucks](http://google.com/search?q=why+flash+sucks)
[http://google.com/search?q=flash+is+slow](http://google.com/search?q=flash+is+slow)

---

### Post by boast on 2011-12-01
> **brawnypandora0 said:**
> So what's the guess?

its only like 1 guy trying to port the windows version to linux.

---

