---
title: "New printer (all in one) for Ubuntu Lucid systems."
date: 2010-08-02
forum: General Help
---

### Post by casbahdk on 2010-08-02
I am looking for a new wireless all in one printer for my Lucid based systems. The two main candidates don't come up when I try to Google or look on the Open Printing database:

1) Epson SX425W
2) HP PhotoSmart WiFi Q8447

Does anyone have any experience with either printer? Is there decent Linux support? Also for wireless scanning?

Cheers

---

### Post by willscuff on 2010-09-06
The Epson SX425W works OK with Lucid using the Avasys drivers and software

Printing over USB:[INDENT]
[LIST]
[*]Install lsb
[*]Use the appropriate Avasys driver from[ http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/]("http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/") - for me it was [http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-i386/epson-inkjet-printer-nx420_1.0.0-1lsb3.2_i386.deb](http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-i386/epson-inkjet-printer-nx420_1.0.0-1lsb3.2_i386.deb)
[/LIST]
[/INDENT]Scanning over USB: [INDENT]
[LIST]
[*] Works "out-of-the box" e.g. with Applications > Graphics > Simple Scan
[/LIST]
[/INDENT]Printing over Wifi:[INDENT]
[LIST]
[*] Set the printer up with IP address (e.g. 192.168.0.5), SSID, password etc. using the Network Settings menu on the LCD display. Setup via a GUI over USB is only possible via Windows, using the install CD.
[*] With lsb and driver installed as for USB above do[INDENT]System > Administration > Printing > Add > Network Printer
[/INDENT]
[*] Select Epson Stylus SX420W(192.168.0.5), leave as default Passthru Mode.
[*] Click on Forward, wait for driver search to complete, then modify Printer name, Description and Location as appropriate
[/LIST]
[/INDENT]Scanning over Wifi, as suggested by olivers at [http://ubuntuforums.org/archive/index.php/t-1089972.html](http://ubuntuforums.org/archive/index.php/t-1089972.html):[INDENT]
[LIST]
[*] Install iscan for the GT20000 from [http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do) - for me it was iscan-data_1.0.1-1_all.deb, iscan_2.25.0-1.ltdl7_i386.deb, iscan-network-nt_1.1.0-2_i386.deb
[*] sudo sh -c "echo net 192.168.0.5 >> /etc/sane.d/epkowa.conf (modify IP address 192.168.0.5 as appropriate)
[*] check iscan S/W works over USB with Applications > Graphics > Image Scan! for Linux - this seemed to initialise the settings for the next step ..
[*] run iscan S/W or xsane and select the available device tagged [epkowa:net:192.168.0.5]
[LIST]
[*]The device tagged [epson2:net:192.168.0.5] gives an I/O error and locks the printer/scanner if it is used. To   prevent this option being offered comment out the "net autodiscovery" entry in /etc/sane.d/epson2.conf
[/LIST]
 
[/LIST]
[/INDENT]

---

### Post by sandyd on 2010-09-06
> **casbahdk said:**
> I am looking for a new wireless all in one printer for my Lucid based systems. The two main candidates don't come up when I try to Google or look on the Open Printing database:

1) Epson SX425W
2) HP PhotoSmart WiFi Q8447

Does anyone have any experience with either printer? Is there decent Linux support? Also for wireless scanning?

Cheers
All HP printers work OOB because of HPLIP. Not sure about wifi tho.
You can check if its supported by looking up the printer on the HPLIP site.

---

### Post by casbahdk on 2010-09-07
Thanks the informative reply Carlee.

---

### Post by casbahdk on 2010-10-11
> **willscuff said:**
> The Epson SX425W works OK with Lucid using the Avasys drivers and software

