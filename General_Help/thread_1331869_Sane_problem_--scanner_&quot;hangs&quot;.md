---
title: "Sane problem --scanner &quot;hangs&quot;"
date: 2009-11-19
forum: General Help
---

### Post by ks78 on 2009-11-19
I have an Epson Perfection 4490 scanner, which I want the users in my network to be able to connect to remotely.  Its currently connected to a machine running Ubuntu 8.04 (64bit).  

Thanks to Ubuntu forums and various other sites, I've got Sane installed and its working with my scanner --at least locally.  I have phpSANE installed and its working, too.

My problem is, I'd like to use a Sane frontend such as SaneTwain so my Windows users can also access the scanner.

I've got SaneTwain installed on a WinXP machine and it does "see" the server.  When SaneTwain starts, it displays a mysterious **"Device busy"** message, but the device dropdown populates with **"epkowa:interpreter:005:006"**. --That matches what scanimage -L returns on the server.  So, I know client and server can see each other.

However, when I click the Scan or Preview buttons, the scanner seems to start to scan, but then stops.  I can see the lightbar stuck a couple inches down the page from its starting point.  When I run scanimage -L at that point, **"Perfection 4490"** is replaced with **"unknown model"**.  From there, all I can do is power cycle the scanner.  Does anyone have any ideas on how to fix this?

I know its not a problem with the scanner, because it works when connected to a Windows machine.  Also, Sane is working with phpSANE.  --I know I must be missing something, but hopefully someone out there knows what it is.

---

### Post by ks78 on 2009-11-21
If there's any further info you need, let me know.  I'd really like to get this working.

---

