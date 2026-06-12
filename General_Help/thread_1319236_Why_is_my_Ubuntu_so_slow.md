---
title: "Why is my Ubuntu so slow???"
date: 2009-11-08
forum: General Help
---

### Post by madmax.santana on 2009-11-08
I am not using an Intel 8086... I am using an HP HDX 16 laptop which has 4Gig of RAM and a dual core processor... I was inspired with linux as I heard it never gets stuck or slowed down and it doesn't even crash... wooah!
I have been using linux for a month now... It pretty well crashed some time back and it wouldn't run.. I selected the recovery mode at startup and then it ran perfectly... Then it got stuck probably a dozen times in the past 24 hrz. Once stuck for about 15 minutes... No clicks would work, terminal wouldn't open, you know, dead desktop. And now, it is going real real slow, like when I type something, it takes at least 2 seconds to dislplay the character and when i move the mouse, it moves like a real low fps video. Music is playiing in the background, it plays and pauses and plays and pauses... Why do I feel like I am using an Intel 8086??? Even Vista full of viruses runs better than that on a 666MHz processor with 48MB RAM... <Just a 
What's wrong with it??? Or is it a mistake on my part...

Let me again list my related system specs...
Processor: Intel Core2Duo 2.20Ghz (T6600)
RAM: 4GB DDR3
Video Card: nVidia GeForce 9600M
OS: Ubuntu Jaunty Jackalope (9.04)

---

### Post by madmax.santana on 2009-11-18
No replies so far... Seems like no one is interested in making Ubuntu better. So I guess I must mark this post solved and simply quit Ubuntu.

**EDIT**
I take my words back. I never meant them... Just to motivate a few people to post a possible reason of the problem I was facing. Thread is solved and closed anyway... Happy ending...

P.S. I never quit Ubuntu, never will... :)

---

### Post by girto on 2009-11-18
> **madmax.santana said:**
> Seems like no one is interested in making Ubuntu better.

The Ubuntu community and developers are making Ubuntu better, release after release.

I hope you're not assuming that making Ubuntu better revolves solely around solving someone's specific problem which might be due to hardware issues, misconfiguration, user blunders, or some other odd issue.

You could check for a start what process is eating CPU cycles either by launching the graphical system monitor from the menu, or firing up a terminal and typing:
```
top
```

On the other hand, you seem to have sorted out this issue by marking the thread as solved.

---

### Post by SteveHillier on 2009-11-18
> **madmax.santana said:**
> No replies so far... Seems like no one is interested in making Ubuntu better. So I guess I must mark this post solved and simply quit Ubuntu.

I doubt it is a case of no-one being interested.  It might just be that no-one has come across the problems you are reporting and therefore are in no position to help.
I read a lot of threads in this forum, many of which I would like to help if I knew the answer, but often I find it useful to view the thread in case the replies solve issues I have.
Many thanks to girto for pointing out 'top'.  See what is hogging the processor and then see if there is more specific help, if need be post the output on this forum and see if you get a response.  
I have found people will help you if they can.  Most forum users are like yourself, people seeking answers themselves.

---

### Post by roke24 on 2009-11-18
That version of Ubuntu have some problems with Intel MoBos, should upgrade to 9.10, even look for another distro, this week have arrived OpenSuse and Fedora, is not just about Ubuntu, its about the freedom to experiment in the way you wish that Linux gives you. Sorry if I cant tell you a more technical response, im just a newbie like you.

---

### Post by madmax.santana on 2009-11-19
No offense intended guys, please do not mind. I cannot think about quitting Ubuntu and moving back to that @#!*$% Microsoft Operating System. Actually my PC was working real slow and I needed a quick overview of what is happening, but did not receive any comments. Sorry about that but it was just a motivational sort of thing ;)... I thought if I put a line like that, more Ubuntu lovers will try to answer that... And see, 4 posts in one day.

Thanks all. I really didn't intend any offense, and I am still using Ubuntu. It might have gone slower, but is definitely better than Windows. I take my words back...

As I have deduced, the problem arose due to zero swap partition. I had no idea about swap thing before. I knew about  paging memory but I very recently heard that it is the same as the swap area on HDD... Thanks pals. Once again sorry if I hurt you emotions... ;)

---

### Post by girto on 2009-11-19
> **madmax.santana said:**
> ... I thought if I put a line like that, more Ubuntu lovers will try to answer that... And see, 4 posts in one day.

You can trust me on that your line was not the main motive behind my reply. It was rather a stroke of luck that your post was in the 1st couple of pages of this forum when i visited, and i thought i had a suggestion to give. Threads get buried deep quite quickly, and would not be visible to many.

I am glad you found out by yourself the cause, as this shows good determination. I wouldn't have thought about swap partition since normal installations get a swap partition allocated automatically (and hence my allusion regarding misconfiguration).

Happy Ubuntuing :D

---

