---
title: "Dual Booting Windows 7 and Karmic"
date: 2010-01-21
forum: General Help
---

### Post by james.exe on 2010-01-21
So I partitioned my hard drive about half and half a couple of hours ago. I went ahead and installed windows 7 on the available space and successfully did so. When I restarted my computer, it would load to windows 7 automatically without giving me the option to boot karmic. I did a little reading and stumbled upon what seemed like a fix. Pretty much, I booted ubuntu from a livecd and plugged in some terminal commands to get my grub working for me again. I was able to successfully boot karmic upon restarting, but now I can't boot windows 7. I'm guessing I transfered the boot priority over to my ubuntu partition. I've been reading and reading and can't seem to find anything of help. Most of the guides assume that you're doing clean installs of either OS but I already have both installed on separate partitions. How can I give boot priorities to both my Windows 7 and Karmic partitions?

---

### Post by ubunterooster on 2010-01-21
try: sudo update-grub

---

