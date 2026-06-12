---
title: "Sharing a printer with Windows?"
date: 2011-04-10
forum: General Help
---

### Post by aquascrotum on 2011-04-10
Hi all.

I've gone and bought a printer (Epson Stylus SX415) - I've made sure that it can be made to work fully with Ubuntu.

My home network has 3 Win 7 PC's and my Ubuntu PC.  I want to set the printer up so that it's available as a shared printer to all PC's.

Am I better installing it on one of the Windows machines, in which case can I share it from there to my Ubuntu?  Or if I install it primarily on Ubuntu, will the Windows machines be able to access it via Samba or something similar?

Any advice would be appreciated at this stage, before I start connecting stuff up!

---

### Post by gerowen on 2011-04-10
Ubuntu shares printers over http, and since it's being shared between different operating systems, you'll have to make sure you have "Windows" drivers available.  The easiest method is this, and I'll include screenshots from my setup.

1) On your Ubuntu server, make sure the printer is marked as "Shared", and that you have the server settings configured properly.  Just click the "Server" menu, then click the "Settings" option.
[**Screenshot 1**](http://adams-family.homeip.net/images/shared/server.png)
[**Screenshot 2**](http://adams-family.homeip.net/images/shared/shared-print.png)

2) Browse to your print server from a remote machine with the web browser by going to [http://foo:631](http://foo:631) where "foo" is the hostname or IP of the Ubuntu server.
[**Screenshot**](http://adams-family.homeip.net/images/shared/cups.png)

3) Click the "Printers" tab, right click the printer you want to connect to and copy the link location.
[**Screenshot**](http://adams-family.homeip.net/images/shared/printers.png)

4) Add a printer as you normally would, and when asked click "Add a Network, Wireless, or Bluetooth Printer".
[**Screenshot**](http://adams-family.homeip.net/images/shared/network.png)

5) The printer "might" show up in this next screen automatically, if it does just select it and continue on, you may have to install the Windows drivers at this point.  If it does not, just click "The printer that I want isn't listed".

6) In the next screen, if it's not already selected, click the second bubble that reads, "Select a Shared Printer by name".  In this dialog box, paste the URL that you previously copied from your Ubuntu CUPS server.
[**Screenshot**](http://adams-family.homeip.net/images/shared/url.png)

From here on out it should be like adding any other printer, drivers, naming it, etc.  If you have any problems let me know and I'll help the best I can.

Edit: Also note that you can administer your print server via this web interface if you want.  Just browse to http**s**://foo:631 and when you attempt to do something administrative, just enter the username/password of a user account with sudo rights.

---

### Post by rvchari on 2011-04-10
> **aquascrotum said:**
> Hi all.

I've gone and bought a printer (Epson Stylus SX415) - I've made sure that it can be made to work fully with Ubuntu.

My home network has 3 Win 7 PC's and my Ubuntu PC.  I want to set the printer up so that it's available as a shared printer to all PC's.

Am I better installing it on one of the Windows machines, in which case can I share it from there to my Ubuntu?  Or if I install it primarily on Ubuntu, will the Windows machines be able to access it via Samba or something similar?

Any advice would be appreciated at this stage, before I start connecting stuff up!

its perfectly possible. i am using my ubuntu laptop in office which is running windows and i am able to connect the printer thru the windows machine with ease.

u ll need samba to be installed.
if its there then fine else install samba from synaptic or ubuntu software center.

then go to printer configuration in ur ubuntu machine.
go to System > Administation > Printing.

add printer. select network printer and give the ip address of the machine that has the printer coupled. (i presume u have made that printer thats installed in windows machine as shared)
u should see the printer listed. select it and configure as default printer.

---

### Post by gerowen on 2011-04-10
My server is going down for some maintenance and cleaning, so I've archived all of the screenshots linked earlier and attached them to this post.

---

