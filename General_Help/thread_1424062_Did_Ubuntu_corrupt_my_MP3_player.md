---
title: "Did Ubuntu corrupt my MP3 player?"
date: 2010-03-07
forum: General Help
---

### Post by Alex_GT on 2010-03-07
Ever since I connected my MP3 player to ubuntu the music I put on it doesn't show in the players interface. The actual storage device seems fine and if I delete music off it removes it fine also.

Basically, the problem is the MP3 player isn't now recognising new music being put onto it.

This is also happening on my XP computer, the player was working on Vista a few days previous.

Could it just be a coincidence my MP3 player breaks as soon as I start using Ubuntu or what do you think?

---

### Post by _khAttAm_ on 2010-03-07
What kind of media player do you own? 

You should probably check the drive with fsck.vfat from ubuntu or from windows.

---

### Post by Alex_GT on 2010-03-07
I own a creative zen v plus 4gb model.

I'm sure the drive integrity is still good, because I'm able to move files on and off the device, play them on other computers.

Also, about that command you gave me, I'm drawing blanks on how I use it.

I typed in terminal:

fsck -a vfat gphoto2://[usb:002,003]/

and it came up with instructions, can you help again?

---

### Post by wilee-nilee on 2010-03-07
I would check for firmware updates, this may take care of the problem you never know.

---

### Post by dnairb on 2010-03-07
The "gphoto2://[usb:002,003]/" is a giveaway: IIRC there is a bug in gvfs-gphoto2-volume-monitor which leads to problems with mp3 players (it happened to my Trekstor Vibez as well) [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/363101](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/363101) - relates to a Sansa e250 player, but there have been problems with others.

I think: for now, try "killall gvfs-gphoto2-volume-monitor" in terminal before plugging in your mp3 player. You may find that gphoto2 has already damaged the filesystem on the mp3 player, in which case a format or restore to factory settings may be necessary.

---

### Post by Alex_GT on 2010-03-07
Thanks for the help, it seems the problem is Ubuntu and not the device. 

Having said that, it wasn't a device that liked to simply "plug and play" anyhow, and I could see why Ubuntu didn't like it.

I guess I'll need to use windows to transfer files...the command you gave me just seems to make it so ubuntu doesn't recognise the device at all.

---

### Post by dnairb on 2010-03-08
> **Alex_GT said:**
> ...the command you gave me just seems to make it so ubuntu doesn't recognise the device at all.

Pants! Sorry about that - it's obviously not the bug I was thinking of.

It may be wise to check, if possible, the file transfer setting. Your player should have an option in settings for MTP or MSC. MSC *should* be "plug and play" in Ubuntu.

---

