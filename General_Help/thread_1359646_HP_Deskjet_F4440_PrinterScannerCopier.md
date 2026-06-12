---
title: "HP Deskjet F4440 Printer/Scanner/Copier"
date: 2009-12-19
forum: General Help
---

### Post by justin.tami on 2009-12-19
Hello, I have been using Linux for about a year, I have been using ubuntu for the past 6 months or so.

My dad bought for me, as a Christmas gift, an HP Deskjet F4440 Printer/Scanner/Copier.
I had been told that I could not go wrong getting an HP, which was mostly true. It prints and copies. But when it comes to scanning, I was hoping for a little help from this forum.

It seems the 'scan' aspect of this system is not compatible with ubuntu, and under the FAQ it mentioned that I might be able to fix the problem. I was wondering if anyone could tell me what I need to do to get the scanner to work, if anything. :confused:

The printer unit does not have any SD card slots. I thought perhaps there would be something I could do in the terminal to make the scanner transmit the image to the CPU.

Thank you for any help that you can provide.

Justin.

---

### Post by sgosnell on 2009-12-19
You need xsane for scanning.  With luck, you can just open xsane (Applications/Graphics/XSane Image Scanning Program).  When it opens you should be able to select your printer and scan.  You can also install hplip, which gives you an icon in the panel, and which you can open and select Scan, which then opens xsane.  I have no experience with that particular model, but in general HP provides decent Linux drivers, better than their Windows drivers.

A check of the HP website shows that there are no Linux drivers for it, but you may be able to get it to work using the closest model.  I would expect Linux drivers to be released fairly soon.

---

### Post by hansdown on 2009-12-19
Hi justin.tami.

As sgosnell said, you should get a screen to "choose" your printer.

---

### Post by inhiway on 2009-12-21
The link in this reply helped me tremendously:

[http://ubuntuforums.org/showpost.php?p=8533943&postcount=3](http://ubuntuforums.org/showpost.php?p=8533943&postcount=3)

Just follow the instructions on the HP page from the forum link.

---

