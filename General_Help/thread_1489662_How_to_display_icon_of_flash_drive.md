---
title: "How to display icon of flash drive?"
date: 2010-05-21
forum: General Help
---

### Post by oxf on 2010-05-21
Hi,

This is not a work stopping problem but I think there's probably  a fairly simple explanation so I'll ask...

I have this flash drive that I recently reformatted. Before when I mounted it a little icon of the flash drive would pop up. I saved the .ico file that contained the image before formatting and placed it back on the drive. Now all I get when mounting it is a generic sort of icon not the image of the particular drive. How do I get it to display?

Thanks

---

### Post by Chesamo on 2010-05-21
You need to save the autorun.inf as well. Here's a simple one that will display the icon named "icon.ico":
```
[autorun]
icon=icon.ico
```

---

### Post by oxf on 2010-05-21
> **Chesamo said:**
> You need to save the autorun.inf as well. Here's a simple one that will display the icon named "icon.ico":
```
[autorun]
icon=icon.ico
```

OK thanks.. I'll try that

---

### Post by oxf on 2010-05-21
OK that seems to do it!
I'm just wondering if there's a way of customising the label? Right now it just displays as 
"2 GB File System" Can I put my own label instead?

---

### Post by Chesamo on 2010-05-21
When you format the drive, you can set a volume label. You can do that using GParted. Also see this:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by oxf on 2010-05-21
> **Chesamo said:**
> When you format the drive, you can set a volume label. You can do that using GParted. Also see this:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)


OK thats useful. Thanks :)

---

