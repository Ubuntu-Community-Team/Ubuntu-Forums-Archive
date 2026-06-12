---
title: "boot up error (busybox initramfs prompt)"
date: 2009-07-27
forum: General Help
---

### Post by eternal_sage on 2009-07-27
ok, i've been having this error for.... nearly a year now, i just keep forgetting to fix it because i reboot so rarely. i am dual booting Ubuntu and XP (pretty much just because LotRO doesn't play well with my sound card under Ubuntu). for the last year (approximately) i've been sporadically having the following problem: sometimes when i try to boot into Ubuntu from GRUB i drop to the initramfs terminal prompt (for lack of a better description).

i have not ever noticed this problem until i started messing with the Intrepid Alpha, but i doubt that has anything to do with the continuing issue... anyway i digress. when this would happen, the only way i could ever get Ubuntu to boot was to boot into Windows, reboot from there and then select Linux.

being a slight newb with hardware, i assumed this had something to do with a crappy HD not spinning up for Linux for some reason, thus needing to be still spinning from a reboot. i learned that that was not the case, but regardless i have no idea why this worked. it just did. anyway, two days ago my XP caught a cold and it would have been more trouble to fix than to just clean install and fix GRUB. however, i am stuck not being able to get into Ubuntu nor can i log into XP (XP hangs in an infinite log in - log out routine which is amusing if a bit annoying).

poking around on the net via the liveCD offers only one clue. someone somewhere mentioned an unclean shutdown could cause this problem. while i cannot verify this was the case everytime over the last 11 months or so, it would make some sense, because a power blip or XP freeze was about the only time my computer got to completely power down.

this got me thinking that a fsck on my Ubuntu partition would fix me. however, from the liveCD i cannot seem to load my harddrives. they are not even showing up for me to mount via terminal. all i really need to do is save a very small handful of files from XP, but i can't even do that from this vantage point. does anyone know what to do here?

p.s. if its relevant, XP is on hd0,0, linux swap is hd0,1 and ubuntu is on hd0,2. thanks!

---

### Post by t4thfavor on 2009-07-27
It probably has something to do with the order in which you HDD's aredetected. If you have a USB disk of any type remove it, and try booting again. 

My menu.lst for grup looks like this

```

title           Ubuntu 9.04, kernel 2.6.28-13-generic
uuid            adf3927b-aa18-4cb8-ac9b-8fae733d0746
kernel          /boot/vmlinuz-2.6.28-13-generic root=UUID=adf3927b-aa18-4cb8-ac9b-8fae733d0746 ro quiet splash
initrd          /boot/initrd.img-2.6.28-13-generic
quiet

```

I would bet yours probably says something like

```

title           Ubuntu 9.04, kernel 2.6.28-13-generic
uuid            adf3927b-aa18-4cb8-ac9b-8fae733d0746
kernel          /boot/vmlinuz-2.6.28-13-generic root=hd0,2 ro quiet splash
initrd          /boot/initrd.img-2.6.28-13-generic
quiet

```

So if you boot, it will look  at hd0,2 even if that disk has changed since Grub was installed.

---

### Post by eternal_sage on 2009-07-27
tried this (and thanks for the reply, btw) but it sent me into kernel panic (and strangely also knocked out my usb support... had to unplug and replug my keyboard to get back here :D).

the exact statement was this: kernel panic - not syncing: attempted to kill init

no clue what that meant, but it just froze after that statement requiring a hard restart (and the aforementioned keyboard fix). however, i am now able to access my hard drives from the liveCD (couldn't earlier as i said). i am going to try a fsck on them and see if i can fix from here. if anyone else has any suggestions, i'd appreciate it. talk to you all soon. thanks again!

---

### Post by eternal_sage on 2009-07-27
strange update... after the kernel panic i was able to see the HD from the liveCD. a strange thought hit me, which was to try to boot again. it fixed it. i am posting this from my actual Ubuntu installation. why this worked i do not know.

to reiterate, i have not changed anything since i got the kernel panic. it just worked the next time i tried it. while this is all well and good, i really want to understand what is happening here. if anyone has any clues, please let me know.

---

