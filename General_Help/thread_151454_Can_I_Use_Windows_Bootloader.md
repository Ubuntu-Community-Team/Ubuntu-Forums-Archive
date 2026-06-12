---
title: "Can I Use Windows Bootloader?"
date: 2006-03-27
forum: General Help
---

### Post by Minn3h on 2006-03-27
I'm multi-booting my machine, and have another OS that I only know how to boot with the windows bootloader, which means I'd rather not use GRUB.  I had Windows and Ubuntu dual-booted using grub before adding another OS, but now have reverted back to using the windows bootloader.  So, is there a way to take my already present Ubuntu install and boot it with the windows bootloader.  I have tried various methods like dd if=/dev/hdb1/ ... and bootpart but neither worked (then again, I might have done either one wrong).  Suggestions?

---

### Post by Sef on 2006-03-27
Here's how a someone got a windows 2000 boot loader to load Linux as well:

[http://pcquest.ciol.com/content/networking/100080119.asp]("http://pcquest.ciol.com/content/networking/100080119.asp")

What problems did you have with GRUB?

---

### Post by Minn3h on 2006-03-27
Ok, so what I gather from that article is by originally installing GRUB to the MBR there's nothing on my existing linux partition that will work to make ubuntu.bin for use in boot.ini.  So, the suggestions in that link would work, except that I don't have LILO installed and can't get to my Linux partition, though I do have a Knoppix live-cd if that is any help, and I suppose I could download and make an ubuntu live cd.

So I guess what I do is:
1. Install LILO on my linux partition (not the MBR)
2. Follow the directions in the link.

Ideas on how to do #1?

---

