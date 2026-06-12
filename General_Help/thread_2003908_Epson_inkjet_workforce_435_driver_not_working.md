---
title: "Epson inkjet workforce 435 driver not working"
date: 2012-06-14
forum: General Help
---

### Post by LinuxNo0b445 on 2012-06-14
what i did: ubuntu ver. 12.04 LTS

top right panel
-> system settings
-> Printing
"there are no printers configured yet"
-> Add
came up with:
"Epson workforce 435
Enter URI
|> network printer"
-> clicked Epson workforce 435
-> forward
it started searching for a new driver
"searching driver for Epson workforce 435"
*additional drivers window popped open with:
"epson inkjet printer driver for linux (version 1.0.0)[Reccommended]
epson inkjet printer driver (ESC/P-R) for linux (version 1.2.0)


problem: i chose the recommended version first and it started downlaoding (clicked the "activate" button)
Functionality:
  text: 100%
  lineart: 100%
  photo: 100%
  graphics: 100%
Supplied by: Seiko Epson Corporation (printer manufacturer)
Support contacts:
 - Seiko Epson Corporation (voluntary): [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

it prompted for password, and it accepted the password i gave
started downloading a little bit then abruptly stopped and came up with " SOrry, the installation of this driver failed.
Pleasehave alook at the log file for deatils: /var/log/jockey.log"

i loked at the og and went to the last bit.. all the last line said was: "2012-06-15 11:43:17,724 ERROR: Binary package epson-inkjet-printer-201109w has no trusted origin, rejecting"

help, anyone? any details, just ask.. thank you for reading this

---

### Post by mrshr3d on 2012-08-11
[I]**EDIT:  Downloaded driver from [here]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX"),  ****search for "Workforce 435"**

Selected the first driver option in the list.  After downloading and installing the .deb, I removed and re-added the printer.  Test page worked fine as well as a PDF document.

Hope this helps.[/I]


I am also having issues with this model printer, purchased today.  For some reason mine is being detected as an Epson Workforce 315 instead of a Workforce 435.

I don't get any options to install additional drivers, so I presume I have to somehow remove the Epson Workforce 315 driver so that it can attempt download/install of the correct driver?

Running 12.04 LTS 32bit
Mine is not a fresh install - has been upgraded from 10.04 all the way to 12.04 :-p
Will try a fresh install if necessary.

---

