---
title: "Installing Epson Stylus Printer Wirelessly"
date: 2011-11-21
forum: General Help
---

### Post by TovarishChump on 2011-11-21
I have just bought an epson stylus SX235w printer. I am new to linux and ubuntu. I have tried the avasys website and downloaded the correct driver from this website: 
[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/)
I have the packages in "downloads" but i dont know what the next step is. Please help. I am a complete newb.
TovarishChump

---

### Post by ajgreeny on 2011-11-21
Have you tried attaching it by USB, assuming that is possible, to see if the printer is recognised already?  Ubuntu often detects and can print using Epson machines with no further driver installation.

If that is so, you will simply need to follow the instructions for wireless printing in **System->Administration->Printing** if using the classic desktop, and wherever **Printing** is in unity.

---

### Post by ikt on 2011-11-21
> **ajgreeny said:**
> and wherever **Printing** is in unity.

The printing utility comes up when you search for print, printing or printer in the dash.

---

### Post by Mark Phelps on 2011-11-21
You could try using CUPS to install the printer.

Open a browser and enter "localhost:631"

Once that page comes up, use the menu option to Add a Printer.

When that opens, see if it lists your printer has having been discovered.  IF it does, then  choose it and continue through the menus and pages to add the printer and the drivers.

Suggest this because CUPS in 11.10 seems to do an especially good job of detecting networked printers.

---

### Post by TovarishChump on 2011-11-22
No luck with finding a printer on CUPS (No printer detected). If I try to "add printer they ask me for a password and I am not a member. I can print on a wired connection via USB, however I want to print wirelessly. Bear in mind that the printer is completely new and the only usage it has had is wired to my Ubuntu computer. I also cannot scan even with a wired connection. I am also fairly new to Ubuntu. The wireless is working now, I think due to me installing the drivers form the Avasys website, however the wireless is still not working. Thanks for the previous suggestions but the issue still remains.
Sorry if I'm saying stupid things, but I'm still getting used to ubuntu after years with mac.

---

### Post by YannBuntu on 2011-12-08
Hello
Italian users have managed to solve the problems (scanner and wifi):
[http://translate.google.fr/translate?hl=fr&sl=it&tl=en&u=http%3A%2F%2Fwww.linuxmint-italia.org%2Findex.php%3Faction%3Dprintpage%3Btopic%3D11183.0](http://translate.google.fr/translate?hl=fr&sl=it&tl=en&u=http%3A%2F%2Fwww.linuxmint-italia.org%2Findex.php%3Faction%3Dprintpage%3Btopic%3D11183.0)

(original: [http://www.linuxmint-italia.org/index.php?action=printpage;topic=11183.0%29](http://www.linuxmint-italia.org/index.php?action=printpage;topic=11183.0%29) )

I am thinking of buying this printer, so please confirm if it works for you ?

---

### Post by YannBuntu on 2011-12-28
Dear all, I bought the Epson stylus sx235w and managed to make it work (all except the wifi):

**1)** connect the ink cartridges (if you don't the scanner won't work either)
**2)** go to [http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/) , click on "All-In-One", select "sx235w", then at the bottom apply. This page will appear:
[[img]http://pix.toile-libre.org/upload/thumb/1325071942.png[/img]](http://pix.toile-libre.org/?img=1325071942.png)
from this page, download the following packages:
- "iscan-network-nt_1.1.0-2_i386.deb" (if your Ubuntu is 32bits) or "iscan-network-nt_1.1.0-2_amd64.deb" (if your Ubuntu is 64bits)
- iscan-data_1.13.0-1_all.deb
- iscan_2.28.1-3.ltdl7_i386.deb (32bits) or iscan_2.28.1-3.ltdl7_amd64.deb (64bits)

**3)** then come back at the top of the page, in the "Printer Driver" section, click on "Please refer to the page", another page will appear:
[[img]http://pix.toile-libre.org/upload/thumb/1325071960.png[/img]](http://pix.toile-libre.org/?img=1325071960.png)
in this page, search "sx235w" and just below download the following package:
epson-inkjet-printer-201108w_1.0.0-1lsb3.2_i386.deb (32bits) or epson-inkjet-printer-201108w_1.0.0-1lsb3.2_amd64.deb (64bits)

4) Install those 4 packages by double-click on it, or via the "dpkg -i *.deb" command.

Nota1: i think the printing drivers is already in the Ubuntu repositories, which explains why some people can automatically use the printing but not the scanner function.
Nota2: **if you find a solution for the WIFI, please tell me** ;)

