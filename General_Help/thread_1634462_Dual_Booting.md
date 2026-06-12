---
title: "Dual Booting"
date: 2010-11-30
forum: General Help
---

### Post by ZJE123 on 2010-11-30
I have installed both Windows 7(64bit) in a 150gb partitian and Ubuntu 10.10(64bit) to the other 150gb partitian. I am using a dell xps M1530(2.0ghz dual core, 3gb Ram,upgrading to 8gb ram soon, 320gb hard drive, ect.). I seem to have trouble dual booting. When I load form the Hard Drive, it automatically goes to Windows. I have fully upgraded the BIOS to A12. How do set it up so it lets me select the Operating System I want to boot into?

---

### Post by oldfred on 2010-11-30
Did you install windows last so its boot loader is in the MBR? Otherwise grub2 should be in the MBR and boot to a menu letting you choose Ubuntu or windows.

To see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

---

