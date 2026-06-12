---
title: "Incrimental CD writing"
date: 2011-12-09
forum: General Help
---

### Post by chejose on 2011-12-09
It has been a few years since I used Windows, but I remember we had a program (can't remember the name) where we could add a file to a CD, set it aside, and then later add another.

I find that what I have found on Google mostly confusing, so bring up the subject to you. Is there something for Ubuntu that would do that? Something fairly simple, for someone out of the geek class?

Thanks for your suggestions.

José

---

### Post by mike555 on 2011-12-09
if you use a cd-rw you should be able to do that with your burning software , just don't finalize it.

---

### Post by chejose on 2011-12-09
Very good Mike, but...

I do all my CD work with K3b, but cannot see how to implement your answer.

Can you give me more help?

José

---

### Post by mcduck on 2011-12-09
> **chejose said:**
> It has been a few years since I used Windows, but I remember we had a program (can't remember the name) where we could add a file to a CD, set it aside, and then later add another.

I find that what I have found on Google mostly confusing, so bring up the subject to you. Is there something for Ubuntu that would do that? Something fairly simple, for someone out of the geek class?

Thanks for your suggestions.

José

It's called "packet writing". I've seen some ways to add the support for that on Linux, but since such disks have lots of compatibility issues it's never really been popular enough to get much of support. (disks written that way tend to only work correctly when used on a computer that has exactly the same packet writing software installed, and aren't usually playable on other systems or any other devices than computers)

There's an old (really old!) guide on the forums about packet writing here: [http://ubuntuforums.org/showthread.php?t=129093]("http://ubuntuforums.org/showthread.php?t=129093"). But the best bet would be to just search gogole for "linux packet writing" and hope you find something that's not too outdated...

What Mike descibed above also allows you to add some more data to the disc afterwards, but any previously written data can't be removed or changed (not even on a CD-RW dic). And it also has comaptibility problems, unfinalized discs dont' work on other devices than computers and even with computers they might not always work correctly. Such discs can be done simply by setting you CD writer application to not finalize the disc, or set it to "session" mode. What it's actually called depends on the program.

I wouldn't recommend either method for writing discs that you'd want to be sure to be able to read afterwards (definitely not for bakcup purposes), or that you wish to send to some other person

---

### Post by chejose on 2011-12-09
Thanks mcduck... from what I could understand on Google the situation was something like that.

Every so often I run into a short video (from Wimp, for example) that I would like to keep but would be a waste of a whole CD.

Maybe someone will come up with a new twist in the future.

José

---

### Post by mcduck on 2011-12-09
Somebody already did, too bad it didn't gain much popularity. :/

The DVD-RAM is designed to be used like a hard drive instead of like other optical medias, allowing you to add, remeove and change individual files on it as you wish. And since that's part of the spec it had no compatibility issues (apart from the obvious one that it didn't really break through at all).

Luckily empty CDs are rather cheap, and of course you could wait until you have a full CD's worth of material before you burn it to disc..

---

### Post by satanselbow on 2011-12-09
> **chejose said:**
> 
I do all my CD work with K3b, but cannot see how to implement your answer.


When you hit the "burn" button in k3b the dialogue box that pops up will offer you a whole host of options; "start multisession", "continue multisession", "finalize multisession" etc - how did u miss them? :D

May only work on CD's though - DVD may not comply :(

---

### Post by chejose on 2011-12-09
Hmmm... that is interesting. The reason I "missed" them is I did not know what they meant. So I will investigate.

---

