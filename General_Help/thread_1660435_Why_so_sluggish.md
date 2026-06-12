---
title: "Why so sluggish?"
date: 2011-01-05
forum: General Help
---

### Post by xtremesupremacy3 on 2011-01-05
Hello there,

I have a problem which bugs me to no end.
Basically i run Kubuntu 10.10 without much trouble but then after a bit it hangs, it goes slow, it just misbehaves...now i checked top in order to see if something was going wrong but nothing looks odd...it seems to happen mostly after i used Google Chrome (not chromium)...but even if thats killed, it still misbehaves...it also does this if i have just plugged in my headphones....its strange.

Now I am far from a new user, but I have no idea where to start looking, so I was wondering if someone could point me in the right direction.

Thanks
Arthur

---

### Post by xtremesupremacy3 on 2011-01-06
I also had installed Tork, but due to the fact that I hardly ever used it, I decided to uninstall it. Now the problem seems to have gone...I will monitor it for the next few days to see if this has indeed solved it. If so, I will report back on here and reproduce the problem and file a bug for Tork.

Arthur

---

### Post by Zorael on 2011-01-06
It may be that Chromium is using so much RAM that you run out and start to [swap](http://en.wikipedia.org/wiki/Swap_space). If you open up the System Monitor, there's a graph depicting memory use under the System Load tab. It should preferably not be using any swap at all, so the green line should be way down at the bottom.

You can also check this in a terminal with the **free** command.
```
$ free
             total       used       free     shared    buffers     cached
Mem:          2007       1974         33          0          9        164
-/+ buffers/cache:       **[COLOR="Red"]1800[/color]        [color="Green"]206[/COLOR]**
Swap:         2994          0       2994
```

There's a "swappiness" value you can change which dictates how eager the kernel should be to start swapping. By default it's set to 60, and it ranges from 0-100. I set mine to 0 which seems to make a difference. Google swappiness for explanations on what it actually does on a more technical level.

You can set it to 0 temporarily with the following command, though it will revert to 60 upon reboot.
```
$ echo 0 | sudo tee /proc/sys/vm/swappiness
```

You can set it to 0 permanently (although it requires a reboot to take effect) by creating a file such as **/etc/sysctl.d/99-swappiness.conf** with the following content;
```
# Decrease eagerness to hit disk and swap
vm.swappiness=0
```

Also you could hit shift-ESC while in Chromium to pop up its task manager. If you see a tab or an extension using ridiculous amounts of memory, you can hit End Process there and then reload it. Ad blockers can notoriously grow to allocate stupid amounts, as well as pages that update themselves, or tabs which have lots of pictures cached. For instance, Ad Blocker Plus (Beta) is currently using 154.66 Mb of memory (!!) on my machine, so it looks like it's time to kill it and restart the extension on the little bar that scrolls down.

---

### Post by xtremesupremacy3 on 2011-01-06
Thanks for the reply,

You know, I have added the conf file as specified and to be honest swap does sound like a very likely problem. I also noticed this afternoon, just before I seen your reply, that the same occurred when I opened openoffice.org...This time though it shot up in my RAM...I am going to keep this post open purely for those who have had similar problems until I have been able to conclude it fixed. Who knows, perhaps it's a RAM problem and not swap.

Either way, I want to thank you so much for giving me these ideas. It's people like yourself that make the ubuntu community great

+1

---

### Post by xtremesupremacy3 on 2011-01-09
Well I am confident that this was exactly what was needed. Thank you

Solved

---

