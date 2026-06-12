---
title: "Screen goes black when I enable network connections"
date: 2012-06-13
forum: General Help
---

### Post by Black Orpheus on 2012-06-13
I've probably done a lot wrong already, so I should stop and ask a question before I make things any worse.

This afternoon, I was connected wirelessly to the library's internet connection. I run (ran?) I think Ubuntu 11.10, but now when I check it tells me that I'm running 11.04. More on that in a minute. Anyway, the computer told me that I should install some updates, and I stupidly agreed. Then I closed my computer (a hp G42) and checked out some books, and when I opened it a minute later, I was having some problems. The wireless picture of hashes at the screen's top right looked like it was fluttering toward connected, but then it wouldn't connect. I didn't know quite what was the problem; I had been having a weird thing with UbuntuOne in that it kept telling me that it was uploading a small OpenOffice file that shouldn't have taken very long to load, but I didn't know if that was the same problem or not. (Every time I shut down now, the computer tells me that UbuntuOne's still running, but I still don't know it that's a related problem.)

I went home and tried to get things working there. What I did next was probably very stupid: I used System Janitor to clean up the system. I don't know what programs I junked doing this. Anyway, I tried to start up again, and still nothing. I may have my chronology slightly off on this, because I know that at some point I used grub to start things up, and was trying to get back to a form that would let me connect to the Internet again...only now, I'm stuck in 11.04 and I can't access grub by pressing esc at startup like I used to. So I don't know what's going on with that, either.

What's the weirdest thing, right now, is that when I go to the upper right of the screen and click on the pie-shaped divot that tells me about network connections, I can click and go down to the place where it says "Enable Networking"...only when I do that, everything shudders a bit and the screen goes black! Aargh! :confused:

If anyone has any ideas where to start on fixing this, I would really appreciate it. I'm not sure what to do... Thanks.

---

### Post by fuzzyworbles on 2012-06-13
you have a few unrelated problems that would have better been understandable if enumerated.

1. for grub, hold down shift right after post and before grub. it sounds like grub has a hidden timeout enabled. 

2. bleeding edge PPAs notwithstanding, it's never stupid to perform updates. i doubt updating caused any of this.

3. i've had broadcom wireless cards that would flake out from time to time on me when waking a sleeping computer. it wouldn't happen every time, but only some of the time. it would exhibit the same symptoms you describe: inform me of available wireless networks, but fail to connect to them. removing and re-inserting the module would cure the problem. HOWEVER, ever since 12.04, i have not once had this problem. 

4. the only relationship between your video and wireless cards is maybe a shared irq, however i seriously doubt that your bios or the kernel mapped them to the same irq. 

my suggestion: install a fresh copy of 12.04.

---

### Post by Black Orpheus on 2012-06-14
Thanks for your comments, fuzzyworbles. You were exactly correct about GRUB--nothing was wrong there. So far as I can tell, the only thing is that I can't get on the Internet to update anything right now. Even when I go to old versions on GRUB, I still get a black screen when I go up to the pulldown Enable Networking.

Is there any other workaround so that I can get my computer hooked up to the Internet? Or would you suggest I burn a new copy of Ubuntu onto a disk and try to reinstall from scratch, not off the Internet?

---

