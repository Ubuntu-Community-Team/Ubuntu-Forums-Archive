---
title: "How do I set up windows 7 laptop to print to ubuntu local printer"
date: 2011-09-08
forum: General Help
---

### Post by Doublestop on 2011-09-08
i have recently moved to ubuntu 11.04 from windows, so am slowly learning.

i have installed Canon MP510 printer as local printer on ubuntu and all works fine from ubuntu.

i would like to be able to print to it from several windows 7 laptops.

in printer properties the printer is marked as enabled, accepting jobs and shared.

i have tried 'add new network printer' on the w7 laptops but they cant find the printer.

can anyone point me to instructions to set up w7 to print to ubuntu local printer?

i have search internet and ubuntu forums but havent found the idiot-proof instructions i am looking for!

many thanks

---

### Post by evilsoup on 2011-09-08
Are you are trying to connect to the printer directly (so, not through a Ubuntu computer)? If that is the case, you probably don't have the driver installed under windows. There should be a CD in the packaging that your printer came in, failing that check Canon's website.

---

### Post by couling on 2011-09-08
I've been doing this myself recently.

There is a known bug with the current version of ubuntu where smba (windows file and printer shareing) starts before cups (printer server).
[https://lists.ubuntu.com/archives/foundations-bugs/2011-May/000011.html](https://lists.ubuntu.com/archives/foundations-bugs/2011-May/000011.html)

First off try looking at your linux box file and print sharing from a windows machine:
(try to navigate to the following location or click start -> run.  You will need to know the ipaddress or hostname of the linux box:

\\ipaddress\

eg:
```
\\192.168.0.37\
```You'll probobally see no printer there, so ....

On the linux box restart the smba server:
Type the command:

```
sudo service smbd restart
```Then try navigating to the server from the windows box a second time and see if the printer is there.  

**If it is then you can make a configuration fix:**
The file: /etc/init/smbd.conf
Find the line near the start that says:
```
start on (* blah* and *blah* )
```And change the line to be:
```
start on (* blah* and *blah* **and started cups** )
```That should mean that things start in the correct order.

---

### Post by couling on 2011-09-08
Sorry I should have offered an "idiot proof" instructions...

Assuming everything is working well (see above) the printers should be shared by smba.
SMBA is basically windows file and print sharing for linux (it does other stuff as well but i'm giving the simple version).

The easy way to add the printer on a windows 7 box is

[LIST]
[*]Install the driver on the windows 7 machine (there's a way to get that working automatically but it's not "idiot proof").
[*]Navigate to the machine using the linux machine name or ip address:
Either start -> run and type \\*name-or-ip\ *or click start -> computer and then in the location bar at the top of the window type \\*name-or-ip\*
[*]This should show you everything shared by that computer including the printer.
[*]Double click on the printer ... it will complain about not being able to get the driver ... just click cancel and choose the driver manually.
[*]Once you've selected the driver it should finish installing the printer and you can print a test page to cehck it.
[/LIST]

I've mentioned that you can use either the IP address or the computer name (hostname).  It's generally better to go with names as IPs can change (unless you've gone through the trouble of stopping that happening).

---

### Post by Wim Sturkenboom on 2011-09-08
[http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html](http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html) helped me; just went through it again for a WinXP laptop

[LIST]
[*]add printer
[*]after some clicks somewhere, you will encounter an option to connect to a printer on the internet
[*]enter _*[noparse]http://ipaddress:631/printers/printername[/noparse]*_
[*]click next and you should get a popup where you can select manufacturer and printer; choose *_generic_* for manufacturer and *_ms publisher imagesetter_* as the printer
[*]click OK
[/LIST]
That should be it; I did the exercise a while ago for Win7 as well and it's very similar; I could basically translate/apply the earlier link without problems.

One thing is to make sure that the firewall on your linux box allows traffic on port 631.

PS
my printer in above scenario is [noparse]http://192.168.2.222:631/printers/HP-LaserJet-P1005[/noparse]

PPS
you don't need samba and you don't need additional printer drivers under windows

PPPS
I use a static IP for the linux machine that has the printer connected

---

