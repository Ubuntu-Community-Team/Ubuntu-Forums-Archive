---
title: "ubuntu does not install either by live cd or wubi"
date: 2011-08-14
forum: General Help
---

### Post by silverrope on 2011-08-14
I have an IBM A20m laptop in which I previously installed Lucid Lynx. It worked for over a year and I was very happy with it. Somehow something got corrupted; stopped booting and got a blank screen so I tried to reinstall Lucid from the live cd. It would not install! I got a blank screen right after selecting to "Install Ubuntu". I then tried to install Natty Narwhal via wubi to run along with Windows 2000. I downloaded the wubi.exe and the iso and the files installed fine. But when I rebooted to complete the installation, it froze just like the live cd. When I boot in verbose mode, I get the following messages near the end:

isapnp: Scanning for PnPcards...
00:0f: ttyS0 at I/O 0x3F8 (irq=4) is a 16550A
serial 0000:00:03.1 : sharing IRQ 11 with 0000:00:03.0

I get the same messages when I try to install using the live cd (noquiet mode).

The mystery for me is that Windows 2000 runs fine on the laptop. And I did have Ubuntu running fine on the same exact laptop for over a year!

So does anyone have any ideas how I can get my Ubuntu back? Or am I now stuck with only Windows 2000 (which means
the laptop will go to the dustbin)?

---

### Post by silverrope on 2011-08-18
OK, I found the solution, but it was thanks to Windows 2000 and not due to Ubuntu error messages.

I went back to Windows 2000 as it looked like Ubuntu would no longer work on my A20m. As I was reinstalling the drivers, I noticed that I could not install the V.90 modem. After several attempts, I gave up. As no one uses a modem, I decided to remove the mini PCI card. I then thought that this might be the reason why Ubuntu failed to install. So after I removed the card, the live CD install worked!

So give 10 points to Windows for their error messages and null points to Ubuntu. But ain't that typical of Linux?

---

