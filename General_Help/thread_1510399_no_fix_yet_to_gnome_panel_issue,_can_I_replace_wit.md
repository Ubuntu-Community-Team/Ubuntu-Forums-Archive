---
title: "no fix yet to gnome panel issue, can I replace with kde"
date: 2010-06-15
forum: General Help
---

### Post by rajn on 2010-06-15
Hi,
I have problems (very often) with Lucid 10.4 . 

First I get a blank purple screen which occasionally responds to right click of the mouse to show me a small menu where I am allowed to open new files etc but nothing else. 
I have to do a "killall gnome-panel" to revert back to a screen with gnome panels. However, on some menus such as system->preferences I do not see thumbnail view of the applications i.e., panel is broken.

Also very often while shutting down, the computer freezes with Caps and Scroll lock indicators flashing.

I have tried everything possible solution suggested, with modeset =1 or 0, no acpi, blah blah blah. I have turned KMS on and then off, used different older kernels, hacked grub files, xorg files and really every thing I tried has been of no avail. I have reinstalled Lucid umpteen times.

Ubuntu 9.10 worked fine except it hogged the CPU which always showed running at 100%. 

So to summarize "UBUNTU IS NOT AN OPTION FOR OLD INTEL CHIP COMPUTERS" or at least my Vaio Sony.

So here is what I would like to find out

1. Mandriva runs without any flaws on my computer (hurray!!). I have partitioned with Grub2 as a boot loader and Mandriva is chain loaded. How can I remove Ubuntu and say goodbye to it without affecting Mandriva?

2. If Mandriva works - is there any way by file comparisons find what is wrong with Lucid? This is my question to the developers. Shouldn't it be relatively easy to see what is wrong with Ubuntu Lucid by looking and comparing with working systems?

3. As a last ditch effort not to give up Ubuntu (which looks unlikely day by day), can I replace gnome with kde? Hopefully, the gnome panel problem of a blank screen will be solved?
 
4. In the eventuality that I just cannot give up Ubuntu, can I write a shell script which just says "killall gnome-panel" on start up. This will prevent me from typing this every time I boot into Lucid?

Appreciate any help.
Thanks,

---

### Post by NoBugs! on 2010-06-15
Sometimes you need to reset the panel, you can do this by moving or deleting your /home/username/.gconf/apps/panel folder.

---

### Post by rajn on 2010-06-16
> **NoBugs! said:**
> Sometimes you need to reset the panel, you can do this by moving or deleting your /home/username/.gconf/apps/panel folder.

Tried it. Removed and made a backup of the panel. But still getting blank purple Lucid wall paper without panels. pkill works only for that session..

Instead tried the following: In system->preferences->startup->options, selected an option which reads something like "auto remember the current configuration during every log out". 
Sorry for not remembering the exact words....I am not on the Linux computer currently.

Anyway, so far I have booted thrice and now the panel shows right away and no blank Lucid wall paper staring at me. Keeping my fingers crossed. Maybe after ten boots if the problem does not reappear, I will notify in this post that part of the problem is solved.

However, one problem which still worries me is that **computer does not shut down most of the time.** During log out either using command - 'shutdown' or graphical log out, the screen hangs **with caps and scroll lock blinking**. The only way is by powering off the computer. I do not see it affecting anything - but - but, I had to do something to make my life easy.

Earlier, I had no partitions on Lucid. It was one big block of memory. As a result after every shutdown problem described above, on rebooting the computer would check the memory and it would take half hour or more for each reboot and every time it would show that /tmp file loading slowly.
So I thought the problem during shutdown maybe affecting only the programs which reside in /tmp directory. Therefore, I partitioned every file/directory. Now I have 9 partitions for Lucid and now for every occurrence of improper shutdown, when I reboot I do notice memory check being done but it happens very fast and is not annoying. No more half an hour of agony.
It helps but looks like is a very temporary solution and perhaps an unsafe issue.

Therefore anyone who can point out why shutdown does not occur, why does computer end into an endless loop with Caps and Scroll lock lights blinking....that would be a great help.
I did perform MEM8x check and it ran through 3 trials after which my patience ran out. But I did not see any problems in those three trials.
Thank you,

---

### Post by tendonstrength on 2010-06-16
This is all anecdotal, but I highly recommend against trying to put KDE on a system with Gnome already installed. I did this with Karmic once and it was a huge mistake. After I installed it, the fonts in both kde AND gnome were completely jacked, presumably because of some kind of conflict between the two. It took me hours to get it back to normal and it was just a huge waste of time. 

With that said, I have never tried a clean install of Kubuntu, which probably works much better. If anything, you might try that if you can't fix your original issue.

---

### Post by rajn on 2010-06-17
I have positive and interesting update on my 2 problems viz 
1.  blank splash screen and 2. Cap and Scroll blinks.

1. My blank splash screen problem on booting which I had to resolve with 'killall gnome-panel' is resolved after I did this
System->Startup Application Preferences->Options->Automatically remember running applications when logging out

It was that easy. And now on every reboot I get a gnome panel and no more blank purple screen. And my settings are 'quiet splash and modeset i915=1'  though I do not think that makes any difference. Just ' quiet splash' is good enough.

2. I have done several trials and have come to the conclusion that the "Cap and Scroll lock lights blink" during shutdown due to heating of the computer.

a. When I run the computer for time when fan does not run and shutdown - I get a normal shutdown and no lights blink
b. When I run computer long enough that the computer fan kicks in and then shutdown - I get a screen hang during shutdown with caps and scroll lights blink.
c. To test this further, when the computer is sufficiently hot that the fan kicks in, I get an ice pack and place it on the bottom safely enough not to stress the heated parts and let it cool down. Then I logout and lo - proper shutdown.
d. I have Mandriva distro. It runs fine and shuts down fine. I noticed that with it the computer gets less heated than with Lucid. 

Therefore, all this tells me that there is something in Lucid -some commands - which do not get killed maybe during shutdown and has to do with CPU temperature and resulting in Kernel panic.
As I mentioned earlier mem test shows fine on 3 passes. Tried no acpi noapic etc but same problems.

I hope now someone can lead me on from here. 

Just some extra information: I had installed extra 256 Mb RAM on this computer. I do not think it has to do with the way the RAM cards are sitting in the slot because Mandriva and Ubuntu 9.10 had no issues.

And finally, you are correct tendonstrength. I remember having issues with both gnome and kde together on Lucid. For some reason I had forgotten all about it. So, I do not think I am going to mess with that.

---

