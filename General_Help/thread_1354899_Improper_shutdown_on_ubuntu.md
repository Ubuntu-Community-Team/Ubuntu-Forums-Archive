---
title: "Improper shutdown on ubuntu ?"
date: 2009-12-14
forum: General Help
---

### Post by aklo on 2009-12-14
I do not have any problems right now. I'm asking this because doing some searching, seems like ubuntu is almost going to have some serious problem if there is an improper shutdown.

Personally my chance of power outage in my country is virtually 0 and i ensure a proper shutdown everytime but who know? shyt happens i'm talking about "what ifs" here. 

From some of the older post in the forums here regarding problems when there is improper shutdown, it seems extremely serious to the point of not being able to boot into ubuntu or even error before the grub screen.

This worries me. Care to try an improper shutdown on your ubuntu desktop??

---

### Post by Grenage on 2009-12-14
As with any OS, it depends what it's doing when you lose power.  Ubuntu uses a Journalled filesystem, so it's _less_ prone to corruption if it loses power.

---

### Post by Slim Odds on 2009-12-14
> **aklo said:**
> I do not have any problems right now. I'm asking this because doing some searching, seems like ubuntu is almost going to have some serious problem if there is an improper shutdown.

Perhaps you can explain your research. What makes Ubuntu any worse than any other?

> Personally my chance of power outage in my country is virtually 0 and i ensure a proper shutdown everytime but who know? shyt happens i'm talking about "what ifs" here. I also live in a country here the power is very reliable, but there are still occasional glitches that cause improper shutdowns. I've never had a problem. As was mentioned, Ubuntu has used a journaling file system for some time now. This takes care of most problems.

> From some of the older post in the forums here regarding problems when there is improper shutdown, it seems extremely serious to the point of not being able to boot into ubuntu or even error before the grub screen.How old? Before journaling file systems?

> This worries me. Care to try an improper shutdown on your ubuntu desktop??I've had it happen a few times with no issues.

If you're really so worried, why don't you just buy a good uninterruptable power supply? That's the best solution.

---

### Post by anonymtrk on 2010-01-22
Now, this is the case:

Yesterday, i tried to boot up my laptop but the battery was uncharged and it was unable to boot ubuntu karmic 64 bit. so i tried to plug the charger as soon as possible but when i looked at the screen, there was a huge black blank screen. so i had to restart it manually by pressing the power button. Now, i can see the grub screen, i can choose one of three kernels and the Windows. But only Windows can boot but the others doesn't. And also, grub timer does not work  not. It does not count down to zero and autoboot the default os. I tried to reinstall grub but everytime , i got problems. [Here]("https://wiki.ubuntu.com/Grub2") is what i tried to do. In another try [here]("http://ubuntuforums.org/showthread.php?p=8415958#post8415958"), i failed again. In chroot, i could not "apt-get install" as it said i wasn't connected to internet (but i was), and in another try, it could not find p/rmonct /mnt/etc/resolv.conf. :popcorn:

---

