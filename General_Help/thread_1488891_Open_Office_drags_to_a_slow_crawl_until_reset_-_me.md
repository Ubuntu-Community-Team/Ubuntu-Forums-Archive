---
title: "Open Office drags to a slow crawl until reset - memory leak?"
date: 2010-05-20
forum: General Help
---

### Post by LancerNZ on 2010-05-20
I'm writing a book with a number of illustrations and have very tight deadlines. Since moving from a Dell D620 running an old and faithful Ubuntu 8.10 with OpenOffice 2.4 to a bigger Dell M6300 running the new Ubuntu 10.04LTS with OpenOffice 3.2 I have noticed that writing my documents slows down after a while. In particular, scrolling through pages becomes a laggy drag and if I do so, I am often faced with greyed OpenOffice window while OpenOffice catches up.

Saving and restarting OpenOffice seems to work fine, bringing it back up to speed when I load in the document anew, but it's not long before Open Office begins to crawl again.

I have since disabled Java thinking it might speed things up. I thought it did speed things up at first, but the laggy drag still seems to be happening.

Looks to me like the Ubuntu OpenOffice package has some kind of a memory leak.

---

### Post by tgalati4 on 2010-05-20
Open a terminal:

sudo apt-get install htop
htop

Watch htop along side your document.  See if there is a RAM issue or a CPU load issue over time.

How much RAM in your system?  How big is your swap drive?
When OO is running slow, post the output of:

free

---

### Post by shane2peru on 2010-05-21
I have noticed that OO.o has become extrememly slow as well if working with a larger document.  It takes me almost 10 minutes to open a document that is 4mb in size.  Granted I know that is a large document, however it used to open in 1-2 minutes, I never timed it, but it was certainly less that the 10 minutes it now takes.  I have 4GB or ram and 5GB of swap, ram shouldn't be an issue, same machine, only differences in Lucid! and updated OO.o.  Here is my free after 5 minutes of opening the document:
```


free -m
             total       used       free     shared    buffers     cached
Mem:          3962       1836       2125          0        124        673
-/+ buffers/cache:       1038       2923
Swap:         5239          0       5239

```

Any help for this would be greatly appreciated!

htop tells me it has been opening the document for 12 min, one of my two cpu's is at 99% Mem is at 3.2% I'm not sure who's fault this is, but there is a problem.

Shane

---

### Post by shane2peru on 2010-05-21
I just opened this same document in OpenSuse 11.2 (got to love a dual boot setup) and it opened in a mere 30 seconds or so.  It was very fast opening compared to trying to open this in Ubuntu.  I really hoped this get's sorted out and fixed soon.  I guess I'm off to file a bug report.

Shane

---

### Post by gruntlips_ on 2010-05-23
I have the same problem. If I have two calc spreadsheets open at once, after awhile my cpu bounces around near 100% and things get really slow. If I close them and reopen they are fine for awhile and the same thing happens again. My memory usage remains low the entire time.

10.04 (clean install!)
serval (serp4), 2.5 core 2 duo
4 gig ram, 2 gig swap

---

### Post by gruntlips_ on 2010-05-23
A quick poke of mr. googles reveals...

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/411542](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/411542)
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/462487](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/462487)

Use top to see what is hijacking all the cpu with open office open. For me it was xorg. I disabled anti-aliasing in open office prefs under base and it stopped. Maybe this is different for you but top is a good place to start.

- gl

---

### Post by LancerNZ on 2010-05-23
> **tgalati4 said:**
> Open a terminal:

sudo apt-get install htop
htop

Watch htop along side your document.  See if there is a RAM issue or a CPU load issue over time.
It seems to be both. When OO Writer slows down, and I scroll (this triggers it off badly when it's happening) my Memory is way up there, and the CPUs both pump up and down taking turns from 0-100%.

[ATTACH]157990[/ATTACH]
***htop - click thumbnail for full size.***

...look at that big root process! When OO is having this problem, root causes a massive CPU spike from /usr/bin/X. I'm not sure why this is happening. Even if I like wobbly windows I don't think OpenOffice should have permission to make root take this extreme. But sure enough, scrolling in OpenOffice makes that process jump right up there, then it calms down when the scrolling has stopped.

> **tgalati4 said:**
> 
How much RAM in your system?  How big is your swap drive?
When OO is running slow, post the output of:
free

```
lancer@lancer-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       3613096    2856676     756420          0     135660    2068092
-/+ buffers/cache:     652924    2960172
Swap:     10584056       1340   10582716
```

Disabling Java in OpenOffice does seem to have helped in making it less frequent. However, if I leave OpenOffice on for any good time with a large document loaded, it's a matter of when.

---

### Post by shane2peru on 2010-05-25
I realize that you all have a bit of a different problem than I had.  However I removed all of openoffice that came with my install and installed straight from OpenOffice.org's web page, and waaahhhlllla  Everything is great!  This would be one of thos try this at your own risk things, but really helped my issue.  OpenOffice.org has installation instructions on their web page:  

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Those are what I used.  Worked like a champ. 

Shane

---

### Post by Engphyzer on 2010-06-03
Hi I have the same problem with sluggish OOo impress. I disabled both anti-aliasing and "hardware acceleration" and it helped a lot,  though it's not as fast as I would have liked still. 

I am on a fairly ancient laptop without any dedicated memory for graphics accelerator. That may be why.

In case anyone's wondering, that's Tools -> options -> openoffice.org -> view -> graphics output  -> use anti-aliasing (uncheck)

---

### Post by COKEDUDE on 2010-07-24
I am also having this problem with a 7 page doc file that has a lot of images.

---

