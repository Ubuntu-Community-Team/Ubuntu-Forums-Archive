---
title: "Epson Artisan 700 scanner"
date: 2009-09-05
forum: General Help
---

### Post by coskierken on 2009-09-05
I researched for past post on getting the Artisan 700 scanner working with Ubuntu.  No luck as of yet!:confused:  Anyone out there have any ideas?  The printer is working great and did not have to do anything.  The memory card slots are not seen either.  If it did see the mem slots, I could scan to it and just read it from there instead of scanning to mem slots, removing it, and putting it in my computer.  Any help would be greatly appreciated.

---

### Post by Liolikas on 2009-09-05
[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Artisan_700](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Artisan_700)

---

### Post by coskierken on 2009-09-05
Ok, got it solved!  Printing was never a problem.  Guten print modules are already built into Ubuntu 9.04. It is vendor/device ID which has to be changed in the epson.conf.  Once your Artisan 700 is plugged in, use lsusb to list the vendor and device id.  The Artisan 700 I have is 0x4b8 0x846.  Once you change this in the conf file, start Xsane and it will show and work great.  I edited down the epson.conf to this:

# epson.conf
#
# This is all you need to configure the EPSON backend
#

# USB scanner:
#  Get your epson artisan ID with cmd: "lsusb" and then change line below
#  it's device ID) is known to the backend. 
usb

# usb <product ID> <device ID>
# e.g.:
usb 0x4b8 0x846
# And for the scanner module, use the following configuration:
usb /dev/usb/scanner0

......................................................

I hope this works for others!  Enjoy!

---

### Post by coskierken on 2009-09-05
For those who want to connect directly to your Artisan series printer (mine is the 700 and picked it up as a return from Sams Club for $50), it is dead easy (using Ubuntu 9.04).  Just turn on the WIFI printer transmitter and then go to system/admin/printing and hit "new" and it should find the printer and the IP address.  Just follow the prompts and your done!  Works great for me!  No drivers needed at all.  I am sure it will work on a cat5 on a router, also.  Hope this helps!

---

### Post by coskierken on 2009-09-05
One more time!  To access the memory card readers on the Artisan series, go to setup on the printer and enable file sharing.  Then go to network on your computer pick the epson (you should see it) and the folder is called "memory card".  Again, dead easy.  So, I managed to have the Artisan 700 working at about 90%.  I tried to check the ink levels, but it won't report it.

---

### Post by blegs38552 on 2010-05-03
OK - now how do I do this for a networked deivce (Artisan 810)?This seems to be for a USB connection. Unfortunately, my device and my laptop are not in proximity to one another which is why I had it set up as a networked evice (note- scans fine in this configuration in Windows 7).

> **coskierken said:**
> Ok, got it solved!  Printing was never a problem.  Guten print modules are already built into Ubuntu 9.04. It is vendor/device ID which has to be changed in the epson.conf.  Once your Artisan 700 is plugged in, use lsusb to list the vendor and device id.  The Artisan 700 I have is 0x4b8 0x846.  Once you change this in the conf file, start Xsane and it will show and work great.  I edited down the epson.conf to this:

# epson.conf
#
# This is all you need to configure the EPSON backend
#

# USB scanner:
#  Get your epson artisan ID with cmd: "lsusb" and then change line below
#  it's device ID) is known to the backend. 
usb

# usb <product ID> <device ID>
# e.g.:
usb 0x4b8 0x846
# And for the scanner module, use the following configuration:
usb /dev/usb/scanner0

......................................................

I hope this works for others!  Enjoy!

---

### Post by GaryUK on 2011-02-24
Dear All

This is how you get network scanning working for your Epson Stylus Photo PX700W / Epson Artisan 700 (hereinafter called a "PX700W"). I actually worked this out last year, forgot to keep a note how I did it, then have had to remember the method as my wife has gone Ubuntu as well now - Doh! should have written it up in this forum but had to go out for a dinner date before I could write it up!!

I have scanning working for both a wired lucid desktop and a lucid wireless laptop. The PX700W is ethernet wired to the router as is the desktop. This post will not consider the printing side as I consider that is covered adequately elsewhere.

You will need to get the SANE components:

