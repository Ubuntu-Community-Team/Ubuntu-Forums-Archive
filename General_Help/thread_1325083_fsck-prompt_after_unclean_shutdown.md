---
title: "fsck-prompt after unclean shutdown"
date: 2009-11-13
forum: General Help
---

### Post by asdir on 2009-11-13
**The Problem:**

I often have an unclean shutdown, which I guess is related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/367059").

After those unclean shutdowns, since I upgraded to Karmic, the system checks the harddrive after every unclean shutdown in a different way than before, which in itself is not a bad thing, of course.

However, today the the checking program stopped at 70% (a random number, I guess), or rather continued checking but did not progress.


**The Odyssey:**

So I made a hard reboot a couple of times with the same result. If I tried to skip, I was simply presented with a prompt that only told me how to restart. After some tries I booted into the recovery mode. Suddenly all the nice graphics were gone and I was presented with technical gibberish and, after a while, the same harddrive check in another look. Again, it stopped, too.

However, this time it asked me to run fsck manually. So I did. Although it must have been basically the same program that checked my harddisk, this time it complained to me in a way that made more sense: It actually reported to me what was wrong and asked me if it should fix that (some nodes being a duplicate of something). I let it do that, which meant I had to press "y" for about a 100 times.

After that, everything worked fine again.

**The Aftermath:**

I have a couple of questions for the development team (who do fine work, generally, in my opinion):

 - Why is my whole system setup in my local language, but the important warning and system messages are in English? I guess there is some way to change those, too (at least apt-get prompts are in my language as well), but can't remember being asked about that. How should users like my parents, who neither understand english nor tech-gibberish, cope with this?

 - Why do I have to boot into recovery mode to let fsck do the same work again?

 - Why did fsck not ask if it should fix the problem in the normal mode already? For that matter, why didn't it give me any hint what was going on instead of being stuck at 70% for half an hour?

 - Why, even in recovery mode, do I have to start fsck manually although it started automatically? I assume there is a very good reason, but knowing about it (and thereby letting me know, that I don't run a risk by letting it run "manually") would be very reassuring. And reassuring is what is needed when you try to fix the harddrive with your thesis on it, believe me. :S

Sorry, for the rant, but I just had to let off steam. I hope my critique is at least a bit constructive.

---

### Post by Giblet5 on 2009-11-13
The 'dev team' doesn't read this forum.

Other users like you read this forum and answer questions.

It sounds to me like your system is extremely unstable.

I would begin by rebooting to the grub menu, selecting "memtest86" and letting it run for four hours. If you get even one error, you will have to fix your hardware before attempting to boot anything. Otherwise you will lose (more) data.


Once that's out of the way, you should boot from a Live CD image and run fsck against your / filesystem drive. I would no longer trust the fsck program on the installed disk.

No operating system will tolerate cold booting while it's trying to repair its own filesystem. If the drive light is on/blinking and you think the system is hung, just walk away for an hour or three. If you reset or poweroff while a disk is writing, you **will** lose data. Not maybe lose data: *will* lose data. That's just normal writing... Poweroff or reset during fsck and you can remove everything on the disk in about 6 milliseconds.

Once you have repaired the filesystem (assuming that is even possible now, and working from a Live CD image still) you should attempt to mount the drive and backup your home directory (I would use a USB stick and the 'tar' command). Then I would double-click the "Install Ubuntu" icon and perform a clean install. Test everything. Then, restore the backup and test again.

---

### Post by asdir on 2009-11-13
First off: Thanks for caring.

As for addressing the devs: I just did not know where else to post this. Most of my questions don't relate to something that looks like a bug. So I did not try launchpad. But I still thought (and think) my critique is valid, hence my post here.

As for the problem: I will certainly heed your advice. I wasn't aware that the consequences could be so grave. I have killed the system via power button every day for a year now. It did not seem to have any consequences so far. I hope the problem here originated in terminating fsck in the first place, so I would not have to worry as long as I don't hard-restart it again.

Will report on memtest86, as soon as I can spare the laptop for 4 hours.

---

### Post by asdir on 2009-11-14
I did the memtest86 and results were negative. I seem to have no errors on my harddrive anymore. I conclude from that, that powering down manually after the monitor turns blank does not cause errors on my harddrive, but the hard-reboot during fsck did.

Still, the original bug as well as the way fsck works are a riddle to me.

Thanks for all the info, though.

---

