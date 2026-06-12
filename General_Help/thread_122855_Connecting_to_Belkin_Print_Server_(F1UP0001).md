---
title: "Connecting to Belkin Print Server (F1UP0001)"
date: 2006-01-28
forum: General Help
---

### Post by prateek51 on 2006-01-28
Hi,

Im trying to connect my Epson Styuls C62 printer to ubuntu. The printer is connected through a print server (192.168.1.101) and works fine on all my windows boxes. However i cant connect to it using linux and ive tried several different settings!

Help Would be appreciated

---

### Post by gslater on 2006-01-29
I have exactly the same problem...can you ping your printer on that address?  Mine says that it is connected to 192.168.0.8 but when I try and ping it I have no luck

Anybody else have this type of problem?

---

### Post by prateek51 on 2006-01-29
Yep, pinging 192.168.1.101 works. I tried going to 192.168.1.101:9100 (the port my printer is on)  and it makes the printer print what type of browser im using. However it gets stuck half way and i have to manually take it out.

I wonder if this means anything?

---

### Post by gslater on 2006-01-29
Did you have to install any linux drivers to get that far or were you able to get the printer recognised with the existing Breezy build

---

### Post by prateek51 on 2006-01-29
Nope, it was recogonized without me having to do anything. What happens if you try 192.168.0.8:9100?

---

### Post by gslater on 2006-01-29
It says host unreachable....but something odd also happens when I ping just 192.168.0.8....it pings that address first and then the second ping goes to 192.168.0.5 (which is the address I have my linux PC on

---

### Post by spamnchips on 2006-08-19
It can be done.  I am using SUSE 10.1 and have managed to get Linux to talk to my Belkin Printer Server by using KDE Print Manager and TCP/IP print via CUPS.  BTW, the F1UP0001 uses port 515 as a default.

Regards

John

---

### Post by jctilly on 2006-09-18
hello

response here

[http://ubuntuforums.org/showthread.php?t=122746&highlight=F1UP0001](http://ubuntuforums.org/showthread.php?t=122746&highlight=F1UP0001)

jc

---

### Post by nickpaton on 2007-06-30
Update for Feisty

In Printer setup select Network printer > TCP/Socket.

Host:  IP address of the Belkin server.

Port: 9100 for Printer 1 port on server, or 9101 for Printer 2 port on server.

Give suitable names for the printer and location.

I also set up CUPS using [this]("http://ubuntuforums.org/showthread.php?t=480039") excellent HOWTO.

---

### Post by stephanvaningen on 2007-11-23
Gutsy install steps:
--
I got this working by adding the printer as a HP JetDirect printer, so with these steps:

1/2 Setup the print server
*I found out that most problems on getting the print server set up for wireless is because the web pages served by the print server are not well handled by many browsers. I had problems selecting the correct network security in following web browsers: lynx, firefox (2 and 3), opera, iceape, epiphany. Finally I could have good forms on my browser with Konqueror (Konqueror crashed regularly after a few page clicks, but it did the job ;-))
*Setup the network switch off DHCP and select a free IP address for your network.

2/2 Add printer (attached to the print server) to your computer
*Go to System, Administration, Printing.
*Click New Printer
*Choose AppSocket/HP JetDirect
*Hostname: IP address of the wireless printer
*Port: 9100 for first printer, 9101 for second printer
*Click Forward and go on with the printer wizzard to select brand, model and settings as you would do for a local printer

It worked great for me!

---

### Post by Qbert on 2007-11-25
> **stephanvaningen said:**
> Gutsy install steps:
--
I got this working by adding the printer as a HP JetDirect printer, so with these steps:

1/2 Setup the print server
*I found out that most problems on getting the print server set up for wireless is because the web pages served by the print server are not well handled by many browsers. I had problems selecting the correct network security in following web browsers: lynx, firefox (2 and 3), opera, iceape, epiphany. Finally I could have good forms on my browser with Konqueror (Konqueror crashed regularly after a few page clicks, but it did the job ;-))
*Setup the network switch off DHCP and select a free IP address for your network.

2/2 Add printer (attached to the print server) to your computer
*Go to System, Administration, Printing.
*Click New Printer
*Choose AppSocket/HP JetDirect
*Hostname: IP address of the wireless printer
*Port: 9100 for first printer, 9101 for second printer
*Click Forward and go on with the printer wizzard to select brand, model and settings as you would do for a local printer

It worked great for me!


Thanks that worked for me.

---

### Post by webchimp on 2008-04-16
[CENTER][SIZE="5"]Victory![/SIZE][/CENTER]

After two hours of proding and poking I have finally managed to print wirlessly from my Linux box. I have tried a number of different suggestions found in different forums/posts, but the instructions in this thread finally got me to my goal.

Printer 1: Epson R300
Printer 2: Samsung 1510

Took two attempts though as I had got my printers the wrong way round and assingned them the wrong ports. So when I tried prnting a test page for the Samsung, a lot of junk came spewing out of the Epson.:oops:

Still, it all came out right in the end. You never know, in five to ten years I might finally get the hang of this Linux malarkey.

---

