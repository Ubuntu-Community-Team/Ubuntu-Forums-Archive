---
title: "Update-grub updated, but no new entries?"
date: 2011-05-31
forum: General Help
---

### Post by MrRichard on 2011-05-31
I Googled around to find an answer to this with no luck. This was a tutorial on how to manually add an entry to Fedora: [http://forums.fedoraforum.org/showthread.php?t=263739](http://forums.fedoraforum.org/showthread.php?t=263739) However, this won't work for me because I can't boot into Fedora.

Before trying to dual boot Ubuntu, there was Fedora on my machine. Ubuntu installed fine, however, I noticed GRUB didn't find Fedora 15. After a boot into Ubuntu, I ran:
```
sudo update-grub
```It spat out:
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Ubuntu 11.04 (11.04) on /dev/sda7
Found Fedora release 15 (Lovelock) on /dev/sda8
done
```I rebooted the machine to find Fedora nowhere to be found. I found it a bit odd because this worked for me before.
So, is there any way to manually add an entry into GRUB so Fedora can be booted up?

I'd really appreciate any suggestions :)

---

### Post by oldfred on 2011-05-31
It says it found it. Does that entry not appear on the menu when you reboot?

Post this to see where everything is at:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by MrRichard on 2011-06-01
> **oldfred said:**
> It says it found it. Does that entry not appear on the menu when you reboot?

Post this to see where everything is at:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Thank's for the reply! I'll look into Bootinfoscript :)

---

