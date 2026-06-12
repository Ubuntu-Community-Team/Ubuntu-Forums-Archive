---
title: "Swap resized"
date: 2012-09-03
forum: General Help
---

### Post by Jedcurtis on 2012-09-03
Hello all,
When I installed 12.04 Precise 64bit, I created a 16Gb swap partition.  I know, I'm an idiot!  After months of use, I never once saw the swap use more that about 300kb of hd space.  Because of this, I shrunk the swap partition down to 4Gb.  I didn't want to eliminate it altogether as I've read this can cause problems.  (I have 8Gb of Ram and really believe that I don't need a swap partition!  Am I wrong?)  I've never seen the Ram utilization surpass 30 percent!
I now have an unused 10.9Gb partition that isn't being utilized.  For my humble use of Linux, I would just like to add that unused space to /home.  Is this even possible?  As you can see from the screen shot, I have a 256Gb SSD drive.  I take lots of pic's using a DSLR, and space for me is paramount.  Any help or advice appreciated...
Thanks for the help...

Jed

PS, it is the one with the distro label I'm questioning about.  I was originally going to use it to install and experiment with other Linux distros...

[IMG]http://www.jedsdesk.com/tmp/partitions.jpg[/IMG]

---

### Post by mcduck on 2012-09-03
Sure, it is possible to add that space to your /home partition, but because the space is located inside the extended partition, and the root partition sits between the free space and your /home, it's going to take a bit of work.

First you'll need to delete the empty aprtition you have (sda6, I suppose?). Then you can shrink the extended partition to only fit the swap inside it, after that move the root partition forward (or grow it to sue the free space before it, and then shring it again to free the same amount of space after the /).

...and after all that you should finally have the free space next to your /home partition, and you can grow the /home to use that space. :)

What comes to needing a swap partition, I recommend having at last some swap space as it's suefull for some meory management tasks, and also ecause some programs might actually want one. And with the proce of drive psace allocating a few gigabytes for swap sure ins't a problem. But unless you want to hibernate the machine, you most liekly won't need more than a minimal amount of swap available. (if you *do* want to hibernate, you need at least as much swap as you are using RAM at the moment you hibernate the machine. So in that case having at least as much swap as you have RAM installed would be a good idea.)

---

### Post by Jedcurtis on 2012-09-03
So am I assuming correctly that I need to boot with the LiveCD and use gparted in order to accomplish this?

Thanks again...

Jed

---

### Post by HermanAB on 2012-09-04
Note that moving partitions around may lead to a loss of all your data if something goes wrong.

Also bear in mind that the swap partition is used to save a machine state and RAM image when you suspend the machine.  If you don't use suspend then fine, shrink the swap space, but if you do want to use suspend, then your swap space needs to be twice the size of the RAM.

---

### Post by NikTh on 2012-09-04
> **HermanAB said:**
>  but if you do want to use suspend, then your swap space needs to be twice the size of the RAM.

Hello , 

I think that is not a rule. I have 4GB of Ram and 3GBs of Swap and suspend just fine. 

**free -m**
```
             total       used       free     shared    buffers     cached
Mem:          3629       1850       1779          0         82       1131
-/+ buffers/cache:        635       2993
Swap:         3030          0       3030
```I think it needs over 2Gbs of swap for suspend ( like suspend-to-disk , Hibernate)  , **but again , its not a rule. **

OP yes , the method you mentioned is correct . Boot from a LiveCD/Usb and shrink swap and then you can merge the space into your Ubuntu partition if you want.

You just be aware that UUID **maybe** change,  so at next reboot no swap will detected. If that happen,  you must change the line in /etc/fstab  accordingly to the result of ```
sudo blkid
```Thanks

---

### Post by mcduck on 2012-09-04
> **NikTh said:**
> Hello , 

I think that is not a rule. I have 4GB of Ram and 3GBs of Swap and suspend just fine. 

**free -m**
```
             total       used       free     shared    buffers     cached
Mem:          3629       1850       1779          0         82       1131
-/+ buffers/cache:        635       2993
Swap:         3030          0       3030
```I think it needs over 2Gbs of swap for suspend , but again , its not a rule. 

OP yes , the method you mentioned is correct . Boot from a LiveCD/Usb and shrink swap and then you can merge the space into your Ubuntu partition if you want.

You just be aware that UUID **maybe** change,  so at next reboot no swap will detected. If that happen,  you must change the line in /etc/fstab  accordingly to the result of ```
sudo blkid
```Thanks
It definitely isn't the rule (swap twice the RAM was the rule for swap space when the amount of RAM in computers was less than 1GB and the swap space was actually often needed.)

Suspending (as in "suspend-to-RAM") doesn't need any swap at all. Hibernating does, and it needs as much swap as you have data in RAM at the moment. So if you have 4GB of RAM, and 1,5GB of it it in use when you try to hibernate the machine, you'll only need the 1,5G of swap, not 4GB. But of course if you have 4GB of RAM then you should set up your system in a way that actually allows you to use all the RAM and still hibernate if you want to, therefore you should have as much swap as you have RAM installed.

---

### Post by dcstar on 2012-09-04
> **NikTh said:**
> Hello , 

I think that is not a rule.
.........

You are so correct. It is a massive problem when someone who believes that they can write "HOWTOs" dispenses totally incorrect information like this.

Makes you wonder what other incorrect information some other person may be given.

---

### Post by NikTh on 2012-09-04
> **mcduck said:**
> 

Suspending (as in "suspend-to-RAM") doesn't need any swap at all. Hibernating does, and it needs as much swap as you have data in RAM at the moment. .


I didn't clarify this and you are so correct. I meant suspend-to-disk. aka Hibernate. 

I will correct this in my post. 

Thank you.

---

### Post by Jedcurtis on 2012-09-04
OK, to alleviate all of your concerns regarding suspend/hibernate issue, I never use either.
Also, that said, I have 8Gb's of Ram.  This is why I have shrunk the Swap to 4Gb's of space, and I'm not averse to shrinking it further to get the space back.  As my first post shows, the Swap is situated as the first spot on the partition.  I'd just like to reclaim some of the space as I'm using a laptop with a 256Gb SSD drive.  My original intent was to use the 'reclaimed' space to make a mount point where I could install other Linux distros to experiment with.  I'm not a Linux pro, so I think I've given up on this idea in favor of just adding the 'reclaimed' space to /Home.
So, if someone could do like a step by step for me I'd greatly appreciate it.  I do understand I'll have to use my boot/live CD to do all this.  Originally when I installed Ubuntu this time, I set it up with the / and /Home separated so the next time I upgraded I wouldn't lose any settings or have to reinstall anything.  I know now that I may still have to reinstall some things, but that is fine so long as documents, music, pictures and such are all still there after a potential upgrade.
A new mount point using the 'reclaimed' space from my Swap to do the different distros would still be highly desirable!  However if it is beyond my skill level, I'd be happy to just be able to get the space back into my /Home.
So many answers in such a short time!  Your all great!
Thanks again,
Jed

---

