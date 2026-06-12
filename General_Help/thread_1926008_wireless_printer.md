---
title: "wireless printer"
date: 2012-02-15
forum: General Help
---

### Post by sn0m on 2012-02-15
Hi guys
I'm due to buy a new printer.
I would appreciate if any of you would provide some guidance.
The preferred features of the new printer shall be:
Laser
wireless
easy to set up with ubuntu
able to print form windows xp running in VM virtual box
many thanks for your help
Sokol

---

### Post by Ms. Daisy on 2012-02-16
Have a look here for compatible printers with linux:

[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

I don't know about "easy to set up." I suppose that depends on your perspective.  I'm pretty new myself and was able to network my all-in-one printer/scanner in Ubuntu & Windows.  Will this printer be networked or for one machine?  Is it going to be a printer/scanner/fax?  

When you find a few candidates, I recommend you research the software for that printer if you're planning to use the scan function.  For instance I've got an HP and I had to install HPLIP Toolbox to use the scanner.

In regards to virtualbox, I haven't tried that. However, I imagine that printing from virtualbox has more to do with configuring virtualbox than it does with the kind of printer you have.

---

### Post by forrestcupp on 2012-02-16
> **Ms. Daisy said:**
> 
In regards to virtualbox, I haven't tried that. However, I imagine that printing from virtualbox has more to do with configuring virtualbox than it does with the kind of printer you have.

Also, a VM will only be able to access a printer that will work with the host OS. So if Linux is your host, you can't use a printer that won't work with Linux even if you're running XP in the VM.

But my experience is that HP works well with Linux. I have an HP wireless printer that was extremely easy to set up in Ubuntu's printer preferences. The wireless worked perfectly without tweaking. The only negative thing is that I have to plug it in to scan, but in Windows, I can scan wirelessly. But I'm happy with that. I remember the days when I was trying to use a Lexmark in Linux, and even after days of headaches trying to get it to work, I never got the scanner to work at all.

But my HP printer isn't a laser printer, so it's not what you're looking for. But HP generally has some of the best Linux support for printers.

---

