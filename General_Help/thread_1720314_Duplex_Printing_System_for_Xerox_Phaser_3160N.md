---
title: "Duplex Printing System for Xerox Phaser 3160N"
date: 2011-04-03
forum: General Help
---

### Post by Tybion on 2011-04-03
If your PC is close to your printer, then you don't need this system - use [Gnome Manual Duplex]("http://sourceforge.net/projects/g-manual-duplex/") - a nice GUI utility - instead.

I developed this system because our printer is upstairs and most of our PCs are downstairs, so I needed a system that did not require clicking an 'OK' button on the PC after re-feeding the paper.  The system is fairly complex, but it works, so I thought I might as well make it available to anyone who might find it useful.  This is how it does it .. 
- on a PC the user prints to a cups-pdf printer queue - this creates a PDF file in the user's $HOME/PDF folder
- a background script detects the creation of this PDF file and sends the PDF file in 2 jobs to a printer queue for the 3160N - one for the even pages, one for the odd pages
- a background script is started that monitors the 3160N queue and the printer itself - it uses SNMP to detect when the person has pulled out the tray to re-feed the printer - at this point it releases the second job that prints out the odd pages

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=188138&d=1301999436[/IMG]

To use the code for your own use ..
- change 10.0.0.10 to the IP address of your print server (this could be your own PC)
- change 10.0.0.21 to the IP address of your Xerox Phaser 3160N printer
- change the name 'Phaser-BW' to the name of your 3160N printer queue
- in 'install_duplex', change the download URL to a web-server where you have your modified copies of the scripts

I use the 'Generic PCL 6/PCL XL Printer Foomatic/pxlmono' driver on the ubuntu print server.

This code could also be modified for any other networked printer that reports its status using the SNMP protocol.

---

