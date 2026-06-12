---
title: "Networking two Ubuntu Computers together with one printer"
date: 2006-06-12
forum: General Help
---

### Post by konacoffeeguy on 2006-06-12
Hey, 
   I can't seem to figure out how to network my two computers together. I have two computers that are connnected threw a router that both have Ubuntu LInux on them. I want to network them together so we can share files. I also want them both to be able to use the same printer. I have no real experience ever networking computers together so am a noob a this kind of a thing. I'm sure it's pretty easy but can't seem to figure it out. How can I do this?? Thanks a bunch 

 Konacoffeeguy

---

### Post by soze on 2006-06-13
Try Samba: 
[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

---

### Post by Athanasius on 2006-06-13
I have been surfing the forums for three months for an answer to your question because it is also my question.  

What I have found so far is that the way CUPS (the printing program that Ubuntu uses) is flawed in that way, you can use Samba to share printers with Windows and Mac but apparently we are one of the few human beings who want to share a printer with another Linux box... go figure.  I have found no easy answer (there should be... at least you'd think so).

---

### Post by biguns on 2006-06-13
What kind of printer do you have? If it is the kind of printer that has a network connection (RJ-45) and can be assigned an IP address than you can configure it that way and plug it directly into your router.

If you have a usb or parrellel port printer there are devices that faciliate the same thing. IMHO this is the easist way to do it and the easiet way to administer. Anyway, its how I do it.

---

### Post by soze on 2006-06-13
[QUOTE=Athanasius]I have been surfing the forums for three months for an answer to your question because it is also my question.  

What I have found so far is that the way CUPS (the printing program that Ubuntu uses) is flawed in that way, you can use Samba to share printers with Windows and Mac but apparently we are one of the few human beings who want to share a printer with another Linux box... go figure.  I have found no easy answer (there should be... at least you'd think so).[/QUOTE]

I share a printer on my Ubuntu box with both another Unbuntu box and two Window's boxes.

Furthermore, all three of these machines also share files on my Ubuntu box.

---

### Post by mattmole on 2006-06-14
Hi,
This is the first reply Ive given trying to advise, so please excuse me if this is of no use, and if it is wrong then someone please correct me!

OK, you have two Ubuntu machines? The printer is plugged into one of them via USB/parallel? Assuming this is the case and if you go to [http://localhost:631](http://localhost:631) on your machine with the printer installed and you can see the printer I suggest the following:

On the machine without the printer physically connected
In /etc/cups/cupsd.conf add the lines
#BrowsePoll address: port
BrowsePoll <SERVER NAME/ADDRESS>:<PORT, usually 631>

Then in /etc/cups/cups.d/browse.conf:

Make sure it says "Browsing on"

Finally, restart cups

sudo /etc/init.d/cupsys restart


THis is what I have done on my laptop, now when I plug into the network at work I can see the approx 20 printers our print server manages. This saves me MUCH effort as before I was emailing the files to my office PC and printing from there.

Hope this is a help, please let me know!

Matt

---

### Post by givré on 2006-06-16
[https://wiki.ubuntu.com/NetworkPrintingWithUbuntu](https://wiki.ubuntu.com/NetworkPrintingWithUbuntu) to know more ;)

---

### Post by shilliard on 2006-06-26
Hi
 
I just use samba to access the remote printer.  I'm using 1 Dapper PC with printer attached (Canon i950) and a Dapper Laptop.
 
1. Get the printer working on the PC it is connected to (the print server).  I use the TurboPrint drivers as it is the only driver that works properly with my Canon printer.
2. Install samba on the print server.  Test using:
 
$ smbclient -L servername_or_ip
 
You should see the printer listed as one of the shares.  If not you will need to adjust the samba configuration /etc/samba/smb.conf.  Mine worked out of the box.
 
3. If you haven't done so already, add a samba password:
 
$ sudo smbpasswd -a yourusername
 
4. Install the drivers on the remote computer the same way.
5. Go to System->Administration->Printing on the remote computer.  Right click the printer and bring up properties.
6. Go to the connection tab.  Set the location to be smb://servername_or_ip/printer_share_name.  In my case it was smb://servername/Canon_i950.
7. Enter username and password to access the share.  Click Print Testpage.
 
I didn't have to enable "Detect LAN printers" or adjust the cups configuration in any way, it just works out of the box through samba.  
Trickiest bit was entering the username and password to access the samba share, without this it fails.  Think you can fix this by adjusting the /etc/samba/smb.conf file and changing the [printer] section option "public no" to "public yes"

---

