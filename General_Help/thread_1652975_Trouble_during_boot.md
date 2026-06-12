---
title: "Trouble during boot"
date: 2010-12-26
forum: General Help
---

### Post by kungfuzed on 2010-12-26
I installed Ubuntu Netbook Remix on a Toshiba nb205 netbook. During boot I have to hold down a key on the keyboard for it to keep booting, otherwise it just doesn't do anything. I have to keep holding down a key until it gets to the login screen. I can tell it is working because the hard drive light only flashes when I'm holding down a key. It doesn't seem to matter which key it is, but I've been using Ctrl. Once I log in I have to wiggle the mouse to get to the desktop, or it doesn't do anything. Then when the desktop comes up it works fine. Any idea what's causing it? Is there an easy fix or will I have to reinstall? Thanks.

---

### Post by kungfuzed on 2010-12-26
Ok, so I formatted and reinstalled and ran the update manager and it is still doing the same thing. If I don't hold down a key it doesn't boot.

---

### Post by Habeouscorpus on 2010-12-26
You might want to check your BIOS settings, since those are the ones that control the boot process. Are you completely sure that it does nothing? It may just be taking a very, very long time to do its thing. And how long do you have to hold down the key?

---

### Post by kungfuzed on 2010-12-26
I didn't find anything in the BIOS that would slow it down, though I'm not sure what would do that. All I did was change the boot order so that it would boot from the SD card so I could install Ubuntu. Now the boot order is set to the hard drive. After reinstalling Linux again it does eventually boot without my intervention but it takes a very long time, and only takes a fraction of the time when I hold down a key. After selecting the linux kernel in the boot menu it goes to a black screen. If I do nothing it just stays dark for a couple of minutes with no hard drive light flashing. Eventually the Ubuntu screen comes up with the dots underneath. It stays that way for a few minutes and I want to find out what's going on so I hit Esc. It seems to get stuck at random points depending on how long I hold down a key. If I press a key it continues the boot with a flash of the hard drive light and more stuff shows up on the screen. If I don't press anything I have to wait. If I hold down the key the entire time the whole boot takes under a minute. Once at the desktop, the computer works perfectly. I also failed to mention that it does the same thing during shutdown, I have to hold down the key until I see the word halt and then the power goes out. If I just close the netbook it does go into standby without any trouble. Maybe it's just something particular to this model of netbook and not Ubuntu, but it didn't do this in XP.

---

### Post by kungfuzed on 2010-12-27
Found the answer in another thread ["Gave up waiting for root device"]("http://ubuntuforums.org/showthread.php?t=1611213&highlight=nb205&page=4") post 33. I went into etc/default/grub and made the change GRUB_CMDLINE_LINUX_DEFAULT="nohz=off rootdelay=90". I have no idea what it means or how it worked, but the guy had the same problem as me and fixed it. Thanks for your help. :D[]("http://ubuntuforums.org/showthread.php?t=1611213&highlight=nb205&page=4")

---

