---
title: "NetGear WNDA3100(v2) USB?"
date: 2012-09-19
forum: General Help
---

### Post by Cam! on 2012-09-19
I had to get a USB WiFi adapter due to a new router, and it won't work on my 64-bit 12.04 installation.

I know that I have to get the drivers from within Windows and do something with "ndiswrappers", but I'm not sure the exact method. I tried doing it on Linux Mint to no avail.

---

### Post by AndyOpie150 on 2012-09-19
You first need to download all these packages by typing them in the browser and putting precise after. Example: If I want to find the libglade2-0_2.6.4-1ubuntu1_i386.deb all I need to type in the browser is libglade2 precise. Then go to the link that says "Ubuntu -- Details of libglade2 in precise. If A link also includes "-Updates" on the end then use that one.

You will need to download all of these packages and put them in your home folder and install them in the order I put them in:

ndiswrapper-common_1.57-1ubuntu1_all.deb
ndiswrapper-utils-1.9_1.57-1ubuntu1_i386.deb
libglade2-0_2.6.4-1ubuntu1_i386.deb
python-glade2_2.24.0-3_i386.deb
ndisgtk_0.8.5-1_i386.deb
dkms_2.2.0.3-1ubuntu3_all.deb
ndiswrapper-dkms_1.57-1ubuntu1_all.deb

To install open a terminal and type in: 
sudo dpkg -i (complete name of package)


Put the driver folder in your Home folder and rename it: Drivers
To install the driver type in this:
sudo ndiswrapper -i Drivers/(full name of driver or driver.INF file)
sudo modprob ndiswrapper
sudo su 
echo ndiswrapper >> /etc/modules
exit

You can only put your security on your router to as high as the Network-Manager recognizes. 
I struggled with this trying every thing I could to get the Network-Manager to recognize the level of security my card was capable of. No go 
I ended up having to set it at the level the Network-Manager recognized.

After I did this I connected right up.

Note: Once installed you can delete the first 7 packages in the home folder.


If you have any more Questions you might need to go to the experts at the Networking and Wireless sub-forum.

---

### Post by Cam! on 2012-09-20
Thanks. I'll try those out and see if they work. I know when I try doing it with only three wrappers (From a diff. guide), the third one has an error come up.

To add, I can't open up Windows Wireless Drivers at all.

---

### Post by AndyOpie150 on 2012-09-21
Install all the packages listed, then I think you might need to have this thread moved to the Networking and Wireless sub-forum and let the experts have a look at the driver (I might not know which part of that driver needs to be installed with ndiswrapper). I'm going to download the driver for your card and see what's up.

EDIT: Could you post the exact full name of the driver (with software version). There seems to be a few WNDA3100v2 software versions. 

Are you dual booted?

---

### Post by kurt18947 on 2012-09-21
Any chance you could return the WNDA3100 and instead purchase a wifi adapter known to work in Ubuntu/Linux without having to fight with NDISwrapper?

---

### Post by AndyOpie150 on 2012-09-21
Actually, ndiswrapper is pretty easy once all the dependency's I mentioned are installed. 
My driver had an .INF folder that I had to install using ndiswrapper. The newer drivers don't, so I don't really know what needs to be installed with the ndiswrapper, but it's should be just as easy as mine was. 
The experts at the Networking and Wireless sub-forum will know what needs to be installed.

---

### Post by kurt18947 on 2012-09-21
> **AndyOpie150 said:**
> Actually, ndiswrapper is pretty easy once all the dependency's I mentioned are installed. 
My driver had an .INF folder that I had to install using ndiswrapper. The newer drivers don't, so I don't really know what needs to be installed with the ndiswrapper, but it's should be just as easy as mine was. 
The experts at the Networking and Wireless sub-forum will know what needs to be installed.

That's one of the tricks.  It seems the majority of Windows driver installers today come as an .exe file.  The only way I know (and I am by no stretch of the imagination  an expert) is to install in Windows, find the correct .inf, .sys, whatever files, copy them to portable media then copy them from the media to the Linux install.  They have to be Windows XP afaik and if the Linux install is 64 bit the windows XP drivers need to be 64 bit.  If there are separate drivers for XP and Vista/Win 7, one would need the XP drivers afaik,  NDISwrapper didn't work with Vista/Win7 specific drivers.   I imagine there's a way to extract files from a self extracting .exe file but doesn't seem like a common operation.    Use WINE somehow? If NDIS wrapper is the only game in town  as it is for some devices then carry on.  If I'm buying new hardware, why not buy something simple?  Life is complicated enough :).  I haven't had to use NDISwrapper for some time so my knowledge and experiences may be outdated, dunno.

---

### Post by AndyOpie150 on 2012-09-21
You make a very good case. 
The OP should now have enough info to make a pretty good decision, based on all the info presented.
I tried Wine on my Video Camera drivers. No go.

---

### Post by Cam! on 2012-09-22
If it matters, here's the software/driver version:

**NetGear WNDA3100 v2 (2.0.0.1)**

Where can I install the previously-mentioned "dkms_2.2.0.3_1ubuntu3_all.deb" package? I can't find that one.

---

### Post by Joseph Rinaldi on 2012-10-24
Hi,
I spent hours on this but found a simply way to get this working flawlessly.
1. From the Ubuntu Software Centre, install Windows Wireless Drivers (NDISWrapper) and the two add-ons, [FONT=Calibri]ndiswrapper-dkms and ndiswrapper-source.[/FONT]
[FONT=Calibri]2. I installed the latest drivers from Netgear on a Windows XP computer. (Just a VM will do, can be on a Linux Box).[/FONT]
[FONT=Calibri]3. This creates a folder in C:\Program Files\NETGEAR\WNDA3100v2\Driver, called WinXP2000. This contains the latest drivers for this adapter. The .sys file should be version 5.100.68.46.[/FONT]
[FONT=Calibri]4. Copy the folder to your Ubuntu (or Xubuntu) computer.[/FONT]
[FONT=Calibri]5. Run the Windows Wireless Drivers software and point to the inf file in this folder.[/FONT]
[FONT=Calibri]6. Reboot. All done![/FONT]

---