Printing over USB:[INDENT]
[LIST]
[*]Install lsb
[*]Use the appropriate Avasys driver from[ http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/]("http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/") - for me it was [http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-i386/epson-inkjet-printer-nx420_1.0.0-1lsb3.2_i386.deb](http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-i386/epson-inkjet-printer-nx420_1.0.0-1lsb3.2_i386.deb)
[/LIST]
[/INDENT]Scanning over USB: [INDENT]
[LIST]
[*] Works "out-of-the box" e.g. with Applications > Graphics > Simple Scan
[/LIST]
[/INDENT]Printing over Wifi:[INDENT]
[LIST]
[*] Set the printer up with IP address (e.g. 192.168.0.5), SSID, password etc. using the Network Settings menu on the LCD display. Setup via a GUI over USB is only possible via Windows, using the install CD.
[*] With lsb and driver installed as for USB above do[INDENT]System > Administration > Printing > Add > Network Printer
[/INDENT]
[*] Select Epson Stylus SX420W(192.168.0.5), leave as default Passthru Mode.
[*] Click on Forward, wait for driver search to complete, then modify Printer name, Description and Location as appropriate
[/LIST]
[/INDENT]Scanning over Wifi, as suggested by olivers at [http://ubuntuforums.org/archive/index.php/t-1089972.html](http://ubuntuforums.org/archive/index.php/t-1089972.html):[INDENT]
[LIST]
[*] Install iscan for the GT20000 from [http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do) - for me it was iscan-data_1.0.1-1_all.deb, iscan_2.25.0-1.ltdl7_i386.deb, iscan-network-nt_1.1.0-2_i386.deb
[*] sudo sh -c "echo net 192.168.0.5 >> /etc/sane.d/epkowa.conf (modify IP address 192.168.0.5 as appropriate)
[*] check iscan S/W works over USB with Applications > Graphics > Image Scan! for Linux - this seemed to initialise the settings for the next step ..
[*] run iscan S/W or xsane and select the available device tagged [epkowa:net:192.168.0.5]
[LIST]
[*]The device tagged [epson2:net:192.168.0.5] gives an I/O error and locks the printer/scanner if it is used. To   prevent this option being offered comment out the "net autodiscovery" entry in /etc/sane.d/epson2.conf
[/LIST]
 
[/LIST]
[/INDENT]

Wow, very nice guide. Thanks. I just bought the Epson SX425W today.

---

### Post by willscuff on 2010-10-18
Epson SX425W printing and scanning still works OK for me after an upgrade from Lucid to Ubuntu 10.10 (Maverick Meerkat). I haven't tried a clean install of the Avasys driver/iScan software under Maverick.

---

### Post by casbahdk on 2010-10-19
> **willscuff said:**
> Epson SX425W printing and scanning still works OK for me after an upgrade from Lucid to Ubuntu 10.10 (Maverick Meerkat). I haven't tried a clean install of the Avasys driver/iScan software under Maverick.

Thanks for the update. BTW, do you know if two scanner drivers can exist peacefully together on a system? I have an Epson Perfection V30 connected to my desktop box via USB.

---

### Post by willscuff on 2010-10-19
> **casbahdk said:**
> Thanks for the update. BTW, do you know if two scanner drivers can exist peacefully together on a system? I have an Epson Perfection V30 connected to my desktop box via USB.

I don't have experience with that scenario.You might have to tweak the sane-epson2 configuration file if you have problems.

---

### Post by Naiki Muliaina on 2010-11-02
> **willscuff said:**
> 
[/INDENT]Printing over Wifi:[INDENT]
[LIST]
[*] Set the printer up with IP address (e.g. 192.168.0.5), SSID, password etc. using the Network Settings menu on the LCD display. Setup via a GUI over USB is only possible via Windows, using the install CD.

[/LIST]


Silly question time! Is it at all possible to set up the ip address etc over the LCD? (Ie, without the CD). If yes, how on earth do you do it?

---

### Post by TheAnachron on 2010-11-02
I use several printers, such as Canon and HP. All work out of the box. 
(A network printer, all in one, was installed with search for network printers for example)

---

### Post by willscuff on 2010-12-07
For setup instructions of the Epson SX425W via the LCD panel, search for "How do I set up my Wi-Fi enabled All-In-One on a wireless infrastructure network without the network setup cable and software CD-ROM?" to find the Epson article at 
[http://www.epson.co.uk/Store/Printers-and-All-in-Ones/Epson-Stylus-SX425W/Drivers-Support]("http://www.epson.co.uk/Store/Printers-and-All-in-Ones/Epson-Stylus-SX425W/Drivers-Support")

---

### Post by Baasje on 2011-01-07
First I want to thank willscuff for writing the guide for scanning over WIFI.
It worked instantly with my Epson Stylus SX420W.

But I am wondering if someone is able to use the scan button on the scanner.
Both wired (USB) and Wireless isn't working.
The printer can't see the ubuntu machine via wifi, and when you plug in the usb cable and try to scan it'll say "Communication Error. Check the connection".

It isn't a huge problem, but it would be a nice feature.

---

### Post by topolinuxx on 2011-01-26
Thank you willscuff, it works nicely ^___^

---

### Post by boy007 on 2011-01-30
> **casbahdk said:**
> I am looking for a new wireless all in one printer for my Lucid based systems. The two main candidates don't come up when I try to Google or look on the Open Printing database:

1) Epson SX425W
2) HP PhotoSmart WiFi Q8447

Does anyone have any experience with either printer? Is there decent Linux support? Also for wireless scanning?

Cheers