EDIT: i created 2 bug reports:
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/909345](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/909345)
[https://bugs.launchpad.net/ubuntu/+source/epson-inkjet-printer-escpr/+bug/909350](https://bugs.launchpad.net/ubuntu/+source/epson-inkjet-printer-escpr/+bug/909350)

---

### Post by tomkasz on 2012-02-05
Hello, I bought sx235w and wifi setup the only option is to install Windows in VirtualBox on Linux. Unfortunately, Wine does not support USB at now. VirtualBox allows you to install the new firmware. Unfortunately, the printer is having problems with WPA. Even the new firmware and new installer enable the correct connection to the network only wifi with no security or WEP 13 character.

---

### Post by YannBuntu on 2012-02-05
Hi tomkasz thanks for the tip. Where do you find the firmware?

---

### Post by tomkasz on 2012-02-05
Hello.
Just install the first two options from Epson software (1 - driver and software, 2 - Network Management Software). In the VirtualBox set the network card in bridged mode with a physical card in the local network, so that the installer will be able to validate the connection to the wifi. After installing the application itself should propose an update if not, you must select the update entry from epson printer icon in the tray. During installation, the printer must be connected by USB. VirtualBox version licensed as Puel (extension pack) has the USB 2.0 support. When installing the printer firmware, update software will reset your sx235w, when the rates return to normal, you need to re-connect the printer in VirtualBox, the update will be continued. To simplify instalation and use, I recommend setting a fixed ip lease on the router for the printer. Using this printer and scanner by wifi in Ubuntu 10.04 is lots of fun :-). Both 32 and 64 bit works perfectly.

---

### Post by tomkasz on 2012-02-05
I could write chaotically. This installer runs from a CD does it all :-). And installed software will download and install the new firmware. I don't know another option to update the firmware. BTW: Is there any better documentation somewhere for this printer, because what is added to it, and online at: Epson is a joke ;-).

---

### Post by theRealGBee on 2012-02-06
You do NOT need windows to use Wi-Fi, but you do need a wireless router/access point which supports WPS (and a wired/wireless connection from your PC to the router). I think that's part of the problem for some people here.

I had the printer setup and working (scanning/printing) over the wireless network in 15 minutes.

I'll describe the steps from beginning to end, these should apply to other Epson models such as the SX230:

1. First you need to setup the printer, install the cartridges and wait until the power light stops flashing.

2. Go to [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)
 and type "Stylus SX235" exactly as written into the search box. Don't include the 'w' at the end!

3. Downloading and install ALL four packages shown in the list

4. Cups should be restarted automatically, but if not do so manually

5. Press the WPS button on your wireless router and then within 30 seconds press and hold the WiFi button on the printer until the wifi light on the printer starts flashing. The light should turn steady green if it's connected, your router should confirm that this has been successful.

5. Go to [https://127.0.0.1:631](https://127.0.0.1:631) in the browser, Select Administration, Find Printer. (Disconnect usb first if you've previously connected it)

6. Click on the printer name, select Epson as the make and then Epson Stylus SX235 from the list of models. Click through the remaining dialogues and the printer will be added.

7. Print a test page just to make sure

Scanner

8. Assuming you know about Sane/iscan, the only step required here is to edit as root (sudo) /etc/sane.d/epkowa.conf - add the line "net {IP of printer}" (Cups will mention the IP during setup, otherwise check your router for the assigned address.

---

### Post by tomkasz on 2012-02-07
WPS is not everywhere and in everything ;). I personally do not like automation. Our printer probably has problems with WPA-TKIP, AES should work, but not checked. As for the rest of you are right and so I installed it in writing in advance. In addition, these same drivers are here [http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/) that's site is Epson owner probably and there can be no problem to find the same drivers after the full name sx235w along with useful instructions.

---

### Post by dresdaforum on 2012-03-26
hi to all...scuse my english,I'm italian
I bought an Epson SX235W wifi (without LCD control panel) and wanting to connect to wi-fi on my Ubuntu 10.04 I ran into some problems:

1) the wizard to connect the printer with the supplied installation CD contains only a mode under Windows
2) the wifi card printer setup mode does not provide DHCP and at least you can understand any static IP, or MAC ADDRESS
3) if you want to connect to the existing network as a router that has the function OPS (in my case a USRobotics router) then you are not able to do so

I then tried to overcome all these variables are able to operate in both the WIFI printer and the scanner ....
 
