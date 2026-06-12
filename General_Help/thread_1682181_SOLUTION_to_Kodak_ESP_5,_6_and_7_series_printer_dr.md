---
title: "SOLUTION to Kodak ESP 5, 6 and 7 series printer driver"
date: 2011-02-05
forum: General Help
---

### Post by Spyderkid on 2011-02-05
[COLOR="Blue"]To make most Kodak esp 5000 upwards printers work you should install this with Firefox....

[SIZE="4"][Kodak Driver]("http://sourceforge.net/projects/cupsdriverkodak/files/c2esp_15-1_i386.deb/download")[/SIZE]

then click open with software centre, then click install.[/COLOR]

[COLOR="Orange"]then...[/COLOR]
[COLOR="SeaGreen"]once you have downloaded it and clicked install on the software centre,


go to system > Administration > Printing

then click "ADD"
then if its wireless click on the >Network tab and wait for it to appear and then click on it and folow instructions. If not it should automaticly appear above the network printer tab.[/COLOR]


[SIZE="3"][COLOR="Red"]DONE![/COLOR][/SIZE]




[COLOR="Red"]Note:
this will not activate the printers scanner.[/COLOR]

---

### Post by Spyderkid on 2011-02-08
If anyone has any problems or it doesn't work for them then please comment!

---

### Post by COMPUTIAC on 2011-02-10
I just tried this and still no go.  What do you mean by, then just install the printer as usual  ?
 
I do not have the install disk.

COMPUTIAC

---

### Post by Spyderkid on 2011-02-11
once you have downloaded it and click install on the software centre,


go to system > Administration > Printing

then click "ADD"
then if its wireless click on the >Network tab and wait for it to appear and then click on it and folow instructions. If not it should automaticly appear above the network printer tab.

---

### Post by COMPUTIAC on 2011-02-12
Thank's alot, Now all is working just fine.  I would like to find a way to print in black only.

COMPUTIAC

---

### Post by Spyderkid on 2011-02-12
Just go to System > Administration > Printing

Right click on the printer that's installed and go to properties.
Go to printer options on the left hand side and where it says colour choose Black And White.

---

### Post by COMPUTIAC on 2011-02-12
It did not say black and white;  so I went with grayscale.

COMPUTIAC

For some reason this machine will not print anything from the computer. I can do test pages from within the printer, but nothing else.

---

### Post by Spyderkid on 2011-02-13
did it work with colour? If it did then you might want to stick with it

but replacing all the ink on a kodak is only £20 and you dont have to do it often

---

### Post by COMPUTIAC on 2011-02-13
No it did not work with color, I am thinking I need to replace the ink first because when I tried to print out a test from with-in the printer it gradually faded.                       Then I will go back to pulling my hair out!

Will post back with results.

---

### Post by satanselbow on 2011-03-30
This worked for me on Linux Mint (x64) - the i386 deb available at [http://cupsdriverkodak.sourceforge.net](http://cupsdriverkodak.sourceforge.net) would not work for me using the --force-architecture flag :( It would install but repeatedly failed to print...

I wasn't brave enough to compile a i686 myself but found these instructions buried in the readme of the latest tarball :)

Add repo:

ppa:jolting/cupsdriverkodak

sudo apt-get update
sudo apt-get install c2esp

Add printer through Administration -> Printing ;)

---

### Post by Kevinc1 on 2011-04-30
Any way to get the scanner to work?

---

### Post by Spyderkid on 2011-04-30
not at this moment in time, sorry.

---

### Post by Trent T on 2012-01-22
It worked well for me!  Thanks Spyderkid!!

I installed the driver as directed above, then went to 
System > Administration > Printing to select the new driver;
The ESP 5500 driver works well with my ESP 7200 wireless printer--

What is the difference between the plain driver and the dithered driver?

Thanks in advance for any info!

---

### Post by paulnewall on 2012-01-23
The dithering process should give you smoother colour transitions. You'd only notice the difference when printing photos.

---

