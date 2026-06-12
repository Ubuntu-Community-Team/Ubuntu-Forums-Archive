---
title: "Ubuntu - Windows laptop"
date: 2009-10-11
forum: General Help
---

### Post by drwatts2 on 2009-10-11
Hey all,
  I'm looking at setting up a Dell Latitude D610 with Ubuntu and Windows XP home and would appreciate suggestions.  My goal is to primarily use the laptop with Ubuntu but want to be able to use some Windows programs like Quicken, Access, genealogy programs, no games.  
  Any help from initial configuration of the laptop with the 2 OSs, to how to access and run windows programs would be greatly appreciated. 

TIA

---

### Post by e24ohm on 2009-10-11
I would suggest a dual boot method, or run VBox on top of Ubuntu and run Windows in your Vbox.

---

### Post by antonkedrov on 2009-10-11
> **drwatts2 said:**
> Hey all,
  I'm looking at setting up a Dell Latitude D610 with Ubuntu and Windows XP home and would appreciate suggestions.  My goal is to primarily use the laptop with Ubuntu but want to be able to use some Windows programs like Quicken, Access, genealogy programs, no games.  
  Any help from initial configuration of the laptop with the 2 OSs, to how to access and run windows programs would be greatly appreciated. 

TIA

i suggest you to install Ubuntu as one OS at your laptop and use VirtualBox to run guest operating system (ex, Windows XP) for launch specific applications, which can not be executed by Wine from Ubuntu.

download VirtualBox proprietary version, which is free for non-commercial usage and has more abilities, from VritualBox site (my advice is don't use VirtualBox OSE - OpenSource Edition).

---

### Post by tpjk on 2009-10-11
there's also the option of setting up a dual boot. if you decide on that you'll want to make windows your boot partition, i.e. install it first (as windows is likely to cause problems with grub if you install it after ubuntu) and then use a live cd to partition your drive and install ubuntu.

---

### Post by ZacDavis on 2009-10-11
Personally, I would dual boot.  I have the same exact laptop, and am on it right now.  I am doing the same exact thing with no problems.  there are many tutorials out there for dual booting, so there is no need to reiterate them, but basically, you'll need to install WinXP first, and then Ubuntu.

---

### Post by drwatts2 on 2009-10-11
All,

 Great info! Thanks.  I'll read up on Vbox.  To use Vbox do I need to install XP like I would for a dual boot?  I get the impression from the comments that is not necessary.  My expectation was that I would set up a partition for XP and then install it, followed by installing Ubuntu.  I would then be able to use Vbox to access XP and apps like quicken through it.  

Thanks.

---

### Post by e24ohm on 2009-10-12
> **drwatts2 said:**
> All,

 Great info! Thanks.  I'll read up on Vbox.  To use Vbox do I need to install XP like I would for a dual boot?  I get the impression from the comments that is not necessary.  My expectation was that I would set up a partition for XP and then install it, followed by installing Ubuntu.  I would then be able to use Vbox to access XP and apps like quicken through it.  

Thanks.No - you install Vbox on top of Ubuntu. With Vbox you configure a dedicated space for the OS. I believed I used 12 GB dedicated for my XP os; however, I did not have good luck with dynamic disk space, so stick with dedicated disk space.

---

