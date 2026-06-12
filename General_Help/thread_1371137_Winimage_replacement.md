---
title: "Winimage replacement?"
date: 2010-01-03
forum: General Help
---

### Post by clevertomato on 2010-01-03
I want to build a print server per instructions at:

[http://members.shaw.ca/nicholas.fong/printsrv/](http://members.shaw.ca/nicholas.fong/printsrv/)

It calls for using Winimage to make a bootable floppy image with particular files, as described in excerpt below:

> [LEFT](3b) Invoke winimage, [drag and drop]("http://members.shaw.ca/nicholas.fong/printsrv/dragdrop.png") the printsrv image in it. Then drag and drop the correct **modules.lrp** into the winimage window. The winimage windows should look like [this]("http://members.shaw.ca/nicholas.fong/printsrv/loaded.png"). Save your newly assembled image [click **[COLOR=#800000]F[/COLOR]**ile **[COLOR=#800000]S[/COLOR]**ave].[/LEFT]
(4) Insert a [ [COLOR=#800000]**new, high-quality**[/COLOR]]("javascript:alert('bulk%20or%20used%20floppy%20disk%20will%20not%20work%20reliably%20with%20high-density%20formatted%20LRP%20disk');")[COLOR=#800000] [/COLOR]floppy disk in drive A. 
[LEFT] Click [COLOR=#800000]**D**[/COLOR]isk...[COLOR=#800000]**W**[/COLOR]rite to create a Print Server **[COLOR=#008080]boot-floppy[/COLOR]**. 
The floppy generated is in a standard 1.4M format.[/LEFT]


So, I don't want to have to use Windows or Winimage. There must be a way to accomplish this step in Linux. Will dd do it? Do I need another app?

---

### Post by gsmanners on 2010-01-03
Linux generally uses CUPS for printing. In Ubuntu, you set up the server and the clients using the "Printing" applet.

See [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by clevertomato on 2010-01-03
I don't want to print from Ubuntu. I can already do that. I want to **build** a dedicated print server to share non-network printers on the network using an old 386, 486, or 586 PC.

All I'm asking here is if there is a Linux replacement that can do what Winimage can do, specifically the part I quoted.

---

### Post by harold4 on 2010-01-03
Run WinImage via [WINE]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=4528")

---

### Post by clevertomato on 2010-01-04
I appreciate the comments so far intended to help, but I don't think my question or intent has been understood.

I don't want to setup printing in Ubuntu. I already have that working. I have one or more PCs with Windows installed, so I can easily use Winimage to accomplish what I want and be done with it. However, if my goal were to take the **easiest** route with everything (at least in the short term), I would never have tried Linux to begin with. That's not the point. The point is, I don't WANT to HAVE to depend on Windows, or WINE. My question **is** whether **there** is **something native to Linux that will accomplish what Winimage accomplishes? Yes or no?** I KNOW I can use Winimage. I don't want to. I want to use Linux (WINE doesn't count).

I don't want to offend anyone, it's just that I'm trying to make myself clear so nobody else's time is wasted trying give me solutions that don't address my question.

---

### Post by gsmanners on 2010-01-04
Sorry. Linux isn't Windows, nor is it DOS.

---

### Post by stinger30au on 2010-01-04
why not wack ubuntu on to the pc/server

set it up so it can print to all the printers you decide to connect to it


share the printers on the lan

ta da!

instant printer server for nuffin

---

### Post by clevertomato on 2010-01-04
No, Linux isn't Windows or DOS. That's irrelevant.

Can Ubuntu fit onto one floppy disk and run on a 386 or 486 PC with 8 mb RAM? No. That's why I don't wack Ubuntu on a PC and use it for a print server.

I found the answer to my own question with some research and trial and error.

I used ```
dd if=/path/to/linuxrouterproject.ima of=/dev/fd0
``` to write the bootable floppy image to a floppy disk.

---

