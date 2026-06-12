---
title: "Printer Sharing"
date: 2011-03-20
forum: General Help
---

### Post by bba1973 on 2011-03-20
This has happened to me ever since I first started messing with Ubuntu. I've got a printer hooked up to a Windows computer, and I can't access it with Ubuntu. Every time I've tried to get it to work, it never would, so I gave up on it. This time, I really want to get my issue resolved. Sharing the printer with other Windows computers (XP, Vista, and 7) works flawlessly.

The computer hosting the printer is a Windows 7 box with AVG Internet Security. The printer is a Brother MFC-8220. My wireless router is a Belkin. The laptop I'm using is an Asus EEE PC with Ubuntu 10.10 netbook edition (using the desktop interface rather than the netbook interface; this issue happened with my experiments with Ubuntu as far back as 8.04).

I didn't see anything in AVG or on the router that looked like it would block my netbook. I'm certainly not ruling that out though. When I try to add it, it can see the Windows 7 PC, but it can't connect. Trying to add the printer with SAMBA, and I've got CUPS and SAMBA installed on the netbook. Tried to add it by entering the name and location of the printer, but it still can't connect.

Any ideas? All help is appreciated.

Thanks

---

### Post by gordintoronto on 2011-03-20
Did you share the printer in Windows? If so, you should be able to run Administration/Printing, select Add, network printer, and wait a few seconds for the printer to appear. Select it, and it should be obvious from there.

---

### Post by bba1973 on 2011-03-21
> **gordintoronto said:**
> Did you share the printer in Windows? If so, you should be able to run Administration/Printing, select Add, network printer, and wait a few seconds for the printer to appear. Select it, and it should be obvious from there.

Yes, I've shared the printer in Windows. It's been shared in Windows for years now, and it works flawlessly when sharing with other Windows machines. 

And yes, I've tried to add the printer with the steps you told me, but it just doesn't work for some reason. I got a "printer share is inaccessible, network connection timed out," or something to that effect, error. On the Windows host, the printer shows up in the WORKGROUP network share. On my Ubuntu netbook, I can see the workgroup and the host, but not the shared printer or any shared files. I went through the steps you told me (several times before this too, mind you), and when I click on the workgroup and wait for it to drop down and show the shared printer, it takes about 2 minutes or so and just sits there.

What's causing this connection to time out and how can I fix it so I can print? It makes no sense to me why this is happening. Turning off the AVG firewall on the Windows host didn't help at all either.

---

### Post by plucky on 2011-03-21
I have had a look on the Brother site for your printer and it doesn't have a driver to install,but uses a PPD file.

Have you installed a PPD file for your printer?

The PPD file can be found [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-8220)

and the installation instructions can be found [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1c.html) including ones for a networked printer.

I have never tried a PPD install, and as I don't have your model of printer,I am unable to test this installation.

Good Luck

---

### Post by Topsiho on 2011-03-21
I have an HP All-in-One printer, which I have shared from the computer to which it is directly connected. As your printer is shared already you need not do this sharing, but I describe it for other readers:
As my language is Dutch, I have to retranslate the menu items, so these might differ a little bit from what you'll find on your systems:

Select System>Administration>Printing>Server>Configure>Publish shared printers connected to this system.

On the other systems that are to use this printer/these printers too, you do exactly the same, except the last step, which is: Show printers shared by other system.

Then you have to wait a little while untill the network has noticed these settings and acts on this.

Topsiho

---

### Post by Morbius1 on 2011-03-21
> **Topsiho said:**
> Select System>Administration>Printing>Server>Configure>Publish shared printers connected to this system.

On the other systems that are to use this printer/these printers too, you do exactly the same, except the last step, which is: [COLOR=Blue]Show printers shared by other system[/COLOR].

Then you have to wait a little while untill the network has noticed these settings and acts on this.

Topsiho
I would highly recommend the process described above for difficult networked printers. From the client user's perspective it's nothing short of magic.

The only other thing I can recommend is that you make sure the following packages are installed on the client:
```
sudo apt-get install libsmbclient
sudo apt-get install smbclient
sudo apt-get install python-smbc

```If that fails then instead of browsing to the Windows' printer you give it's exact location:
System>Administration>Printing > Add > Network Printer > Windows Printer via Samba >

Do not click on browse, just give the exact location in one of these formats:
```
smb://WORKGROUP_NAME/MACHINE_NAME/WinPrinterName
smb://MACHINE_NAME/WinPrinterName
smb://192.168.0.100/WinPrinterName
```

---

### Post by Topsiho on 2011-03-21
Thanks Morbius1,

I quite forgot it is a Windows computer doing the sharing. Which means you have to do the Samba :)

Topsiho

---

### Post by bba1973 on 2011-03-21
It finally worked! Thank you very much to everyone for all your help. I really appreciate it.

I added it with the smb://ip_address/printername but I did NOT click browse, and I clicked on "verify." I could swear I tried that last night, but guess I didn't do it right.

The page took a bit (the printer was probably trying to warm up), but it printed out an Ubuntu test page. I was so happy to see it.

Thanks so much again. Problem solved!

---

