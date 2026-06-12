---
title: "PC wont boot after disasterous event"
date: 2011-01-19
forum: General Help
---

### Post by theone964 on 2011-01-19
I was turning off my pc and my brother pulled out his sd card while the pc was shutting down. Now when I try to boot up I can't boot into my ubuntu partook it just hangs and then comes up with inittramfs. I can boot into my windows partition just fine. I also tried rebooting with the sd card in the slot but same thing.

I managed to load up a live disc but have no idea what to do next if I want to save my old partition (if it can be saved) otherwise as a last resort ill have to overwrite the partition.

Any help would be appreciated. And if there are sleeping errors be forgiving, im using my phone to post this

---

### Post by tk189 on 2011-01-19
I am by no means an expert but I have had a lot of experience with ubuntu not booting properly. The SD card may just have been a coincidence.

If you're getting the init and try passing bootarg error then it might be worth re-installing the grub bootloader.

This problem is cropping up all over this forum and there is a superb step by step walkthrough guide to [purge and reinstall grub from the live CD]("http://ubuntuforums.org/showthread.php?t=1581099") 

It will explain how to chroot from the cd session so you edit your hdd installation of grub as root. It gets rid of the corrupted grub and reinstall it afresh.

It's worked every time for me, it's tedious and the underlying problem that causes grub to mess up is not fixed either.

Good luck :D

---

### Post by theone964 on 2011-01-19
Thanks for the quick reply.
Do you think i should do what you said? the reason i ask is because my grub seems fine...i mean i can see it fine and it loads the windows partition from there just fine, it even loads the recovery modules but the recovery modules work for a while and then hangs randomly with no real error message

if you still think its the grub...i'll do it no probs :)

---

### Post by Rubi1200 on 2011-01-19
It could be a GRUB problem, but also possibly a file-system error because of what happened.

Reinstalling GRUB won't hurt but it might not fix the problem.

Here is what I suggest:

Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes" and when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

