---
title: "Ubuntu 9.10 can't copy properly"
date: 2010-01-12
forum: General Help
---

### Post by prisoner849 on 2010-01-12
I'm having lots of problems right now trying to do pretty much any kind of copying from my network server to my internal hdd:

I'm using ubuntu 9.10 i386 netbook remix on my asus 1002ha using it's wireless connection to a dgn2000 router. The server is a windows box.

While trying to copy a medium number of file (100 to 200), each no bigger than 10-15 meg or copy files over 500 meg:

Copy speed stalls after an average of 100 meg is copied. nautilus must be manually terminated. Will not terminate the copy operation. The network connection no longer works.

Every time this happens, I eventually get the message "error while copying" with the details "cannot allocate memory"

My laptop has a gig of ram.

My hard drive has 100 gig free, more than enough for any of these operations.

I've tried:
rebooting
using ext4
using ext3
using ext2
using a wired connection (although I shouldn't be forced to use this)

Windows 32bit works and ubuntu 8.10 have worked perfectly for me.

Are there any tools I should be using to help debug this error?

Please help. If I can't resolve this soon, I won't be going back to ubuntu because I won't have time soon to be changing operating systems. I also won't be in a position to recommend ubuntu to a large number of people. Which is a shame because the netbook remix is good for everything else. But as you can guess, being able to copy something is pretty important.

---

### Post by prisoner849 on 2010-01-17
sweet! I managed to hold off doing any work on my laptop until I had a few more hours to try and work this out.

I have now got the laptop working perfectly with the router thanks to installing backports:
$ sudo apt-get install linux-backports-modules-karmic

I strongly urge anybody with wireless troubles to first find out what their hardware is and search around for some solutions:
$ sudo lshw -C network

Now that copying is working a treat, I can recommend 9.10 to anybody with a laptop. Everything works great, especially fonts which just seem to be so much nicer to look at than winXP for whatever reason.

---

