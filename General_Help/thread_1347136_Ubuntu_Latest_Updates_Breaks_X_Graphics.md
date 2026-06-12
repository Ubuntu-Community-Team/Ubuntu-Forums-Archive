---
title: "Ubuntu Latest Updates Breaks X Graphics?"
date: 2009-12-05
forum: General Help
---

### Post by dlandis on 2009-12-05
I have just a basic Ubuntu, latest release and just today the Update Manager automatically checked for updates as usual. I installed the recommended updates including I think a new kernel image or something. It asked me to reboot now or later. I said later and then shutdown after a while. Now I start up and I get this error about:

"ubuntu is running in low-graphics mode"

(EE) config/hal: couldn't initialise context: unknown error (null)
ddxSigGiveUp: Closing log

---

### Post by fluffman86 on 2009-12-05
Um, "ubuntu is running in low graphics mode" is not meaningless.  When you upgraded your kernel, kernel upgraded, but apparently your graphics driver didn't.  

1. Complain to the company that released the proprietary driver.  If they would Open Source the driver, then ubuntu would be able to keep it updated easier.

2. Go to System > Admin > Hardware Drivers and see if there are some new ones.

3. If all else fails, hold shift (in karmic) or press ESC (in Jaunty or if you upgraded from Jaunty) while your computer is booting and select the previous kernel.

4. Go to System > Administration > Software Sources > Updates, and uncheck the "Pre-Released" and "Unsupported" updates.  Those are really for testing purposes, and could be why your graphic card company hasn't released an up-to-date version of the driver yet, or why Ubuntu hasn't been able to package your driver for your new kernel yet.

5. Your post was fine until the last paragraph where you started bad mouthing Ubuntu and the people who use it.  Don't do that.  But hey, I won't have to listen to you do it anymore, because you're going on my ignore list.  

Hope you get everything straightened out, or else go back to windows where you get errors like that all the time, without the awesome support like you have here on Ubuntuforums.

---

### Post by dlandis on 2009-12-05
OK sorry for being angry, I was just trying to get some work done and my computer is completely useless now after running a simple update. 

I never bad mouthed people who use ubuntu though so I don't know where you got that from (since i'm obviously one of them that wouldn't make much sense). As for bad mouthing ubuntu itself, don't take it personally it is a piece of software! And it has problems, lots of them.

It never goes into low graphics mode either, so yes the message is useless. I'll try to use the old kernel I guess but I really don't have time to spend hours sifting through this crud. 

And you brought up windows and i have to say my windows NEVER bricked from running a simple update. Not even windows 95. Not ONCE.

---

### Post by michaelzap on 2009-12-05
fluffman gave you some very sound and specific advice. Trying his points number 2 and 3 will take you all of 60 seconds (tops), and one of those two options is very likely to fix your issue. Take a deep breath and try to be as constructive as he was in providing you with (free - as in beer and speech) support.

---

### Post by sgosnell on 2009-12-05
Running in low graphics mode is a long, long way from being a brick.  Just boot from the old kernel and see if that fixes the problem.  That doesn't take hours, just a minute or so to reboot.  If the old kernel doesn't fix it, come back and we'll try to help you, provided you play nicely.

---

### Post by dlandis on 2009-12-05
thanks i'm going to try again later after sleeping on it. i already spent a bunch of time trying to fix it. it is some nvidia problem so i guess it is their "fault" technically but i wish it would just work you know? free/not free is all secondary to me, firstly i just want to be able to get some work done. the computer is just a tool for me, not a hobby or something.

---

### Post by amturnip on 2009-12-05
> **dlandis said:**
> Oh my god this is so annoying. I didn't change a thing besides accepting the stupid updates. How do people even use ubuntu with all these meaningless garbage errors being thrown??? I mean "unknown error (null)"!!!!! Please, this is most unintelligible **** I have ever seen from an operating system.

Good observations, from start to finish.  

Why doesn't System Update say, "Attention - Updates are not available for the following kernel modules to match the kernel update, proceed anyway? y/n"

A good place to suggest enhancements to Ubuntu is [https://launchpad.net/](https://launchpad.net/)

---

### Post by dlandis on 2009-12-05
> **sgosnell said:**
> Running in low graphics mode is a long, long way from being a brick.  Just boot from the old kernel and see if that fixes the problem.  That doesn't take hours, just a minute or so to reboot.  If the old kernel doesn't fix it, come back and we'll try to help you, provided you play nicely.

i know, i know i apologize i'm going to try later.

---

