---
title: "Ubuntu will not boot up (recurring issue)"
date: 2010-03-24
forum: General Help
---

### Post by ironstove on 2010-03-24
Hello, I am having an issue where when I select ubuntu to boot from GRUB, instead of booting up to the ubuntu logo, I simply get a black screen with a text cursor and nothing happens. I have tried to boot into recovery mode, but all that happens is a bunch of text lines (which I don't know the meaning of) span across my screen, stops, then does nothing after that.
 
I originally installed ubuntu using the version 9.10 ISO.
 
I am running a dual boot with windows 7 pro on an ASUS A2K laptop and I have had this exact same issue before in the past when I was running a dual boot with XP pro. I was unable to figure out the cause of the issue or how to solve it, so I gave up and reformatted/reinstalled windows 7 then ubuntu and things were working fine for a few months (about the same amount of time things functioned when I had a windows XP dual boot), but today I tried to log into ubuntu again and I got the problem mentioned above. 
 
There are two things which I noticed in common with the last time this issue occurred:
 
1. I had not logged into ubuntu in a while (Maybe a week +)
 
2. I had installed a large file on my windows partition (ORCAD 16.3 which is 2 GB+)
 
I do not know if this is relevant, but I also want to point out that this laptop was originally a french laptop (with a french windows XP) which I reformatted to install english versions. Also, the laptop has a 64-bit processor, but I have 32-bit windows 7 and 32-bit ubuntu installed (I looked online and I read that this wasn't an issue at all, I mainly did this because I only had 32-bit install discs available to me at the time). 
 
I can boot into windows 7 perfectly fine still and I had both operating systems working for a few months before this problem occurred as with the last time this happened. I would like to know if anyone knows what the problem might be and if it is solvable because I am thinking about changing laptops since my friend has the EXACT same setup as me (even used the same ubuntu/windows 7 disc) but has never had this problem occur for him because it is becoming a real problem how all of my schoolwork on my ubuntu partition keeps getting wiped since I can't access it and have to reformat in order to get ubuntu working again (as far as I know).
 
If anyone can help me or point out the problem I would be extremely grateful.

---

### Post by kamaji792 on 2010-03-24
Not a great deal of help but...

You may be able to use a live CD to let you look at your system and extract files (copy them to a USB) when you can't log in properly.

Best of luck with the rest of the problem. I wonder if it could be a hardware problem with you disk?

All the best

---

### Post by ironstove on 2010-03-24
Hello again,
 
I attempted to install ubuntu within windows and when I restarted and booted GRUB, I selected the windows over the unbootable ubuntu partition.
 
I was then prompted to select whether I wanted to boot into windows 7 or the ubuntu I had just installed. When I initially selected ubuntu, the computer went to a black screen then immediately shut down and restarted. 
 
I then repeated the steps and when I selected the newly installed ubuntu again, the black screen popped up again and I was given this message:
 
"Try (hd0,0):NTFS5: no wubildr"
 
Does anyone know why I might have gotten this error message? I did not want to create a new thread since the previous problem might be related.
 
Thanks again.

---

### Post by isyan on 2010-03-24
if you're using wubi 9.10 try this...

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by ironstove on 2010-03-25
Wow, as a matter of fact, I am using 9.10. 
 
I will look into this solution, but I have a quick question: What if I download and install a version above 9.10? Would that eliminate the chances of this problem reoccurring? Because I have a version 9.10 install disc, so I suppose I could just download the latest ISO and use that as my install disc.
 
But anyway, I will try out the solution listed in the article and get back to you. Thanks a lot for the help, I realize that I did not even list the version of ubuntu which was a very silly thing for me to do. I will edit that in for future users incase they run into the same problem.

---

