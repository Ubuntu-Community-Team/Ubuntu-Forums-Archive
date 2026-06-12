---
title: "firefox using 690 mb ?"
date: 2011-03-12
forum: General Help
---

### Post by sdowney717 on 2011-03-12
why does firefox suck up so much memory?
in just a few minutes look how it jumped up

---

### Post by lithopsian on 2011-03-12
Why shouldn't it use 690MB?  How much memory have you got?  And what were you doing in Firefox?  And which Firefox version were you running?

---

### Post by sdowney717 on 2011-03-12
2gb

I have perhaps 25 tabs open

In the past I have simply killed the firefox process dead
then restart to free up memory.
I will show you, I will kill it and restart to bring up all the pages and see how much it uses then.

---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-12
how do i find System monitor in ubuntu 10.10?

---

### Post by sdowney717 on 2011-03-12
ok finished reloading and now is only 354mb

---

### Post by sdowney717 on 2011-03-12
right click the top panel and select add to panel, then select system monitor

---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-12
> **sdowney717 said:**
> right click the top panel and select add to panel, then select system monitor
thanks, i dident know about that :P i was using the "top" command in terminal till now xD

---

### Post by thunderbirdje on 2011-03-12
> **sdowney717 said:**
> 2gb

I have perhaps 25 tabs open

In the past I have simply killed the firefox process dead
then restart to free up memory.
I will show you, I will kill it and restart to bring up all the pages and see how much it uses then.

I think it's normal given the 25 tabs... The new(er) generation of browsers opens a new (sub)process. One of the advantages is the "crash safety" of the other opened tabs when one of them just "freezes" to explain it simple. The other side of the story is of course that every tab needs his/her (? ;-)) own "memory space".

To be sure do a test: open just one tab and check the used memory. ;)

---

### Post by markeee on 2011-03-12
> **thunderbirdje said:**
> I think it's normal given the 25 tabs... The new(er) generation of browsers opens a new (sub)process. One of the advantages is the "crash safety" of the other opened tabs when one of them just "freezes" to explain it simple. The other side of the story is of course that every tab needs his/her (? ;-)) own "memory space".

To be sure do a test: open just one tab and check the used memory. ;)

yea i think this is about right, maybe try having less tabs open!!

I can't stand having that many tabs open, makes it feel cluttered and well not for me :)

also what version of firefox, there were in some releases issues with memory leaks iirc

---

### Post by lithopsian on 2011-03-12
So you are running 25 instances of the most complex applications on your machine and you think that memory use is excessive?  Firefox is designed to use big chunks of memory, assuming you have a lot of memory, so that it is fast.  Would you rather it used 32MB of your several GB of RAM and takes 30 seconds to load every page?  Firefox 4 (release candidate 1 now out) uses even more memory than 3.6 but is significantly faster, sometimes radically faster.  A step forwards or a step backwards?

I notice you are also running a plugin container, probably Flash.  Who knows what it is doing.  Flash programs are renowned for memory leaks and bugs, that's why they've been farmed out into a separate process.  Look how much memory it is using, for I'm guessing, one Flash instance?

Are you also going to complain about how much memory Chrome is using, because it looks like a whole lot more than 690MB?  For a whole lot less than 25 tabs?

BTW, my Firefox never uses that much memory, presumably because I don't have that much memory.  Be thankful that you are probably getting faster performance than me because so much stuff is getting cached.

---

### Post by Frogs Hair on 2011-03-12
Memory use in increases in every browser when using multiple tabs , benchmarks available on a number of sites.

---

### Post by sdowney717 on 2011-03-12
point is I wonder about memory leaks.
I tend to almost never close Firefox and simply open and close tabs.
When the memory use gets too high, the computer acts glitchy.
I have noticed killing Firefox and restarting the glitchiness is gone for a while.
using Firefox 3.6.15

---

### Post by Frogs Hair on 2011-03-12
I found a leak testing procedure for earlier versions of Firefox , but nothing current. Here is the generic checklist for high memory use. [http://support.mozilla.com/en-US/kb/high%20memory%20usage](http://support.mozilla.com/en-US/kb/high%20memory%20usage)

---

### Post by sandyd on 2011-03-12
I *think* its just becasue of the nature of firefox to be heavy.

In the latest Firefox 4 version, it goes 600mb+ by the time you reach 15-16 tabs. That is, with full adblockers, flashblock on.

---

