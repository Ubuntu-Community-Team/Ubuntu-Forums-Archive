---
title: "Help! Display is suddenly slow and choppy."
date: 2012-04-08
forum: General Help
---

### Post by mtdewd on 2012-04-08
I can't quite figure out how to describe this problem, so bear with me. Running 11.10, and up until yesterday, everything was fine. Yesterday, someone messing with the house breaker box flipped the switch and shut off power to my computer room! 

After I rebooted, my computer display keeps freezing? Any time I access a menu or try to scroll in a window, the video display sort of goes "grainy" and locks up for a second or two... if that makes any sense. It's acting like the CPU is buried with some huge load. It's an Intel Core 2 quad cpu with 2GB Ram. CPU is at 8%, memory at 30%, Swap space usage is at 0%, hard drive is only 30% full, system monitor shows every process is sleeping (except system monitor, and one or two others jump to "running" and then back to sleep.) In other words, there is no load on the CPU or memory, but it keeps hanging like its over loaded. The graphs in system monitor show no spikes in usage or memory. Nothing seems to be going on, but the display just freezes for a second or two every time I scroll or move a window. 

Video card is Nvidia GeForce 9500 GT

I have rebooted a dozen times.
I have installed gnome shell and switched to all the different shells available (gnome, gnome classic, ubuntu 2D, etc). 
I have switched nvidia drivers.
I was running dual monitors, so I unplugged one and configured for single monitor.
I tried different display resolutions.

This problem shows up in the login screen too, before I can select which shell/desktop to run. 

Nothing I have tried seems to make any difference.

On the System Monitor Processes tab, nearly all of the processes say "poll_schedule_timeout" in the "Waiting Chanel" column, if that means anything. 

What can I do? It seems to be a video display problem, because it only does this when something affects the desktop display - i.e. scrolling a window, moving a window, opening a menu. And watching a video (youtube or local video in VLC) is impossible. 

Any suggestions??

---

### Post by TeoBigusGeekus on 2012-04-08
Your video card might be ready to kick the bucket.
If it'a desktop pc, try opening the case, unplugging everything and the replugging it again.

---

### Post by mtdewd on 2012-04-08
Turns out the fan on the video card is no longer spinning... don't know if I caused that when I took it out or not, but it's broke now. So I swapped in a different computer. Turns out the real problem is actually the monitor going bad. I haven't had a hardware failure in so long, it never occurred to me to think hardware.

---

