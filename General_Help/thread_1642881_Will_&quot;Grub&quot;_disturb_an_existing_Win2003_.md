---
title: "Will &quot;Grub&quot; disturb an existing Win2003 Install?"
date: 2010-12-11
forum: General Help
---

### Post by xiotech on 2010-12-11
When I installed Ubuntu Desktop 10.10... I ran updates and was asked if I wanted to install or skip updating "Grub". I chose to skip this.

Is there any danger of losing an existing Win2003 install if I go back and install "Grub"?

Thanks
Tim

---

### Post by Quackers on 2010-12-11
If you install grub or grub2 it will over-write Windows bootloader. This can later be returned to a Windows bootloader with the Windows repair disc.
If you don't install grub or grub2 Ubuntu won't boot.

---

### Post by bodhi.zazen on 2010-12-11
When installing an OS, there is always a small risk of data loss, you should back up any data you do not wish to loose first.

I would not expect installing Ubuntu / Grub to disturb your windows installation.

---

