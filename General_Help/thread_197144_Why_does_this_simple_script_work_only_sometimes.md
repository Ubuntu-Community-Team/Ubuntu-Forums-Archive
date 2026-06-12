---
title: "Why does this simple script work only sometimes?"
date: 2006-06-15
forum: General Help
---

### Post by m0nstr42 on 2006-06-15
My cheap (free, actually) Dell router gives two dns servers - one for the router and one for the ISP.  This causes badness - e.g. web pages stalling for 10-20 seconds with "looking up some.com" at the bottom of the browser.  The solution is to remove the line corresponding to the router from /etc/resolv.conf :

```
nameserver 192.168.2.1   <--- remove this line
nameserver <nameserver for isp>
```

So here is my problem:  I wrote this script to remove that line from the file

```
#! /bin/bash
cp /etc/resolv.conf /etc/resolv.conf.old
cat /etc/resolv.conf | grep -v 192.168 > /etc/resolv.conf
cat /etc/resolv.conf
```

The first and last lines are just to cover myself in case it doesn't work and to spit out the resulting file so I can see whether it worked, the middle line obviously does all the work.  

I could certainly understand if I just did something wrong and it didn't work at all, but the weird thing is, sometimes it DOES work and sometimes it DOESNT work.  That is, sometimes it does exactly what it should do (remove any line containing "192.168"), and sometimes it spits out an empty file.  I've kept track and there doesn't appear to be any difference in the original /etc/resolv.conf file between times when it works and times when it doesn't.

So how can such a simple script perform different actions on the same input file?  I post this to ubuntu forums because a) I'm running ubuntu b) the ubuntu forums rock and c) I played with FC5 for a while and the script *always* worked on that, which leads me to believe that the unreliability has something to do with ubuntu?

---

### Post by IYY on 2006-06-15
What if you did it like this...

#! /bin/bash
cp /etc/resolv.conf /etc/resolv.conf.old
grep -v 192.168 /etc/resolv.conf > /etc/resolv.conf.new
mv  /etc/resolv.conf.new /etc/resolv.conf

---

### Post by soze on 2006-06-15
Well, let's consider what the line
```
cat /etc/resolv.conf | grep -v 192.168 > /etc/resolv.conf
```
is *really *doing.

[LIST]
[*]Start up 2 programs ***at the same time*** (cat and grep)
[*]The output of cat will be sent to the input of grep, the output of which will be written to the ***same file that cat is reading***.
[/LIST]

Depending on the timing of cat's opening/closing of the file (which is independent of grep's writing the output), you will have unpredicatable results, which is why you should not do this sort of thing.

(Shorter answer: Sometimes, grep's output begins before cat opens the file, so cat "sees" an empty file)

So.. IYY's suggestion is a good one.

---

### Post by jmacak on 2006-06-15
Hi

I wonder if this is getting wrapped around the axles during the cat/piping.

In my testing, if I leave off the cat (e.g. grep -v text filename>filename) I always end up with an empty file.  Maybe something is not happening in the right order with your cat pipe grep command, but only sometimes.

If you are copying the original file in the first place, why don't you just use that file as input (e.g. grep -v 192.168 /etc/resolv.conf.old > /etc/resolv.conf).  The script is simplified by no longer needing the cat or the pipe.

Just a thought.

cheers

joe in seattle

---

### Post by soze on 2006-06-15
[QUOTE=jmacak]
In my testing, if I leave off the cat (e.g. grep -v text filename>filename) I always end up with an empty file.  Maybe something is not happening in the right order with your cat pipe grep command, but only sometimes.
[/QUOTE]

Pretty much the same situation as above (albeit a simpler example).
In your case, filename is being opened for output (and clobbered) prior to (or during) grep opening the file for reading, so grep sees nothing but an empty file as its input.

---

### Post by mlind on 2006-06-15
About managing resolv.conf entries, did you read
[http://www.debian.org/doc/manuals/reference/ch-gateway.en.html#s-dns-resolvconf](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html#s-dns-resolvconf)

---

### Post by m0nstr42 on 2006-06-16
All -
Your responses make sense.  I tried the first suggested modification and it works fine so far.  

My queston was partly practical (which seems to be solved - I have a so-far working solution), but partly for a deeper curiosity - why did this work more reliably on another distro and not on ubuntu?  It seems that it must have to do with precedence for mutliple programs accessing files.  Is this configurable?  Are there benefits to different configurations?

I will also check out resolvconf.

Thanks!

---

