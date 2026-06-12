---
title: "No init found"
date: 2011-04-25
forum: General Help
---

### Post by J4x0 on 2011-04-25
Hey.
Yesterday my programs started to behave strange and I got stuck. So I rebooted my pc and I got an error:
No init found try passing init bootarg and something about a 'BusyBox'.
I searched a bit and saw that you could fix that with booting with your LiveUSB and typ something in terminal.
I can't boot from my USB it keeps loading. I've deleted my files on USB and made another LiveUSB but again it didn't boot.
Can someone help me out please?

Thanks, Jaco

---

### Post by J4x0 on 2011-04-25
bump!
Can someone help me pl0x:confused:

---

### Post by Rubi1200 on 2011-04-25
Do you also have a CD drive or only USB?

We need to somehow get you booted into a live environment to find out what is wrong and then try and fix it.

If you can, download and burn to CD (I don't know if it will work with a USB stick but you can try), a distro called Slax:
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

If you can boot the computer (make sure BIOS is set correctly), then please do the following:

Boot the computer with the LiveCD/USB. Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

