---
title: "Clonezilla to migrate to ssd?"
date: 2009-09-27
forum: General Help
---

### Post by josephellengar on 2009-09-27
Just wanted to make sure before I do something really stupid, but if I buy a ssd and want to migrate my Vista installation over to it, will Clonezilla be the way to go?  I was considering buying (or downloading :twisted: Acronis, but Clonezilla would probably work just as well, correct?  I've just never used the device to device functionality on it, only the back up and restore images.  I guess I'd probably just put the old hard drive in an enclosure and the ssd in the laptop and then do it via usb, and then install ubuntu after that was done.  What do you think?

---

### Post by josephellengar on 2009-09-27
Anybody?

---

### Post by solitaire on 2009-09-27
It should be fine since the machine will see the SSD as a normal drive. But I've never used clonezilla...

Also give it a good practice to leave a few hours or so between bumps. not everyone is on here 24/7 ^_^

---

### Post by josephellengar on 2009-09-27
> **solitaire said:**
> It should be fine since the machine will see the SSD as a normal drive. But I've never used clonezilla...

Also give it a good practice to leave a few hours or so between bumps. not everyone is on here 24/7 ^_^

Oh, okay.  Sorry.

---

### Post by noelvh on 2009-09-27
I would post this on the clonezilla forum. I have found CZ is the best clone tool out there. So far the hardest thing I cloned was an encrypted hard drive (the hole drive had been encryptd). I tryed this clone with Ghost, and acronis frist and a big no go from them.

CZ is the best.

Why would you go with a SSD drive? I have not been convinced they are ready yet. They have a limitted life, and that is short from all I have read.

Noel

---

### Post by josephellengar on 2009-09-27
> **noelvh said:**
> I would post this on the clonezilla forum. I have found CZ is the best clone tool out there. So far the hardest thing I cloned was an encrypted hard drive (the hole drive had been encryptd). I tryed this clone with Ghost, and acronis frist and a big no go from them.

CZ is the best.

Why would you go with a SSD drive? I have not been convinced they are ready yet. They have a limitted life, and that is short from all I have read.

Noel

There is a clonezilla forum on the Ubuntu forums?  Or just one on the official CZ website?  I want to go with a SSD because I purchased one in my old computer and the OS booted literally _instantly_.  And then I had to return that computer and get another one (for a variety of reasons) w/out a SSD, and it felt like a snail for everything.  They are so much faster.  Plus, the intel g2 drives last forever, as long as you don't write 20gb+ a day to them, which I would never do.  Plus, I have no library of video/music, so the size makes no difference to me.  So yeah, I know I'm an early adopter, but I think that any high quality drive (not samsung/OCZ/et. al) is incredibly fast, even when "used."  And it looks like they are adding trim() support to Koala, so that will be even better.  Thank you very much for your input though, now I won't have to spend money on Acronis.

---

### Post by StuartN on 2009-09-27
I used Clonezilla to replace my system drive. It was absolutely faultless and pain free - just plugged the new drive in as a primary slave, booted off the Clonezilla disk, duplicated the old drive (primary master) onto it and then plugged it the new drive in as primary master.

The computer booted up (multiple OS with GRUB) as if nothing had changed.

And my little old drive is in the drawer as a backup - nothing has changed on it, so I could have undone Clonezilla if anything went horribly wrong.

Great package.

---

### Post by apocalypse80 on 2009-09-27
Can anyone verify that clonezilla performs proper partition alignment on an ssd?

I did the migration a while ago and it was a royal pain because almost NOTHING respects alignment.

What I had to do:
1) Created a layout of aligned partitions
- Connected the SSD to a windows 7 machine to do initial partitioning and format the ntfs partitions.
- Formatted the ext4 partitions from an ubuntu live cd.
There are many ways to create aligned partitions, this is by miles the easiest one.
2) Created images of all original partitions using tools that respect alignment
- Drive snapshot for ntfs partitions (requires windows)
- fsarchiver (from system rescue cd) for ext4 partitions.
3) restored all images to the ssd.
4) re-installed grub from an ubuntu live cd

fsarchiver and drive snapshot are the only tools I've seen so far that clone a partition while preserving it's geometry.
Things like gparted and acronis TI fail in that regard.
But I haven't tried clonezilla.

---

