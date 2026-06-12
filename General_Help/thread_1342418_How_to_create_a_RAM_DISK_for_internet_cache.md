---
title: "How to create a RAM DISK for internet cache?"
date: 2009-11-30
forum: General Help
---

### Post by ProDigit on 2009-11-30
Hi,
in Xubuntu, I want to move the cache folder accessed by Firefox to a RAM disk.

Reason is, I run Xubuntu from a USB flash drive, and the caching of data on the stick at times causes minor freezes, and probably is also responsible for FireFox crashes I believe.

I know I can disable the cache, but doing so, would increase my internet bandwidth, because every time I load a page, it will need to be reloaded completely from the internet.

Most of the time I keep my computer online almost all day, and load some pages regularly.
Therefor I want to have a cache folder. I care less if the next day my cache folder would be gone, and has to be reloaded again.

I merely want to prevent if I see a youtube video, and want to see it again, that I'd have to coop with freezes because the video is being loaded on the disk, and as a result writes slow down all the other processes making the system lag.

So far for FireFox they told me to type:
```
about:config
```
in the browser URL, and enter a new string called:
**browser.cache.disk.parent_directory**
and enter the full pathname of the cache directory in the string value.

Now I need to know how I can set up a RAM disk, which will be autoloaded from boot, that will serve as cache directory for Firefox.

I have 2GB of RAM, with an Intel IGP, that uses upto 128MB of RAM as VRAM.
So technically, I have about 1,8GB of RAM available, minus the RAM needed for the OS and programs. Firefox at times uses 350-400MB of RAM.
Usually in Xubuntu, the Os uses less than 20% of RAM, which is less than 400MB of RAM.
So technically, I need about 1GB of RAM total minimum, leaving anywhere between 1 to 1024MB of RAM for the cache.

Let's say I want to create a RAMDISK of 512MB of RAM space!
It should be enough for average browsing, no?

I'm not very experienced with Linux, so a simple guide or some shell commands that could solve the problem would be very much appreciated!
For me, I prefer a simple, but effective solution,if that exists.

Thank you!

---

### Post by ProDigit on 2009-12-03
Bump?

How to create a RAMDISK in Ubuntu?

---

### Post by shaggy999 on 2009-12-03
In '/etc/fstab' add an entry similiar to this:

tmpfs directory_to_be_ramdrive tmpfs rw 0 0

---

### Post by jocko on 2009-12-03
There is already a ram disk you can use (/dev/shm).

---

### Post by dcstar on 2009-12-03
> **ProDigit said:**
> Hi,
in Xubuntu, I want to move the cache folder accessed by Firefox to a RAM disk.
........
I'm not very experienced with Linux, so a simple guide or some shell commands that could solve the problem would be very much appreciated!
For me, I prefer a simple, but effective solution,if that exists.


Then just set Firefox to use a Memory Cache.

---

### Post by ProDigit on 2009-12-04
> **dcstar said:**
> Then just set Firefox to use a Memory Cache.

And how do I do that?

I'm already working on a solution with eeeuser.com, so far unsuccessful.

Please look here:
[http://wiki.eeeuser.com/howto:firefoxramcache](http://wiki.eeeuser.com/howto:firefoxramcache)

Any simple suggestions on improvements/corrections?

I'm still not familiar what to type in FF, to set as the ramdisk folder
Is it:
home/user/ramdisk ?
or:
/home/user/ramdisk ?
or file:///home/user/ramdisk?

It's talking about a RAMDISK folder there, not a file, so I'm kind of lost in FF what to set.

---

### Post by TenPlus1 on 2009-12-04
Why use a ramdisk at all, go into about:config and set browser.cache.disk.enable to FALSE, then right-click and select NEW -> INTEGER and type browser.cache.memory.capacity <enter> and set to 30000 (for 30mb)...  Now it'll use your memory as a cache instead of disk...

---

### Post by ProDigit on 2009-12-07
> **TenPlus1 said:**
> Why use a ramdisk at all, go into about:config and set browser.cache.disk.enable to FALSE, then right-click and select NEW -> INTEGER and type browser.cache.memory.capacity <enter> and set to 30000 (for 30mb)...  Now it'll use your memory as a cache instead of disk...


1- Browser.cache.disk.enable was set at false, so I left it with that..
2- I entered the new integer, only I typed "150 000 000", without the spaces, since I at times look at youtube video's and wouldn't want the browser to crash when the video is slightly more than 30MB. On average you need to calculate about 10MB/min especially on HD video's.

I'll test this process out and reply back here!

---

### Post by ProDigit on 2009-12-08
Sorry, I don't have the impression it goes better. Perhaps a little bit, but not like I had expected.

Youtube still freezes...

---

