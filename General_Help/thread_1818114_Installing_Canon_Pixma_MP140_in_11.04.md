---
title: "Installing Canon Pixma MP140 in 11.04"
date: 2011-08-04
forum: General Help
---

### Post by lawra on 2011-08-04
I was using 10.04 until a few days ago, and with 10.04 my printer worked fine, I used the default drivers for MP150 and that worked fine. 

But now I'm using 11.04 and I'm trying to instal the printer with the default drivers for MP150 but it's not working.

When Ubuntu tries to find the driver is not giving me any result for MP140, so I'm selecting the option **"CANON PIXMA MP150 - CUPS+Gutenprint v5.2.6 Simplified [en] (Recomended)"** and allows me to click next and to give a name to the printer and to hit next, but then the windows closes and that's it 

then I go to **System > Admin > Printer** and I double click the printer I just created and I click Print Test Page and then it gives me **"Printer Status: Processing - Printing Page 1.8%"** and after 4minutes or so gives me **"Installation or actualization of package "python-xmpp 0.4.1-cvx20080505.2" failed"** and that's it 

Is there a way to fix this? I have no idea why this is not working since it worked fine in 10.04, and I really need to use the printer and the scanner as soon as possible :S 

thanks in advance!!! 

(sorry if it's a little bit hard to understand what I'm saying, my system is in spanish and it's a bit hard to translate)

---

### Post by demonipuch on 2011-08-05
Hello

You should use this [PPA]("https://launchpad.net/%7Emichael-gruz/+archive/canon"). It provides many Canon PIXMA drivers.

To add the ppa to your repository list:
```
sudo add-apt-repository ppa:michael-gruz/canon
```To install your printer and scanner drivers :
```
sudo apt-get update
sudo apt-get install cnijfilter-mp140series scangearmp-mp140series
```Now go to Admin > System > Printer, remove your old printer entry and add a new one.

Hope it helped

---

### Post by Duncan Williams on 2011-08-05
If you still stuck with it, post back.
I had a bit of an issue with my canon mp270 and the same drivers and CUPS. I got it all good in the end so might be able to help.

---

### Post by lawra on 2011-08-05
THANK YOU!!!!!!!!!!!!

that completely solved the problem, I just deleted the printer, connected the printer to the USB again and it was installed in matter of seconds. after that, I had just to press the start button in the printer and it printed the test page with no problems, and the scanner works just as usual

I love you so much now

[EDIT] thanks for the offering, Duncan, but I'm good to go now :D

---

### Post by IdealisticSlob on 2011-12-13
Thank you,'demonipuch',your fix worked perfectly for me (in 11.10). Much appreciated.

---

### Post by møllerik on 2011-12-13
I've tryed to install a Canon PIXMA iP4850 on Ubuntu 11.04, and I tryed the solution above and got this answer:

erik@erik-Vostro-1720:~$ sudo apt-get install cnijfilter-mp140series scangearmp-mp140series
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ        
Læser tilstandsoplysninger... Færdig
cnijfilter-mp140series er i forvejen den nyeste version.
scangearmp-mp140series er i forvejen den nyeste version.
0 opgraderes, 0 nyinstalleres, 0 afinstalleres og 0 opgraderes ikke.
1 ikke fuldstændigt installerede eller afinstallerede.
Efter denne handling, vil 0 B yderligere diskplads være brugt.
Vil du fortsætte [J/n]? J
Sætter firmware-b43-installer (4.150.10.5-5) op...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: fejl under behandling af firmware-b43-installer (--configure):
 underproces installerede post-installation-script returnerede afslutningsstatus 1
Der opstod fejl under behandlingen:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

What can I do ????

---

