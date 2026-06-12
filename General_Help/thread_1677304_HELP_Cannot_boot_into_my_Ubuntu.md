---
title: "HELP: Cannot boot into my Ubuntu"
date: 2011-01-28
forum: General Help
---

### Post by Kuo000 on 2011-01-28
Hi,
 
My laptop was a Windows XP machine. I installed Ubuntu 10.04 using wubi about one month ago, and everything has been working well until this morning.
 
Yesterday, I had some updates (found by the Update Manager) in Ubuntu, and then switched to my Windows XP to work for a while. 
 
Sadly, when I was trying to boot into my Unbuntu this morning, I failed with a single line of message at prompt: "No wubildr", and my computer just restarted itself. So I booted into my Windows XP, and everything here is working perfect just as before (I'm using it right now). I don't think I deleted anything when working in my Windows XP last time. Also, I do see two files - "wubildr" and "wubildr.mbr" in my C drive in Windows XP (just as before).
 
So, I don't know what makes me unable to load into my Ubuntu. Is it becasue that the Ubuntu undates yesterday make it incapable of finding the wubildr??? 
 
Can someone give me a hand please? I want to fix this so badly.
 
Thanks very much for any help.

---

### Post by dhysk on 2011-01-28
Ewww, I'm not to familure with wubi so I did a bit of googling..

Maybe you could try this: [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

Apparently grub has an isue and breaks it every time it updates and in that thread there is a link to a permanit fix.

---

### Post by Rubi1200 on 2011-01-28
Hi and welcome to the forums Kuo000 :-)

There are issues with GRUB updates breaking Wubi installs at the moment.

The problems and solutions are provided in the Wubi Megathread:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Look at problem #2, solution #1 or 2 should get the job done.

Don't forget to apply the Permanent Fix back in Ubuntu, including locking the grub packages.

If you need more help, let us know.

@dhysk; as you can see, Wubi issues and solutions have been consolidated into one thread and I hope you find it useful in future when helping other users.

Thanks.

---

### Post by dhysk on 2011-01-28
Thank you very much. I just found something that may help and if nothing else would bump the thread for them so poeple with more expertice, like your self, can find it ;).

---

### Post by Kuo000 on 2011-01-28
Thank you, Rubi1200.
 
The step-by-step solution is clear. I should be able to follow them, though I don't know what certain files are about. I'll try this some hours later when I get home (I don't have a Ubuntu LiveCD with me now). Hopefully the problem can be fixed.
 
Once again, thanks a lot.

---

### Post by Kuo000 on 2011-01-29
> **Rubi1200 said:**
> Hi and welcome to the forums Kuo000 :-)

There are issues with GRUB updates breaking Wubi installs at the moment.

The problems and solutions are provided in the Wubi Megathread:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Look at problem #2, solution #1 or 2 should get the job done.

Don't forget to apply the Permanent Fix back in Ubuntu, including locking the grub packages.

If you need more help, let us know.

@dhysk; as you can see, Wubi issues and solutions have been consolidated into one thread and I hope you find it useful in future when helping other users.

Thanks.

Hi,

When I tried to use the Ubuntu CD to boot, it asked me to either "Try Ubuntu without affecting your systems" or "Install Ubuntu". So I chose the first option. But this way I didn't actually boot into my Ubuntu, but instead a trial one in which I cannot access stuff on my Ubuntu. Is it the expected thing, or I should be able to boot into my Ubuntu?

Thanks.

---

### Post by Rubi1200 on 2011-01-29
You need to use the live option in order to fix the broken install on the disk.

This is normal.

All you need to do now is use the relevant commands from the Megathread to fix things and then restart the computer, taking the CD out of course, and all should be good again.

---