```
sudo apt-get install libsane sane-utils xsane xsane-common
```Once you have them you next need to install the iscan and iscan-data components from the Avasys site here:

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do#productinfo](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do#productinfo)

Now, normally, this is all that you can do but the trouble is, you need the "iscan-network-nt" package from the Avasys site as well but Epson will not offer it to you as your PX700W is not supported. Thing is, fortunately, Epson may not support it but that does not mean that it does not work.

What you have to do is fool Avasys into giving you the "iscan-network-nt" package by telling them that you have an Artisan 710/ PX710W all-in-one and then installing the package (and the other two) using GDebi.

Then we need to do a bit of config:

[LIST=1]
[*]Open the epkowa.conf file found in the /etc/sane.d directory and add network details for your PX700W (you must use your router software to assign a internal IP address reservation for the PX700W as availability on the same IP always is a requirement).

```
sudo gedit /etc/sane.d/epkowa.conf
```

[*]Add the following line at the bottom of the file and then save:

```
net 192.168.1.10 1865
```

Where "192.168.1.10" is the IP that you have reserved for the PX700W and that it actually uses. "1865" is the port that Epson uses - I think it will work without the port number expressly put here but better to be safe...


[*]Edit the dll.conf file:

```
sudo gedit /etc/sane.d/dll.conf
```

[*]And comment out the "epson2" entry and save the change - my "E" entries in the file look like this:

```
epjitsu
#epson
#epson2

```

[*]Finally, the PX700W is blocked from working by a blacklist file supplied as part of one of the 3 packages that you downloaded from the Avasys site as above; to unblock it edit the fs-blacklist file:

```
sudo gedit /usr/share/iscan-data/fs-blacklist
```

[*]And comment out the following entry as shown:

```
fs-blacklist NX200
fs-blacklist NX400
fs-blacklist NX300
fs-blacklist WorkForce 600
fs-blacklist Artisan 800
# fs-blacklist Artisan 700
fs-blacklist WorkForce 500
fs-blacklist GT-F720
fs-blacklist GT-S620
```

[/LIST]

You should now be able to network scan with the iscan package that should be accessible from Start Menu => Graphics => Image Scan! for Linux.

Enjoy!!

---

### Post by SqRt7744 on 2011-04-03
> **GaryUK said:**
> Dear All

This is how you get network scanning working for your Epson Stylus Photo PX700W / Epson Artisan 700 

Big Thanks for that  :-)    (Ubuntu 10.10 x64)

**Addendum**: to get the card reader working over the network, 
0. Make sure you have enabled memory card sharing over the network on the printer itself.
1. On your computer (on 11.04 in the File-Manager Nautilus -> File Connect to Server, otherwise click Places -> Connect to Server...)
2. In the Dialog that appears, select "Windows Share" as the Service Type,
 2.1. for the Server, enter the IP Address of the Printer (or better the network name with a ".local" extension, e.g. EPSON3BA375.local )
 2.2. the share is called MEMORYCARD
 2.3. enter something for the username (doesn't matter)
 2.4. You will probably want to add a bookmark, e.g. Epson Card Reader

When it asks for a password, type anything and select "remember forever", The Printer ignores authentication anyway, but you don't want to be prompted every time for a non existent password.

---

### Post by maitrebart on 2011-04-21
> **coskierken said:**
> One more time!  To access the memory card readers on the Artisan series, go to setup on the printer and enable file sharing.  Then go to network on your computer pick the epson (you should see it) and the folder is called "memory card".  Again, dead easy.  So, I managed to have the Artisan 700 working at about 90%.  I tried to check the ink levels, but it won't report it.

On my side, I couldn't find any item related to "file sharing" in Ubuntu's printer options (for Artisan 710). Also my printer was not showing up while browsing the "Network" in Nautilus.

However, Googling around, I found this:
[LIST]
[*]in Gnome's file manager (Nautilus),
[*]in "Location..." (from the Go menu),
[*]specifying smb://192.168.0.107 (which is the IP of my printer)
[*]you have to enter your credentials to access the Windows Share network
[/LIST]
then it will automatically mount the file system named MEMORYCARD and will open the root directory.

From there you may browse the memory card.

---

