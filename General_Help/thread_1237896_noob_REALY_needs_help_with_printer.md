---
title: "noob REALY needs help with printer"
date: 2009-08-11
forum: General Help
---

### Post by umdoobby on 2009-08-11
i have a new epson nx415 printer and it just refuses to work 

in my printer config the status is always stopped when i set the driver as a downloaded ppd for the nx415 but the driver on the install disk says its for the nx410 i dont get it the bottem line is that i need help so plz anyone help

---

### Post by michy99 on 2009-08-11
The driver on the disk is probably a Windows driver. If so, it won't work in Linux. It should install with the built-in drivers.

---

### Post by umdoobby on 2009-08-11
yes but not even the generic text driver works but then the status in idle

---

### Post by RedRat on 2009-08-11
Have you tried to install the CUPS system? It is in Synaptic. I use it with my Canon i860 and it works fine.

---

### Post by umdoobby on 2009-08-11
no ill try that now

---

### Post by umdoobby on 2009-08-11
unless i did something wrong nothing changed

---

### Post by RedRat on 2009-08-11
> **umdoobby said:**
> unless i did something wrong nothing changed

Go to System>Administration>Printing<--click on Printing

You should get a pop up window
You will see "Settings" and several places to fill stuff in. 
1. Description type in Epson whatever your printer is
2.Location: Put in the name of your computer, e.g., "Dell-Ubuntu"
3. Device URI: type in the location if it is shared on another machine, e.g., "smb://MSHOME/IBM-1/Epson_nx415

below that you will see "Make and Model" click on "Change" and then follow along by clicking "Forward". CUPS will try to find a suitable driver.  For example, my is "Canon i860-CUPS+Gutenprint v5.0 Simplified", yours will be different.

That should do it. Try printing a test page.

---

### Post by umdoobby on 2009-08-11
the list dosnt have my modle so i downloaded a ppd but it does not seen to work

---

### Post by michy99 on 2009-08-11
Try using the closest model to yours. The file you downloaded will only work if it was made for linux.

---

### Post by RedRat on 2009-08-11
> **umdoobby said:**
> the list dosnt have my modle so i downloaded a ppd but it does not seen to work

You might want to chose a model that is close to yours. Usually, printer companies keep the basic print engine for a whole series and merely change some externals. Try to go to the Epson site and see what models closely resembles yours. Then go back and recheck the list. 

Just to point out the obvious, before you buy a printer make sure that it has Linux/Ubuntu support. Certain manufacturers are better than other, e.g., HP. Also, your model may be too new and nothing is in the repositories for it. Try searching Google for "Epson nx415 ubuntu", someone, somewhere might have tried this and succeeded.

---

### Post by umdoobby on 2009-08-11
they do have linux support apparently but im yet to be able to contact them or even see their web page for that matter 

im going to try to find a better driver 

also when i select the ppd option it gives me 2 options: use new ppd or copy settings from old ppd , which should i choose

---

### Post by Whiffle on 2009-08-11
Where did you put the ppd?  There should be a point during the printer install where you can give it a ppd to use with your printer.  Or, I think you can put it in /etc/cups/ppd and it will find it and add it to the regular list of printers.

---

### Post by umdoobby on 2009-08-11
when i try to move the ppd in to the folder an error pops up and says that my permission is denied

---

### Post by RedRat on 2009-08-12
> **umdoobby said:**
> when i try to move the ppd in to the folder an error pops up and says that my permission is denied

You must run your file manager as root to do this. In the case of Nautilus, open a terminal window and enter either: 
sudo nautilus

or 

gksudo nautilus

either will work. You now have root privileges and should be able to move the file into that directory.

---

### Post by umdoobby on 2009-08-12
it allowed me to move it but it didnt show up in the list of drivers

---

### Post by RedRat on 2009-08-12
> **umdoobby said:**
> it allowed me to move it but it didnt show up in the list of drivers

I have not installed a ppd driver so I can't offer much help there. When you were running the Printing Services CUPS popup, did you see any Epson printer that was close to yours? Perhaps a slightly different model number. Try one of those CUPS drivers.

Go to Synaptic and press the reload button in the upper left corner. After it loads, click on "All" in the left panel. Then do a search for "Gutenprint", there should be an entry for "cupsys-driver-gutenprint" package. Click on that to install it. this might help under the Printer Services popup.

---

### Post by umdoobby on 2009-08-12
i did the search and nothing was there and the model isnt even close to any of the other models in the driver list

---

### Post by RedRat on 2009-08-12
> **umdoobby said:**
> i did the search and nothing was there and the model isnt even close to any of the other models in the driver list

did you install the gutenprint drivers from synaptic. They are there.

---

### Post by umdoobby on 2009-08-13
thats just it i search for gutenprint and there was nothing there

---

### Post by ronaldprettyman on 2009-08-13
> **umdoobby said:**
> they do have linux support apparently but im yet to be able to contact them or even see their web page for that matter 

im going to try to find a better driver 

also when i select the ppd option it gives me 2 options: use new ppd or copy settings from old ppd , which should i choose

Future reference. HP printers have the best linux support. HPLIP

---

### Post by umdoobby on 2009-08-13
thats y im thinking about returning this one for an HP printer

---

### Post by umdoobby on 2009-08-13
one more question (just to be sure) this printer will work just fine right???

[http://www.newegg.com/Product/Product.aspx?Item=N82E16828115503]("http://www.newegg.com/Product/Product.aspx?Item=N82E16828115503")

---

### Post by Sunfire523 on 2009-08-13
I think that it would be better to buy a printer that has a driver available for download from the company.  I have a Brother MFC-465CN, and Brother actually offers a driver for the printer and the scanner.  I think they also offer drivers for the majority of the MFC printers as well.

---

### Post by umdoobby on 2009-08-14
all right ill keep that in mind

---

