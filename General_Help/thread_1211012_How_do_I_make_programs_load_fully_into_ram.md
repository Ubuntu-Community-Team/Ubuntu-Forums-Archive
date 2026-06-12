---
title: "How do I make programs load fully into ram?"
date: 2009-07-12
forum: General Help
---

### Post by s3a on 2009-07-12
I've read somewhere that people can tell their operating systems to load, let's say every single bit of Firefox into their RAM so that  it's fast. I have the package preload installed. Is this supposed to already achieve what I am talking about? To answer myself to the best of my abilities, I think it only affects the application launch speed however in the unusual event that my hard disk is under heavy load; downloading websites to the hard disk would be very slow so would there be a way to tell it to download websites temporarily directly into the RAM?

_Basically, I'd like to find out:_

1) Does preload preload every single bit of the most used programs' data into RAM?
2) How can I make sure that certain applications of my choice are only allowed to use RAM (or swap just in case RAM is overloaded)?

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by kerry_s on 2009-07-12
1. no
2. no, everything must use ram.

---

### Post by VCoolio on 2009-07-12
You can at least make your system to prefer RAM in general and postpone using Swap by decreasing swappiness as explained [here]("https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27"). Little tweak and easily undone. Don't know if there is anything to configure this for specific apps.

---

### Post by s3a on 2009-07-12
I have vm.swappiness=0 and vm.vfs_cache_pressure=1.

@kerry_s: For #2 I meant to prevent certain applications from using the hard drive in ways other than swap usage.

---

### Post by mano cazalet on 2009-07-12
maybe this thread might interest you

[Firefox profile in RAM for increased speed and stability ]("http://ubuntuforums.org/showthread.php?t=1120475")

---

### Post by kerry_s on 2009-07-12
> @kerry_s: For #2 I meant to prevent certain applications from using the hard drive in ways other than swap usage.

personally i don't even mess with the ram/swap stuff any more, no tweaks, most things are managed very well these days, a whole lot better than it was in the past.
if it needs it let it use it, otherwise your just wasting it, the purpose of it is for speed, swap is used for the old stuff that was in ram, but that might be used again so it's saved for faster access.
no newly started programs use swap, swap is only for stuff moved from ram.

i only have 256mb ram on this system & it hardly ever uses swap, i have to watch a lot of movies/vids in a row or open up huge doc files & even then it will only be less than 30 of swap use.

---

### Post by itsjareds on 2009-07-13
I'm in the same boat as Kerry. I have 1GB of RAM which is low for a desktop when there are laptops around that have 4GB. Even still, usage never gets to more than 60% tops (unless using a VM) and I never see the swap get used at all. The only time my swap is ever in use is when I'm running VirtualBox.

---

