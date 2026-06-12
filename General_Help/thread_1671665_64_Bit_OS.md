---
title: "64 Bit OS"
date: 2011-01-20
forum: General Help
---

### Post by JoeFriday49 on 2011-01-20
I am considering a new PC purchase and was considering going with a 64 bit processor, so I thought I'd look into our forum here for some advise.  It seems that the last post in the 64 bit folder was well over a year ago and I'm perplexed.  Does that mean that no one ever has a problem with a 64 bit Ubuntu build, or does no one use 64 bit Linux?

It appears that when the last posts came along they were discussing the lack of a browser and flash player plug-in's...  Guess all that has been resolved?

---

### Post by cascade9 on 2011-01-20
Not many x86 CPUs around now that arent 64-bit capable. You can still use 32bit if you want. 

Theres been browsers for 64bit for years. Adobe has never realsed an 'offical' 64bit linux flash player, but there has been betas, and now there is flashplayer 'square'. A member here (lovinglinux) has written a firefox add-on called 'flash-aid' which will install/update flash on 64bit ubuntu systems, if you dont want to manually install flash.

---

### Post by TBABill on 2011-01-20
I think if you search the forums  you'll find few posts that are specific to only 64 bit or only 32 bit. People run one or the other, but I don't often see an issue that is one way in 32 bit and another in 64 bit. And the mix of 32 and 64 bit users is much greater than before. That forum was closed out after (during?) Karmic (9.10) if memory serves me correctly. 
 
These days I'd just suggest trying the one you want to use most and if it doesn't suit your needs then try the other. I run only 64 bit on every machine I own and Flash performance is great for me. But others have had different results, often because some people run Flash from the repos and that's only 32 bit. You have to get 64 bit Flash from the repos and, as stated in the post above, Flash Aid makes it a simple task. It's a Firefox extension and a quick search of "Flash Aid" on Google will provide the link.

---

### Post by aaaantoine on 2011-01-20
Virtually every modern x86 CPU supports 64-bit instructions.  It's your choice whether you want to use i386 or x86_64.  As of late, I've suffered very few headaches from using 64-bit, but I've suffered even fewer from using 32-bit.  If your PC has more than 3GB RAM* and you want to utilize all of it, then use a 64-bit OS.

When it comes to supporting 64-bit Linux, Flash is really the worst offender because of how common it is and because it's used as a plugin rather than a complete app.**  The situation was worse when I started using 64-bit in 2007.  Nowadays, it installs fine, because a lot of work has gone in around the package to make it install easily on 64-bit.  In my experience, however, there is a noticeable performance hit when using 32-bit Flash on a 64-bit OS.

[size=1]*32-bit only supports ~4 billion addresses, so usable RAM typically falls somewhere between 3 & 4 GB depending on, say, the amount of graphics memory in your system.

**There are a number of other popular programs that are exclusively 32 bit (the Skype client comes to mind), but there are packages available -- if not installed by default -- that allow you to run i386 programs on an x86_64 OS.  The difficulty of Flash is that it's a 32-bit plugin running inside a 64-bit browser.[/size]

---

### Post by cascade9 on 2011-01-20
> **aaaantoine said:**
> Virtually every modern x86 CPU supports 64-bit instructions.  It's your choice whether you want to use i386 or x86_64.  As of late, I've suffered very few headaches from using 64-bit, but I've suffered even fewer from using 32-bit.  If your PC has more than 3GB RAM* and you want to utilize all of it, then use a 64-bit OS.

When it comes to supporting 64-bit Linux, Flash is really the worst offender because of how common it is and because it's used as a plugin rather than a complete app.**  The situation was worse when I started using 64-bit in 2007.  Nowadays, it installs fine, because a lot of work has gone in around the package to make it install easily on 64-bit.  In my experience, however, there is a noticeable performance hit when using 32-bit Flash on a 64-bit OS.

[SIZE=1]*32-bit only supports ~4 billion addresses, so usable RAM typically falls somewhere between 3 & 4 GB depending on, say, the amount of graphics memory in your system.

**There are a number of other popular programs that are exclusively 32 bit (the Skype client comes to mind), but there are packages available -- if not installed by default -- that allow you to run i386 programs on an x86_64 OS.  The difficulty of Flash is that it's a 32-bit plugin running inside a 64-bit browser.[/SIZE]

32bit PAE kernels support more than 4GB, you dont _have_ to use 64bit to get 4GB+. 

AFAIK, the 64bit flash plugins arent 32bit at all, but native 64bit. The days of using a 32bit flash version with a 64bit linux OS are over...(well, unless you insist on getting the 32bit flash in the ubuntu repos).  

In my experience, even the 'beta' 64bit flash versions work as well as 32bit flash on 32bit linux ever did.

---

### Post by cascade9 on 2011-01-20
I didnt think I hit the 'post' button twice...oh well, at least it was only a double post. :lolflag:

---

### Post by TBABill on 2011-01-20
+1 on Flash. Yes, if you install the flash plugin from the repo you get 32 bit Flash on a 64 bit OS, but I would normally install ubuntu-restricted-extras, then remove flash and open java, then install Adobe Flash (by way of Flash Aid) and Sun Java plugins. Takes just 1-2 minutes to get all the codecs sorted out that way. And Flash performance in 64 bit is great....but that hasn't always been the case. Not so long ago Flash was horrible on 64 bit, but Adobe stepped up and improved the product. And those who still have an issue can usually solve it by right clicking on a video and un-checking "enable hardware acceleration".
 
Phoronix ran a test using a standard 32 bit Ubuntu kernel, 32 bit PAE Ubuntu kernel and 64 bit kernel. 64 bit was faster in every test. Sometimes not by much, but it always won in every test. And I run it on a machine with 1GB RAM and another with 4GB...great performance on both. 
 
I also have great results with 32 bit on all my machines. Not a thing wrong with using it. I just "feel" a slight edge on the desktop with 64 bit, but I have not run tests to provide numerical results. I figured if all my hardware is 64 bit capable I may as well see how it runs a 64 bit OS and they all do well with it so I'm sold on 64 bit until I find a reason not to be.

---

### Post by oldos2er on 2011-01-20
The 64-bit subforum was closed quite awhile ago; that's why there are no new posts.

---

### Post by Slim Odds on 2011-01-20
> **oldos2er said:**
> The 64-bit subforum was closed quite awhile ago; that's why there are no new posts.

Shouldn't be too long before the 128-bit sub-forum starts up.... :D

---

### Post by JoeFriday49 on 2011-01-25
Thank you one and all...  I feel a lot better now  ( :

---

