---
title: "VGA card has stopped start-up?"
date: 2011-02-24
forum: General Help
---

### Post by etsah57 on 2011-02-24
My vga card died, so I replaced it with an ASUS EAH5670 1GB card.
The computer starts up normally in Windows xp, but when I want to boot up in ubuntu, I choose ubuntu, then I get a series of upgrades or recovery modes, I always just choose the top one, then the ubuntu screen flashes up for about 1 second, then I get a black screen for a few seconds, then a message telling me the monitor is going to sleep!

What do I do to get back into ubuntu?

---

### Post by An Sanct on 2011-02-24
My first guess would be for you to do this:

Boot, select the "recovery mode", you will be brought to a ascii menu, from there, go to shell with networking (or without, doesn't matter).

Then run this command

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.new_GPU
```

This will rename you X screen configuration to ...+".new_GPU".

after that, enter

```
sudo reboot
```

This will reboot the computer.

If this doesn't help, you can restore the backup file with

```
sudo mv /etc/X11/xorg.conf.new_GPU /etc/X11/xorg.conf
```

PS. Have you used proprietary drivers?

---

### Post by etsah57 on 2011-02-24
PS. Have you used proprietary drivers?

PC wouldn't boot up in ubuntu, so I started it in windows, ran the install disc that came with the card. Everything is fine in windows, just can't seem to start in ubuntu.
Will try your suggestions after dinner, thanks

---

### Post by An Sanct on 2011-02-24
Well, if you can get into XP, then its fairly simple to prepare a live USB/CD (IMHO preferably USB) and run into Linux from there, fix the problem and be back to your good old Ubuntu :)

---

