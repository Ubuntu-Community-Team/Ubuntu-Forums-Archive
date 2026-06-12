---
title: "Grub Error - I messed up bad!"
date: 2010-01-08
forum: General Help
---

### Post by ided on 2010-01-08
So I needed to remove linux from a dual boot, single drive setup I had going.

Without thinking I was in Windows XP and formatted the linux partition I had created.  After trying to reboot the computer I receive a Grub 1.5 Error 17 rightfully so.

I am having a hard time finding a solution...  All I need to do is get the machine back to being able to boot into Windows without any prompts.  Thank you for advance for any help you can provide!  I will continue to google!

---

### Post by the.lazy.boi on 2010-01-08
You're going to need your windows xp CD. Boot from the CD and when you get into first menu choose the repair console option. When you get to the command shell run "fixmbr", that should overwrite grub.

---

### Post by Leppie on 2010-01-08
boot with the livecd, open a terminal and issue these commands:
```
sudo apt-get install ms-sys
sudo ms-sys -m /dev/sda  ##if it's an ide drive use /dev/hda
```

Note: you may need to enable the 'universe' repository (System->Administration->Software Sources)

---

### Post by ided on 2010-01-08
Thank you both for your replies.  Unfortunately my Windows XP cd was too scratched to be properly read so I had to go the Live CD route.

As a brief side note for anyone that may read this post in the future the ms-sys package is no longer available via apt-get due to licensing issues from what I gathered.  You may still download and install the package from [http://ms-sys.sourceforge.net/#Download]("http://ms-sys.sourceforge.net/#Download").

You will have to compile the package in order for it to work but it is straight forward.
```
sudo make
sudo make install

```

Please also note that in order to compile you may need the gettext package.

```
sudo apt-get install gettext
```

Thank you both very much for your assistance as I would have been hunting around for a while before I found an easy solution.

---

### Post by Leppie on 2010-01-08
sorry about that, i always forget that package has been deleted.
there's also the lilo way:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

