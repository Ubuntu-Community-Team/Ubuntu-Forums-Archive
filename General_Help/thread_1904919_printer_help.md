---
title: "printer help"
date: 2012-01-05
forum: General Help
---

### Post by lamdis on 2012-01-05
have downloaded from lexmark international the driver for the Z2300 series ;
dialog box asking for root admin. password in order to install; 
message of incorrect password  is returned, even though password correct for logging into 
my desktop;
anyone with a fix for problem;  need to use the printer;

thanks

---

### Post by imachavel on 2012-01-05
wow your password doesn't work? incredible. I don't know then :confused:

once the driver is installed, the printer is not guaranteed to work if linux doesn't like the driver. However, I'm assuming you installed the correct driver that probably said 'linux'

ok then, try ctrl+p, open up your printer page. Is there a chance linux already has a generic driver installed for your printer? I would assume it's possible. Let us all know, I'm very surprised your password doesn't work for installs, but works for logging in to linux. 

I don't know if this will work for ubuntu, but try it:

[http://community.linuxmint.com/tutorial/view/339](http://community.linuxmint.com/tutorial/view/339)

but then that might not be necessary. Why don't you try, restart the computer. enter your password. make absolutely certain your password works. IDK bad solution? :confused:

---

### Post by lamdis on 2012-01-06
driver resists being installed ; I guess what I need is a printer compatible with Ubunto 11.10 right out of the box ; is there anything out there; advice greatly appreciated; 
I truly enjoy using Ubunto but a year now without a printer and having to email all my work to another -windows based-machine for printing is a drawback to say the least.

---

### Post by guestolo on 2012-01-06
Try not just double clicking on the file and running it

Put the download in your HOME folder to make it easiest
Open terminal and type in, or copy/paste if that is the actual name of the file

[B]sudo ./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh
[/B]
In terminal, you will input your password at the prompt, then the install should carry on
It installs fine on my Virtual machine

---

### Post by lamdis on 2012-01-07
The command finally installed driver; problem now it keeps looping around "connect usb cable of printer to computer" click ok and then repeats itself w/ no end in sight; therefore, installation instructions cannot be completed and printer in limbo w/ no output; if know fix for this last leg of installation maybe there is a fighting chance...

many thanks anyway for your help;
I got much further than before...

---

### Post by guestolo on 2012-01-07
Just a possibility
After you connect USB cable to printer and computer
Have you powered on the printer?

---

### Post by lamdis on 2012-01-07
Powered it and bought new ink too....Used known working USB computer port; USB printer cable and printer work on windows based machines on my network; so the problem remains. Ubunto and printers are incompatible right off the box; I need to study computer programming at Oxford to figure this one out; and then maybe a Phd on Unix at NYU to work on this OS...

anyway many thanks ..............

---

### Post by lamdis on 2012-01-08
the following messages are being generated on test page printing attempt:

Printer status: printer driver has insecure permissions
Printer driver warning: 'cups-insecure-filter'

any ideas greatly appreciated

---

### Post by guestolo on 2012-01-08
From what I can find, indicates permission problems on a couple folders >>
backend and filter


Why not run the following in terminal and post the output, see if it possibly is  a permission issue

**ls -l /usr/lib/cups**

---

### Post by lamdis on 2012-01-09
The following results to command suggested:



ls -l /usr/lib/cups
total 32
drwxr-xr-x 2 root root 4096 2012-01-08 09:51 backend
drwxr-xr-x 2 root root 4096 2011-12-17 08:39 backend-available
drwxr-xr-x 2 root root 4096 2011-12-17 08:39 cgi-bin
drwxr-xr-x 2 root root 4096 2011-12-17 08:39 daemon
drwxr-xr-x 2 root root 4096 2011-12-17 08:39 driver
drwxr-xr-x 2 root root 4096 2011-12-20 20:37 filter
drwxr-xr-x 2 root root 4096 2011-12-17 08:39 monitor
drwxr-xr-x 2 root root 4096 2011-12-17 08:39 notifier


many thanks to any information....

---

### Post by lamdis on 2012-01-17
Found an old Canon BJC-250 for which Ubunto has driver and printing resumed;
But the Lexmark issue unresolved; many thanis

---

