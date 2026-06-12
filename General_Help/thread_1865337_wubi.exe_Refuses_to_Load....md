---
title: "wubi.exe Refuses to Load..."
date: 2011-10-20
forum: General Help
---

### Post by CyberOptix on 2011-10-20
[FONT="Arial Narrow"][/FONT]

Alright, this is my first post. Tell me how I do.
--------------------------------------------------------
     So I decide to install Ubuntu 11.10 after trying it out in VMWare. This is what I do:

1. Download the Ubuntu torrent from thepiratebay.org (much faster than the official website)
2. Used UltraISO to write the iso to my almost 4GB USB (I chose Bootable)
3. Downloaded Wubi from the Ubuntu website

But when I try to open up wubi.exe, nothing happens other than the cursor showing the "Working in Background" symbol. I've rebooted and cleared out the Temp files and I'm really irritated :( It works on all other versions of Wubi though, which irritates me more. 

Any suggestions?

---

### Post by hhh on 2011-10-20
What the... ? Wubi is a way of installing Ubuntu INSIDE OF WINDOWS and is not needed for a standard Ubuntu install. And don't use Pirate Bay for the ISO, although it's probably fine you don't really know what you're getting. Do some research and then install the official Ubuntu ISO. Some links to help you...

If you want to test Ubuntu inside of Windows...
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If you want to dive right in with Ubuntu on it's own partition...
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Mark Phelps on 2011-10-20
You mentioned VMWare -- so I'm guessing that you're currently running Win7, right?  If not, then ignore the rest of this ...

If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by CyberOptix on 2011-10-20
[FONT="Arial"][/FONT] What... I'm confused. I thought Wubi was used to either Dual-Boot Ubuntu with Windows or to replace Windows with Ubuntu. And I used PirateBay because the official ISO from the website was downloading EXTREMELY slow. I'll look at the links.

---

### Post by bcbc on 2011-10-20
> **CyberOptix said:**
> [FONT="Arial"][/FONT] What... I'm confused. I thought Wubi was used to either Dual-Boot Ubuntu with Windows or to replace Windows with Ubuntu. And I used PirateBay because the official ISO from the website was downloading EXTREMELY slow. I'll look at the links.

Wubi dual boots with a virtual disk. It cannot replace windows with Ubuntu. It's good to try out ubuntu as it's easy to install/uninstall.

Yes you're right you don't need to create a partition for it - that's for a proper dual boot.

PS you can't install wubi from a USB stick *** - if you've downloaded the ISO you can place it in the same directory as wubi.exe on your hard drive and it will use it.
If wubi.exe doesn't run it's likely a conflict with a different version of python already installed on your computer. Check for errors in the log file in the %temp% directory (wubi-xx.xx-revxxx.log) - if it's not there then it's likely python.

---

### Post by CyberOptix on 2011-10-20
[FONT="Arial"][/FONT] Oh, OK. Thanks. I'll post if anything happens.

---

### Post by CyberOptix on 2011-10-20
[FONT="Arial"][/FONT] SUCCESS. I'm running Ubuntu! Thanks!

---

