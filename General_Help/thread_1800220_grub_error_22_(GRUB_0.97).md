---
title: "grub error 22 (GRUB 0.97)"
date: 2011-07-08
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-07-08
i just copied my root partition to a different drive
went through the process to fix the mbr
```
sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0)
```
all the UUIDs are correct and their are not conflicting UUIDs
sda became sdb and the net drive is sda
i am getting frustrated now

---

### Post by oldfred on 2011-07-08
Post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Error 22 says some partition is not correct:
[http://members.iinet.net.au/~herman546/p15.html#22](http://members.iinet.net.au/~herman546/p15.html#22)

---

### Post by pqwoerituytrueiwoq on 2011-07-08
i was in the boot menu and tried to boot the ssd manually and it booted
here i was thinking sata slot the drived was pluged into determined the boot order
seems the wrong drive was set to boot in the bios i just fixed it

---

