---
title: "Printing without Spooling"
date: 2006-04-11
forum: General Help
---

### Post by Video Toaster on 2006-04-11
I recently set up an Epson thermal receipt printer with Kubuntu for my local library.  I have CUPS set to RAW output and Innovative Millennium, their Java-based circulation program, set to text output.

However, CUPS is taking way too long to spool receipt print jobs - much longer than Windows ever took. It prints two or three lines, stops, prints two or three more lines, and so on. Is there any way I can set Kubuntu to not spool print jobs for that printer and just send print jobs for that printer directly to lp0?

---

### Post by Video Toaster on 2006-04-12
*bump*

Anybody?

---

### Post by hoarythehedgehog2009 on 2006-04-15
I feel bad that so many people have looked at your thread, but have not know the answer.  If your definition of spooling is: "To store (data sent to a printer) in a buffer, allowing the program that sent the data to the printer to resume its normal operation."  I don't know how to "stop" it from spooling, but to make it spool faster, try a lighter weight window manager, such as XFCE...

Open the terminal and type in the following:

sudo apt-get install xubuntu-desktop

This will not upgrade the computer to Dapper (which I am assuming you don't want to do) just install XFCE.

If this does not help, HANG IN THERE! (or just re-install windows)  :)

---

### Post by Video Toaster on 2006-04-16
[QUOTE=hoarythehedgehog2009]I feel bad that so many people have looked at your thread, but have not know the answer.  If your definition of spooling is: "To store (data sent to a printer) in a buffer, allowing the program that sent the data to the printer to resume its normal operation."  I don't know how to "stop" it from spooling, but to make it spool faster, try a lighter weight window manager, such as XFCE...

Open the terminal and type in the following:

sudo apt-get install xubuntu-desktop

This will not upgrade the computer to Dapper (which I am assuming you don't want to do) just install XFCE.

If this does not help, HANG IN THERE! (or just re-install windows)  :)[/QUOTE]
Hey, thanks for the reply!  That is what I meant, but it seems that I was on the wrong track.  The problem lays not with CUPS but with my parallel port, which is extremely slow - sending text to lp0 as root in Konsole is also slow.  It seems DMA is not enabled for lp0, which I think is slowing down output.  I've found something I can try putting in /etc/modprobe.d/parport_pc to make it use DMA, so I'll post back when I find out if it works or not.

Thanks again!

---

### Post by Video Toaster on 2006-04-21
IT WORKS!!! :D

For anybody else with this problem, here's what I did:

[LIST]
[*]Go into BIOS and check the settings for the parallel port.  Make sure it is set to ECP and that DMA is enabled.  Write down the IO address and the DMA address.
[*]Reboot and open Konsole.  Type the following:
```
sudo nano /etc/modprobe.d/parport_pc
```
[*]Within nano, type the following:
```
alias parport_lowlevel parport_pc
options parport_pc io=0x378 irq=7 dma=3

```
Replace IO and DMA values with the ones you wrote down from BIOS.  Also, make sure you leave a blank line at the end of the file.  Press CTRL+O, press enter to save, and then press CTRL+X to quit nano.
[*]Reboot.  Once KDE has finished starting, open KSystemLog (under System in the K-Menu).  Filter by "parport0".  Look for the most recent line that begins "parport0".  If DMA is mentioned, you're done!  If it's not, I don't know how to help you.  :D
[/LIST]

Hope that made some sense and that it helps somebody... please post a reply if it helped you!

---

