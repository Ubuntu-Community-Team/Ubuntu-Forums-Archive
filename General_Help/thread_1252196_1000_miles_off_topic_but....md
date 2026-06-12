---
title: "1000 miles off topic but..."
date: 2009-08-28
forum: General Help
---

### Post by Jameshardy88 on 2009-08-28
Hi guys i realise that this is about as far off topic as i could possibly get but i am totally confused by this problem and could think of nowhere else i could possibly get the answer. As such i'll understand if i don't get much of a response.

Basically i dual boot windows vista and ubuntu jaunty (jaunty for most of the time, vista purely to play games with a few friends over a LAN pretty much). On my vista partition i have 3 games that i use crysis, crysis warhead and COD4. until recently they all worked flawlessly then all of a sudden crysis and COD4 would no longer start giving me error code 1000. After trying all that i could think off i gave up and completely reinstalled vista and the games. however again i encountered the exact same problem on those to games. However when using the same install disks on another computer they work fine! i can't see what the problem is the OS is fresh and the CD's still work fine, ive tried emptying my directories and everything, what could possibly be causing this?

Thankyou very much for your time, all the best,

James

---

### Post by credobyte on 2009-08-28
Agreed @ off topic, but - would be nice if you could show us some screenies ( error 1000 .. wtf ? ).

---

### Post by Jameshardy88 on 2009-08-28
ill get right on it 2mins...

---

### Post by Jameshardy88 on 2009-08-28
I apologise for the bad photoshopping but essentially after clciking to load one of the games i am displayed with the message on the left followed shortly afterwards by the one on the right.

---

### Post by Jameshardy88 on 2009-08-28
oh sorry and the error 1000 is the code that it references when i looked up the failure on event viewer (keeps a log of all things that go wrong on windows according to my friend) im not much on a windows buff

---

### Post by credobyte on 2009-08-28
Do you emulate their CD/DVD's ( Daemon Tools, Alcohol, etc. ) ?

---

### Post by Jameshardy88 on 2009-08-28
emulate? what like a crack or something?

---

### Post by credobyte on 2009-08-28
> **Jameshardy88 said:**
> emulate? what like a crack or something?

No, as an example, you use .iso image instead of an actual DVD ( physical one ). All I could find about this problem pointed to bad .mdf / .iso images ..

---

### Post by Jameshardy88 on 2009-08-28
nope sorry i use actual CD =(

---

### Post by smakand on 2009-08-28
> No, as an example, you use .iso image instead of an actual DVD ( physical one ). All I could find about this problem pointed to bad .mdf / .iso images ..Actually Event ID 1000 means that the application crashed without warning, it's like the most generic error you can get, in my experience it's because of segfaults.

Have you run memtest?

---

### Post by wirelessmonkey on 2009-08-28
Are you using burned disks, or are you using disk images? Do you have Daemon Tools installed on Vista? Alcohol 120% maybe? Google implies that this is an error caused by the DRM crap used by these games.

---

### Post by Jameshardy88 on 2009-08-28
whats a segfault? and how would i got about running a memtest in vista? (sorry lots of silly questions)

---

### Post by Jameshardy88 on 2009-08-28
also whats the DRM (sorry) and no im using the actual CD

---

### Post by smakand on 2009-08-28
Pop in your Ubuntu cd and run a memtest when the prompts come up. You might need the alternative CD, I'm not sure. DRM stands for Digital Rights Management, and it's designed to remove any rights you have on a digital item, and stop piracy.

> Google implies that this is an error caused by the DRM crap used by these games.     That just means that these cracks are causing a generic, unreported error. It could be anything, it doesn't mean he's using a crack. I get these sometimes when writing my own applications. But if it is caused by the DRM, it could be that something on these games is designating his system as hostile.

---

### Post by Jameshardy88 on 2009-08-28
oh so i can just runa ubuntu 1 at it'll check the windows partition as well? ill have a go at that now, thanks =)

---

### Post by P4man on 2009-08-28
No it will just test your physical RAM memory. but thats a good thing to test :)

---

### Post by P4man on 2009-08-28
> **smakand said:**
> DRM stands for Digital Rights Management, and it's designed to remove any rights you have on a digital item, and stop piracy.


You're right of course, thats what its designed to do. But because it gives you many headaches to legal owners who just want to run the damn software they paid for, if anything it ends up encouraging piracy. The pirated copies work without problems, the legal copies require you to have the cd in place, run DRM crap drivers  in the  background that crash your pc or even install backdoor trojans (hello sony?). Its more than ironic that pirated copies give a "better user experience" :)

---

### Post by Hogosha on 2009-08-28
still better than starforce.

---

### Post by Jameshardy88 on 2009-08-28
i assume there is is no way to delete this DRM stuff if thats the problem, guess that would kind of defeat the object of it lol

---

### Post by del_diablo on 2009-08-28
> **Jameshardy88 said:**
> i assume there is is no way to delete this DRM stuff if thats the problem, guess that would kind of defeat the object of it lol

Thats the purpose of cracks, alot of games run ages better in Wine after the DRM is disabled. It also applies to Windows.

---

### Post by blueridgedog on 2009-08-28
There are lots of suggestions in this thread:

[http://www.hardforum.com/showthread.php?t=1290635&page=2](http://www.hardforum.com/showthread.php?t=1290635&page=2)

And there are plenty of places to post such a question ([http://forum.ea.com/eaforum/categories/show/38.page](http://forum.ea.com/eaforum/categories/show/38.page))

---