[http://2.225.140.8/phpbb/viewtopic.php?f=1&t=69&sid=7bc3092c22107795542fbe3775f18a69](http://2.225.140.8/phpbb/viewtopic.php?f=1&t=69&sid=7bc3092c22107795542fbe3775f18a69)

---

### Post by itsterry on 2012-05-01
> **theRealGBee said:**
> You do NOT need windows to use Wi-Fi, but you do need a wireless router/access point which supports WPS (and a wired/wireless connection from your PC to the router). I think that's part of the problem for some people here.

I had the printer setup and working (scanning/printing) over the wireless network in 15 minutes.

I'll describe the steps from beginning to end, these should apply to other Epson models such as the SX230:

1. First you need to setup the printer, install the cartridges and wait until the power light stops flashing.

2. Go to [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)
 and type "Stylus SX235" exactly as written into the search box. Don't include the 'w' at the end!

3. Downloading and install ALL four packages shown in the list

4. Cups should be restarted automatically, but if not do so manually

5. Press the WPS button on your wireless router and then within 30 seconds press and hold the WiFi button on the printer until the wifi light on the printer starts flashing. The light should turn steady green if it's connected, your router should confirm that this has been successful.

5. Go to [https://127.0.0.1:631](https://127.0.0.1:631) in the browser, Select Administration, Find Printer. (Disconnect usb first if you've previously connected it)

6. Click on the printer name, select Epson as the make and then Epson Stylus SX235 from the list of models. Click through the remaining dialogues and the printer will be added.

7. Print a test page just to make sure

Scanner

8. Assuming you know about Sane/iscan, the only step required here is to edit as root (sudo) /etc/sane.d/epkowa.conf - add the line "net {IP of printer}" (Cups will mention the IP during setup, otherwise check your router for the assigned address.


Thank you! This worked flawlessly for me!

---

### Post by chitebbeiv on 2012-08-06
> **theRealGBee said:**
> Scanner

8. Assuming you know about Sane/iscan, the only step required here is to edit as root (sudo) /etc/sane.d/epkowa.conf - add the line "net {IP of printer}" (Cups will mention the IP during setup, otherwise check your router for the assigned address.

my scanner still doesn't work... 
already edited the epkowa.conf file, but maybe there's something else to manage...

EDIT: the scanner started working now, didn't change anything then I don't know why but that's enough for now \\:D/

---

### Post by ysaric on 2012-08-20
I have an Epson Stylus NX330, but in my sane.d directory no file called epkowa.conf.  I've set the printer/scanner to a static IP, but not sure what to edit at this point.  It looks as if there is a file epson2.conf that in the ## indicates you can set a net address, but making that edit seemed to have no effect.

I can print wirelessly at this point no problem, just trying to get the scanner working over the same setup.  Thanks much for any information provided.

---

### Post by jakslev on 2012-09-21
> **theRealGBee said:**
> You do NOT need windows to use Wi-Fi, but you do need a wireless router/access point which supports WPS (and a wired/wireless connection from your PC to the router). I think that's part of the problem for some people here.

I had the printer setup and working (scanning/printing) over the wireless network in 15 minutes.

I'll describe the steps from beginning to end, these should apply to other Epson models such as the SX230:

1. First you need to setup the printer, install the cartridges and wait until the power light stops flashing.

2. Go to [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)
 and type "Stylus SX235" exactly as written into the search box. Don't include the 'w' at the end!

3. Downloading and install ALL four packages shown in the list

4. Cups should be restarted automatically, but if not do so manually

5. Press the WPS button on your wireless router and then within 30 seconds press and hold the WiFi button on the printer until the wifi light on the printer starts flashing. The light should turn steady green if it's connected, your router should confirm that this has been successful.

5. Go to [https://127.0.0.1:631](https://127.0.0.1:631) in the browser, Select Administration, Find Printer. (Disconnect usb first if you've previously connected it)

6. Click on the printer name, select Epson as the make and then Epson Stylus SX235 from the list of models. Click through the remaining dialogues and the printer will be added.

7. Print a test page just to make sure

Scanner

8. Assuming you know about Sane/iscan, the only step required here is to edit as root (sudo) /etc/sane.d/epkowa.conf - add the line "net {IP of printer}" (Cups will mention the IP during setup, otherwise check your router for the assigned address.

Yup did it for me too. Except I didn't have a WPS so I had to work out how to connect the printer to my non-WPS router :)

Curious?

---

### Post by nortexoid on 2013-01-01
> **theRealGBee said:**
> You do NOT need windows to use Wi-Fi, but you do need a wireless router/access point which supports WPS (and a wired/wireless connection from your PC to the router). I think that's part of the problem for some people here.

I had the printer setup and working (scanning/printing) over the wireless network in 15 minutes.

I'll describe the steps from beginning to end, these should apply to other Epson models such as the SX230:

1. First you need to setup the printer, install the cartridges and wait until the power light stops flashing.

2. Go to [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)
 and type "Stylus SX235" exactly as written into the search box. Don't include the 'w' at the end!

3. Downloading and install ALL four packages shown in the list

4. Cups should be restarted automatically, but if not do so manually

5. Press the WPS button on your wireless router and then within 30 seconds press and hold the WiFi button on the printer until the wifi light on the printer starts flashing. The light should turn steady green if it's connected, your router should confirm that this has been successful.

5. Go to [https://127.0.0.1:631](https://127.0.0.1:631) in the browser, Select Administration, Find Printer. (Disconnect usb first if you've previously connected it)

6. Click on the printer name, select Epson as the make and then Epson Stylus SX235 from the list of models. Click through the remaining dialogues and the printer will be added.

7. Print a test page just to make sure


Thank you very much! I had downloaded the drivers from Epson, it detected the printer and I installed it, but printing wouldn't work. (I'm using KDE, Kubuntu.) Strangely the scanner worked over wifi. I found your instructions and set up the printer through the CUPS html page. Now my printer is working flawlessly over wifi. Thanks!

---

### Post by daziel on 2013-01-04
Ubuntu installed a driver from its library for my Epson Workforce 520, but the printer just ejects blank pages (non-stop) for every print job.  I have to turn the printer off.

Ubuntu 10.04 LTS

Thanks
Marc

---

### Post by Athena's Owl on 2013-01-06
> **theRealGBee said:**
> 
3. Downloading and install ALL four packages shown in the list

I'm sorry, these instructions just lost me. I don't understand what they mean. 

I installed ... something that claims to be an epson printer driver, but my computer still doesn't recognize my printer. and i downloaded thato packages, but...how do you install them? you can't just click on them, I tried that.

> 4. Cups should be restarted automatically, but if not do so manually

what's a cups? ETA: oh that's the localhost:631 thing. got it.


> 5. Press the WPS button on your wireless router and then within 30 seconds press and hold the WiFi button on the printer until the wifi light on the printer starts flashing. The light should turn steady green if it's connected, your router should confirm that this has been successful.

I already have my printer hooked up to the router; I used my windows machine to print with it. it's my linux netbook i'm worried about. but I can't use the cd because...netbook.

Do i have to start over and explain my problem from the beginning? I have to do that, don't I? This doesn't make any sense to anyone here. Sorry. I'm on hour four of trying to find the solution myself.

ETA again: I found the print utility. it asks me to add a new printer, and i chose network, because it's on a wireless network, but maybe that's a bad assumption, and it asks me for Host: 

what am I supposed to write there? what is my host, is it my (terrible!) router SSID or is it the name of the printer in my network, or the name of the printer, or what?

---

### Post by meng1usa on 2013-01-12
that worked for me!
Thank you a lot!

> **theRealGBee said:**
> You do NOT need windows to use Wi-Fi, but you do need a wireless router/access point which supports WPS (and a wired/wireless connection from your PC to the router). I think that's part of the problem for some people here.

I had the printer setup and working (scanning/printing) over the wireless network in 15 minutes.

I'll describe the steps from beginning to end, these should apply to other Epson models such as the SX230:

1. First you need to setup the printer, install the cartridges and wait until the power light stops flashing.

2. Go to [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)
 and type "Stylus SX235" exactly as written into the search box. Don't include the 'w' at the end!

3. Downloading and install ALL four packages shown in the list

4. Cups should be restarted automatically, but if not do so manually

5. Press the WPS button on your wireless router and then within 30 seconds press and hold the WiFi button on the printer until the wifi light on the printer starts flashing. The light should turn steady green if it's connected, your router should confirm that this has been successful.

5. Go to [https://127.0.0.1:631](https://127.0.0.1:631) in the browser, Select Administration, Find Printer. (Disconnect usb first if you've previously connected it)

6. Click on the printer name, select Epson as the make and then Epson Stylus SX235 from the list of models. Click through the remaining dialogues and the printer will be added.

7. Print a test page just to make sure

Scanner

8. Assuming you know about Sane/iscan, the only step required here is to edit as root (sudo) /etc/sane.d/epkowa.conf - add the line "net {IP of printer}" (Cups will mention the IP during setup, otherwise check your router for the assigned address.

---

