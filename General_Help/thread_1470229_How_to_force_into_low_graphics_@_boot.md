---
title: "How to force into low graphics @ boot?"
date: 2010-05-02
forum: General Help
---

### Post by rflook on 2010-05-02
Hi, hoping someone can help me with this as it's bugging me like crazy. Have just moved into my gf's place from a shared accomodation and have taken my mythbuntu (8.04) box with me. Have plugged it into her Sony tv and initially it looks promising, bios screen shows and so does the mythbuntu splash. But after that the tv just sits there with a message saying "out of range". Anyone got any ideas how I can force it into a low graphics mode or similar so at the very least I can access the desktop. 

Oh and to make things worse my gf has no Internet access (writing this on my phone) and I don't have a livecd to hand :-(

---

### Post by WorMzy on 2010-05-02
When grub is booting, can you press Esc to show the boot menu? If so, press 'e' to edit the first entry, then scroll down to the line beginning with "kernel" and press 'e' again, then add 'vga=ask' to the end, press Enter, then press 'b' to boot. You should be presented with a list of VGA modes that your system is compatible with, choose the one that looks the most appropriate for your resolution.

---

### Post by rflook on 2010-05-02
The grub thing would be a good idea if I could tell when grub was loading, as I have just realized that whereas on my old tv I would see boot/shutdown messages either side of the splash, this time I just get the "out of range" message on my tv when I would usually expect to see bootup messages :-/

---

### Post by WorMzy on 2010-05-02
Grub does it's thing after bios, but before the mythbuntu boot splash, so try pressing escape between those two events.

---

### Post by rflook on 2010-05-03
Hmm, there has got to be a slightly better way of doing this, I think I can get into the grub menu by hitting esc at right time as I don't get the splash screen but still only get the put of range message so I can't see any grub options :-/

---

### Post by WorMzy on 2010-05-03
If you can't get into the grub menu, then the only other solutions I can think of would include the use of a Live CD. I know you said you don't have one, but just in case:

It doesn't have to be a Ubuntu Live CD, it can be any. You just need to mount the partition with your /boot folder and manually edit /boot/grub/menu.lst (or grub.cfg if you're using grub2). Add 'vga=ask' to the end of the kernel line if you're using grub legacy. You'll probably need something different for grub2's config file, but I'm afraid that I can't help with that as I don't know anything about grub2.

---

### Post by rflook on 2010-05-03
Found a backtrack livecd kicking about thankfully, so managed to find my menu.lst file, added the VGA=ask option and commented out hidden menu. When I booted up my machine it still doesn't show the grub menu, I'm pretty sure the computer is outputting it but it just won't show on the tv. It's weird but anything other than the splash and bios screens just result in a 'out of range' error :-/

---

### Post by WorMzy on 2010-05-03
That is weird. Are you sure that the changes to the file were written to the disk? I've had a couple of occasions where I've edited menu.lst only to have the file revert to it's pre-changed state when I rebooted.

Might be worth rechecking. Also, check the timeout isn't a really low number of seconds.

---

