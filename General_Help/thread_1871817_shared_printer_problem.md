---
title: "shared printer problem"
date: 2011-10-29
forum: General Help
---

### Post by watgrad on 2011-10-29
Hello,
I have a desktop and laptop computer both running ubuntu 11.10.
The desktop has a HP F4100 printer connected via USB.  I have shared this printer and selected "Publish shared printers connected to the system" in the printers network menu.

On the laptop I've selected "show printers shared by other system".  The shared F4100 printer shows up on the laptop's printer list.  However, when I select the printer for printing, or to view it's properties the printing system hangs...like it is stuck trying to communicate with the printer...

I'm not sure how to fix this, even when I run the "Problems?" troubleshooter in Ubuntu the system hangs....

Anyone have any ideas about how to fix this?

---

### Post by watgrad on 2011-11-01
anyone?

---

### Post by serpentracer on 2011-11-01
I don't know,  but my HP printer works perfectly on my network.  I've never tried to hook it up via the usb and share it that way.

have you tried installing the HP drivers/toolbox for linux?  it's like the windows version of what comes with the printer...and it's made by HP.
in the software center it's called HPLIP toolbox.
it might help you resolve the issue by correcting the path to the printer etc.

---

### Post by pqwoerituytrueiwoq on 2011-11-01
is this a linux to linux share?
if so both devices need the driver
if you are running a firewall be sure port 443 (iirc) is open

---

### Post by watgrad on 2011-11-02
> **pqwoerituytrueiwoq said:**
> is this a linux to linux share?
if so both devices need the driver

if you are running a firewall be sure port 443 (iirc) is open


Thanks for your suggestion - I do have the driver installed - but I didn't think to check the port - I will make sure the port is open in the firewall.

Thanks again,

---

### Post by doctorprunesquallor on 2011-11-02
I have the same problem.

The desktop PC has 11.10 as does the netbook. The printer and server is enabled for sharing. The printer shows up on the netbook but when trying to print a test page the printer state is "Processing - the printer is not responding"

---

### Post by malcmail on 2011-11-02
Can either of you reach the CUPS interface on the machine that hosts the printer?

---

### Post by SparTacux on 2011-11-02
I'm not that familiar with this type of printer but i do use an HP printer as a shared printer using USB. Mine works on port 631 which is IPP. On the client side you have to find the printer using find network printer or specify the location of the server IP directly and also tell it what port you are using. If using static IP this is relatively easy since the IP of the server will always be the same. I've never done it on a system using DHCP. I'd set up the print server with a static IP.

Your printer may work differently. but this may give you some sort of idea what may be wrong.

My system uses port 631 ( IPP ) and any firewall on the server must allow traffic on port 631 out and In. The server broadcasts traffic every couple of seconds or so if you selected publish printers. If you don't it won't work. The clients also need to allow traffic both in and out on port 631 mainly to pick up the broadcast traffic and also send data directly to the print server. 

You may be able to see what is going on by typing netstat -ntuc

This will observe your traffic when you hit the PRINT button and see what ports you are using. You may be a able to spot problems here. If you need a more detailed analysis try using GUFW and allow HIGH log levels and check your UFW logs to get a detailed inspection of your network traffic.

When setting up a client to connect to the print server using the find network printer command you will see ( in the UFW logs ) that the process causes quite a few different ports to be tested to locate your printer. If you have a firewall ( on the print server ) blocking incoming connections then it  won't be able to find your printer.   

Hope this helps

Oh and don't forget a ping test to your computer connected to the printer. You may have some sort of network problem.

---

### Post by watgrad on 2011-11-02
Thanks for your help - it was the firewall blocking the printers ports.  Opening 631 did the trick.

---

### Post by serpentracer on 2011-11-02
that's a lot of crap. lol
thank god for network (via ethernet) printing.  basically plugged mine in to the router, turned it on, and all the computers can see it.

---

### Post by watgrad on 2011-11-02
Yes - I think I'll get a new wireless router with the USB port that lets you share a normal printer as if it were wireless.  Apparently you can use them to share hard drives wirelessly as well...would make sharing files and the printer much less of a headache...

---

### Post by SparTacux on 2011-11-03
> **serpentracer said:**
> that's a lot of crap. lol
thank god for network (via ethernet) printing.  basically plugged mine in to the router, turned it on, and all the computers can see it.

I guess that was a little too technical for you. Never mind we all started as newbies :-)

You'd never get the printer working with a Firewall blocking incoming connections even if using HPTOOLBOX. GUFW has the option to deny all incoming traffic and if you select it then you are going to run into trouble printing - it's as simple as that.

---

### Post by doctorprunesquallor on 2011-11-04
Using the command "sudo ufw allow 631" to make sure the port was open on both machines didn't help. I can ping the printer server from the netbook. Also I can log in to CUPS on both machines OK. However the netbook still responds: Processing - "The printer is not responding".

Appreciate any assistance!

---

