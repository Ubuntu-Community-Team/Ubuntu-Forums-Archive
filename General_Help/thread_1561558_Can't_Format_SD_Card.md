---
title: "Can't Format SD Card"
date: 2010-08-26
forum: General Help
---

### Post by moore.bryan on 2010-08-26
I've tried everything--from the CLI to GParted and back--but I can't seem to format my SD card. I *know* it's not the card because it is recognized in three other devices, which offer to format it because they don't think it's formatted.

When in GParted, I can create a new partition table and create a new partition, but after that completes, the card remains grey and the GParted tells me the disk label is unrecognizable.

When I go at it with fdisk/mkfs.vfat, I'm told:
```


Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x24edb58b.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to switch off the mode (command 'c') and change display units to sectors (command 'u').

```

*Nothing* I do makes this card readable in Ubuntu. Help!

This is all on Ubuntu 10.04.1, kernel 2.6.34-24-generic, GNOME 2.30.2 running on my Asus EeePC 1005HA.

---

### Post by inameiname on 2010-08-26
Maybe if all else is failing, try to erase it first, and then try to format it. If you haven't already.


        sudo shred -v -z -n 0 /dev/sdX

...where /dev/sdX is wherever your drive is

Perhaps it's something on the card that just isn't getting formatted properly, so as a last resort, best to make it essentially like a new drive and see what happens.

Could also do the formatting from a Live CD instead of your current computer, as maybe it's something on your drive, idk.

---

### Post by moore.bryan on 2010-08-26
Good advice @inameiname, I hadn't thought about shredding it. I just did that, ran parted, made a partition, formatted it FAT32, and everything looked good. I ejected it, plugged it back in and only /dev/sdc showed up, not the partition. When I ran parted again and selected /dev/sdc, it told me ```
Error: /dev/sdc: unrecognised disk label
```

So, I "borrowed" my wife's computer running Windows XP, inserted the SD card and it complained about it not being formatted. No biggie. Formatted it on XP, wrote a test file to it, ejected it, plugged it back in and... WTF? XP complained about it not being formatted.

Downloaded the SD formatter program from [here]("http://www.sdcard.org/consumers/formatter/"), ran that, completely erasing everything, and formatting it anew. Saved a test file to it, ejected it, plugged it back in and **WTF?** *Apparently, it's **still** not formatted!* Now, this SD card saves raw pictures from a camera, files on an ancient Dell Axim, but can't seem to work with either XP or Ubuntu?

So I tried your LiveCD idea and got the same results as above. I even, for who knows why, restarted my Asus about ten times.

Argh!!!!

---

### Post by inameiname on 2010-08-26
I know you said it isn't the card, but if it simply cannot get formatted from both Ubuntu, Windows, and the Live CD, deductively it must be the card.

For the fun of it, try formatting in some other format, like Win16 or even Ext. Not sure why that would make a difference, but who knows.

---

### Post by moore.bryan on 2010-08-26
> **inameiname said:**
> I know you said it isn't the card, but if it simply cannot get formatted from both Ubuntu, Windows, and the Live CD, deductively it must be the card.
That's exactly what I thought until I could put it into other devices and it *worked*.

> For the fun of it, try formatting in some other format, like Win16 or even Ext. Not sure why that would make a difference, but who knows.
Tried this just before I checked back for your post... no dice.

Everything *seems* fine after using fdisk, or parted, or mkfs.vfat, but when I eject and plug back in all the fit hits the shan.

---

### Post by moore.bryan on 2010-08-26
I don't know if this is headway or not, but I'm now able to have Ubuntu at least *see* the SD card. I'm not entirely sure how I did that, but a new problem has surfaced: I can't put anything on it. 

For example, I insert the card, Ubuntu mounts it with a random name (this time was 25FB-0AE1) and lets me write something to it. I can unmount and remount it and my file is there; however, as soon as I pull the SD card out of the reader and put it back in, Ubuntu mounts it and there's nothing on it.

How does this make any sense?

---

### Post by inameiname on 2010-08-26
Yikes. No, that doesn't make any sense why it would show as empty upon unplugging and plugging back in. I'm afraid I'm not really sure what to tell you.

Oh one thing to ask is using the EXACT same methods, are you finding trouble with other flash drives / sd cards? Another sign that it's gotta be something up with the card.

---

### Post by moore.bryan on 2010-08-26
Does the same when I try and format any other SD cards... borked my wife's camera card earlier. She's none too happy, in-case you were wondering...

---

### Post by inameiname on 2010-08-27
Aw, man. Guess then, I have no clue what would be causing it. If it's not the card, not the computer, what in the world? Hehe. Sorry. Maybe somebody else will find a solution for ya.

---

### Post by TwoEars on 2010-08-27
It might be the reader, especially if you have a cheap one. Try using a different one.

---

### Post by moore.bryan on 2010-08-27
> **TwoEars said:**
> It might be the reader, especially if you have a cheap one. Try using a different one.
It's the one built-in to my Asus... besides, other cards work--sometimes.

---