[https://alioth.debian.org/tracker/index.php?func=detail&aid=312963&group_id=30186&atid=410366](https://alioth.debian.org/tracker/index.php?func=detail&aid=312963&group_id=30186&atid=410366)

**Date:**
2011-01-30 13:24 			**Priority:**
3 		  		 			**State:**
Open 			
		 		 	         			**Submitted by:**
			Joni-Pekka  kurronen				([boy007-guest]("https://alioth.debian.org/users/boy007-guest/")) 						 			**Assigned to:**
			Nobody (None) 		  	 			 			 			 					**Category: **
None 					**Group: **
None 			 			 					**Resolution: **
None 					  			 			 		**Summary:**
XSANE progarm color/1200dpi/over WIFI will RESET INKJET AMOUNT EPSON SX420W  		 			
			                              **Detailed description** Software: - sane - Xsane - ubuntu 10.10 - Wifi network, push button authorization , Telewell EA-530 - EPson Stylus SX420W  When you start Scanning 1200dpi / color picture  EPSON SX420W will rest to zeor BLACK INK CARTIGE so IT CAN NOT BE USED DUE IT'S ELECTRONICALLY MARKED EMPTY,..., SO I HAVE allready two INK CARTIGES which are very litle used but due lectroniucally marked empty can not use,...  Epson will start scanning but will crash,... You must take all cartiges away and re-install and the it says ,... LOADING,.. after few minutes it's start's normal but YOU CAN NOT USE INK CARTIGES DUE THOSE ARE RESETED ZERO,....  joni [http://sites.google.com/site/jpsreviewsosco/twea530](http://sites.google.com/site/jpsreviewsosco/twea530)
So I made bug report,... Epson is great until you star
scanning,.., scanning WILL EMPTY, RESET, inkjet counter and
you can not use Black cartige,....

Epson dose not connect immidiately via sane over local network,..
..., it take some time,... you must have sane installed and
give printer IP at config files,...

---

### Post by John55 on 2011-06-19
Hi 
I'm new to ubuntu so I hope its OK jumping into the middle of a thread like this. I bought a epson SX425W a week ago, having read that epson was now providing linux drivers. Im currently running ubuntu 11.04 (natty) on my laptop. Epson driver seemed to download ok but when I tried to print, paper just fed through printer until none remained. Installed printer on windows xp desktop, it printed ok. Have separate drive with lucid on desktop, same problem occurred as with natty, paper fed through but nothing printed. Tried connecting with usb, (had been using wifi) but still couldn't get either laptop or desktop to print with ubuntu. Contacted epson support but they said they didn't provide support for ubuntu. Hope someone can help, thanks in anticipation.

---

### Post by zebala on 2011-07-02
Hi John55,

I'm having the exact same problem as you. I got a few good prints but sometimes the printer just (even randomly) starts printing jibberish or feeding the paper through. Are you also using the drivers for 415 which Ubuntu recommended? Also, what kernel are you using? Maybe an older or an newer one would have the 425 one...

---

### Post by mpitt79 on 2011-11-04
John55, zebala: I had the same issue with an SX420W, installing the driver from [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do) and then reinstalling the printer solved the problem.

---

### Post by desconocido on 2012-03-15
> **Naiki Muliaina said:**
> Silly question time! Is it at all possible to set up the ip address etc over the LCD? (Ie, without the CD). If yes, how on earth do you do it?

I have the same problem. When I go to Setup on the printer's LCD panel and then to Network Settings, I do not get the option of "General Network Setup" as suggested by [http://www.epson.co.uk/Store/Printers-and-All-in-Ones/Epson-Stylus-SX420W/Drivers-Support?target=article&extn=.html&articleId=1895]("http://www.epson.co.uk/Store/Printers-and-All-in-Ones/Epson-Stylus-SX420W/Drivers-Support?target=article&extn=.html&articleId=1895")

Do I have old firmware for my printer (bought in Spain last autumn)? Or is there some other approach. I want to set a static IP address for the printer and can't see how to do it.

---

### Post by desconocido on 2012-03-19
> **desconocido said:**
> I have the same problem. When I go to Setup on the printer's LCD panel and then to Network Settings, I do not get the option of "General Network Setup"...I want to set a static IP address for the printer and can't see how to do it.

Couldn't set the static IP address from the Epson, in spite of the manuals saying it was possible. However, I configured the WiFi router to link a static IP address to the MAC address of the Epson, and the printer was content to take it from the router. Solved for me.

---

### Post by desconocido on 2012-03-22
> **willscuff said:**
> The Epson SX425W works OK with Lucid using the Avasys drivers and software
..........
Scanning over Wifi, as suggested by olivers at [http://ubuntuforums.org/archive/index.php/t-1089972.html](http://ubuntuforums.org/archive/index.php/t-1089972.html):[INDENT]
[LIST]
[*] check iscan S/W works over USB with Applications > Graphics > Image Scan! for Linux - this seemed to initialise the settings for the next step ..
[*] run iscan S/W or xsane and select the available device tagged [epkowa:net:192.168.0.5]

[/LIST]
[/INDENT]

Thanks for this. I got scanning working without using a USB cable. I ran Image Scan! for Linux (nothing happened); then I ran xsane (worked OK); then I ran Image Scan! for Linux again (worked OK). Maybe it just needs to run a scanning program once to get set up.

This was an Epson Stylus SX420W on Ubuntu 9.10.

---

