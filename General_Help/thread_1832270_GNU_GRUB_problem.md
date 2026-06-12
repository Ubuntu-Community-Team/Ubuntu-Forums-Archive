---
title: "GNU GRUB problem"
date: 2011-08-24
forum: General Help
---

### Post by Charobnjak on 2011-08-24
I have a problem with gnu grub. It all started when one day instead of showing a nice ubuntu loading screen it showed busy box(I think that was the name of it) screen and neither recovery mode didn't help. Then I though maybe my filesystem has been corrupted(since it happened before once but I managed to fix it) and since I couldn't run the fsck command for repairing the filesystem in the busy box I wanted to run ubuntu from USB stick(as "try ubuntu without installing") and that worked for me before but now it just shows some stuff I don't understands and won't load(I think when I tried opening the console it showed "cannot open stdin and stdout" or something like that. Than after that I left it like that for a while since I was too lazy to fix it. And today I decided to fix it. I put my hard disk into my brothers' computer. Run ubuntu from USB and everything worked fine, I saved what files I could and continued to install ubuntu again but the mistake was that I did it on my brothers',computer(but on my hard disc). The result was that now when i remove my hard disc from his computer gnu grub shows a "grub rescue"screen and i can't fix it. Anyone has an idea how I can remove or change gnu grub so that it automaticly boots windows 7 that he had on his hard disc?

---

### Post by sanderd17 on 2011-08-24
you can repair it with easyBCD I guess: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

Or you can repair the bootloader with a windows repair disk.

---

