---
title: "61% of RAM used as cache?"
date: 2010-10-07
forum: General Help
---

### Post by Nate_is_cool on 2010-10-07
My comp is litterly doing nothing, and 61% of my RAM is being used as cache. I don't know if I created a swap space correctly. I loaded up gparted and I see that I do have a 2gb partition labled linux-swap. Why am I completely out of RAM? I have 4gb btw

I think its broken..

---

### Post by sanderd17 on 2010-10-07
So you say: when your computer doesn't execute a process, you still have a ram usage of 61% and a swap usage of 0%?

well, that's normal. It isn't because he isn't calculating anymore that he has to write everything to the hard disk (aka swap partition).

---

### Post by Nate_is_cool on 2010-10-07
So your trying to tell me that after an hour of not being touched, an idling computer should 66% of its ram in use as cache. 

Thank you for the response, but I have been working on computers a long time, and I know that this isn't normal.

---

### Post by sanderd17 on 2010-10-07
Ok, 61% of 4g is a lot. But your pictures show less than 61%. What apps are using the ram so much?

---

### Post by oldos2er on 2010-10-07
Looks fine to me. If you're coming from a Windows background, understand that Linux uses RAM in a very different manner. Here's an explanation: [http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage](http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage)

---

### Post by Nate_is_cool on 2010-10-07
> **sanderd17 said:**
> Ok, 61% of 4g is a lot. But your pictures show less than 61%. What apps are using the ram so much?

Look at the desktop on. I scrolled over the icon bar. it says 66% as cache.

attached is a picture of hw monitor

---

### Post by NightwishFan on 2010-10-07
Dont Panic!!! :D [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

That is desired and expected behavior, in fact it is putting all 6gb of your ram to epic good use! Enjoy.

---

### Post by sanderd17 on 2010-10-07
Isn't the cache memory the internal memory of the CPU? I didn't know there were tools that displayed it since it's almost always filled.

---

### Post by NightwishFan on 2010-10-07
No, it is cached ram for use by the system in Linux. The cpu cache is something different. If any program needs the ram, the cache will be emptied to let the program make use of free ram. Essentially cached ram is free, just making use of empty ram to improve performance.

---

### Post by CharlesA on 2010-10-07
> **NightwishFan said:**
> No, it is cached ram for use by the system in Linux. The cpu cache is something different. If any program needs the ram, the cache will be emptied to let the program make use of free ram. Essentially cached ram is free, just making use of empty ram to improve performance.

Yep.

If you really want to know how much is being used as cache, run this in a terminal:

```
free -m
```

---

### Post by skogs on 2010-10-07
Can we please get the original poster to mark this as [SOLVED]....  

And, as a side note to the OP, Windows 7 also performs in a similar fashion.  It only took Redmond a couple of decades to figure out that yes, you can write something to disk and still remember it later without having to wait for a disk read of something you may or may  not have used 10 seconds ago.  

It is indeed very normal Linux/Unix behavior...and is now quite normal in Win7.  If you are worried, we also promise that in case you actually try to do something with that memory...it will release it and do whatever you need.

---

### Post by Nate_is_cool on 2010-10-07
i have not the slightest clue as how to do that

---

### Post by NightwishFan on 2010-10-07
Its easy, thread tools at the top, mark as solved. Hope you got your answers! Happy Ubuntu-ing.

---

