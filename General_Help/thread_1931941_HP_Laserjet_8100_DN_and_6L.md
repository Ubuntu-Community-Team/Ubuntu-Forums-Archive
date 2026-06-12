---
title: "HP Laserjet 8100 DN and 6L"
date: 2012-02-26
forum: General Help
---

### Post by then_dude on 2012-02-26
Hello everybody,

i got this problem with my printer, but it seems really a problem a lot of people are having. 

i have ubuntu 10.04, and run on an parrallel port a hp 6l. the printer was found but could not print, the printing documents were pending and then disseappered. 

Now i have connected a hp laserjet 8100 DN on the parrallel port. 
ubuntu sees the printer, and i can print a test page, or a print self page. 
BUT when i print a document, the document gets processed (as long as it is a small document). The printer tells me that there is an buffer overflow problem.....

my mainbord is a z68 chipset. (asrock). 

can anybody help me out. a lot of people seem to suffer from the same problem. 

i could try to print via the utp port of the printer, but when i connected the utp port of the printer to the computer, ubuntu did not find the printer. 

please guys help me, i'm going crazy over this. 
thanks

---

### Post by Tamlynmac on 2012-02-26
The compatibility of HP 6l is located [here]("http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_6l.html"). - for the 8100 DN [here]("http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_8100_series.html"). After a quick scan of the tables the 6l using the Ubuntu included HPLIP driver will support parallel port printing, while the 8100 DN is does not include parallel port support.

I'd suggest you stick with the 6l and install the HPLIP print driver using this [wizard]("http://hplipopensource.com/hplip-web/install_wizard/index.html"). One thing to remember, when the install is completed - don't forget to reboot. The HPLIP driver for that printer should already be in Ubuntu 10.04, but perhaps it's compromised or in need of a bug fix. Which the new HPLIP driver will include. 

******* One other thought (before you install the new HPLIP driver) that might be causing problems is if the "Print to file" option is default selected in the printer setup, instead of the selected printer. The result of "Print to file" is very similar to what your defining as the 6l print problem. Just prior to printing, check and make sure your 6l is selected in the printer setup.

For future reference should you wish to confirm HP printer compatibility simply go [here]("http://hplipopensource.com/hplip-web/supported_devices/index.html") and select the printer.

Good Luck and hope this helps.

---

### Post by then_dude on 2012-02-26
thanks a lot   i'll give the 6l a try tomorrow.   i have seen that the 8100 is only supported by USB, i guess i will have to be a printer server USB module, or could i use a usb-parrallel cable, which would be much cheaper ?   i would like to use the 8100 because it is much much faster then the 6l  thanks again

---

### Post by Gremlinzzz on 2012-02-26
you could also use a upgraded live DVD, do not install just a test, to see if your printer would work better in say 11.10.:popcorn:

---

### Post by Tamlynmac on 2012-02-27
> then_dude
 i guess i will have to be a printer server USB module, or could i use a  usb-parrallel cable, which would be much cheaper ?

You could try the adapter cable, but my suspicions are that it won't work.  Depending on what's available in your area and if you have a spare PCI  socket in you system, you might try a PCI - usb hub. Adding 4 to 6 usb  ports to your system. They're fairly cheap and I think they're even  available at Walmart for about $10 - $20.

As for testing an upgrade (Gremlinzzz), I personally wouldn't suggest it  at this point. At least, not until you've identified that you can get  the printer(s) working. 11.10 has it's own problems and it appears your  comfortable with 10.04. I'd also be cautious trying a new version, until  you confirmed compatibility with other system hardware. I believe, the  driver installed with the wizard is the same one used in 11.10 and can  be installed fairly quickly by just following the wizard instructions.

Either way - Good Luck & if you need more assistance just post here and I'll remain subscribed to the thread.

---

### Post by then_dude on 2012-02-27
thanks for the replies.   some thougths.  I can get the 6L to run with a live cd of linux mint.  I used to run the 6L on 10.04 on my old computer.   Now i have a new pc, new hardware, a Z68 chipset.  i had several problems with it.  1)i use dual monitor and the onboard video. i could only solve it to upgrade the kernel to 2.38, 2)i had to use the pae kernel for 8gb of ram.  So my ubuntu is tampered.  it's a 10.04 with the kernel of the 11.10 .   But i noticed the same problems with linux mint: in livecd version i could print, once installed i had the same prolbem of pending the print documents...  someone suggested it that the driver of the videocard is interfering with the driver for the printer... i guess he could be very right.   2)when i said i needed a usb print server, i wasn't refering to a part to put in the pc, but a part to put in the printer. JetDirect connectivity card J4135A to be exact.   maybe today the linux kernel has better grip on the Z68 chipset and onboard video. or i might buy a video card to get over the hassle.  still i want to work with the laserjet 8100, so i guess i need to buy a usb interface. a bit of a cost ...

---

### Post by then_dude on 2012-02-27
what i didn't mention but maybe makes a difference is that the printer has a jetdirect print server.   So i guess, i can use it to print. If i connect the printer with the router and then configure cups, i should be able to print ?   what do you think ?

---

### Post by Tamlynmac on 2012-02-28
> then_dude
If i connect the printer with the router and then configure cups, i should be able to print ?   what do you think ?

I think that's definitely worth a try. However, I'm wondering if the jetdirect is Windows based and may not be compatible with the Linux driver. All I could find on compatibility with respect to this card's system requirements - was either Windows or Mac. With the 10.04 kernel modified, it will be interesting how your system  will react to the router.

Is there any way you can bypass the router and run the printer direct? This would at least confirm that the printer is interfacing with your system and the HPLIP driver. Then you could connect the jetdirect router and if problems arise you'll know it's directly related to the jetdirect.

---

### Post by then_dude on 2012-02-28
IT IS WORKING,


the jetdirect is a print server. that can be adressed at all time, if you use the correct IP adress,

so what i did: i connected the printer via the UTP print server connection to my router, and then 

add printer
choose jjetdirect
choose your type of printer: the 8100 is supported. 

it is that easy; i was thrown offguard because the hp pages did mention that the network for this printer is not supported by llinux, but i guess there is no UTP connection only a UTP print server connection. 

Just great, the confusion came with fact that i had never used a print server before, but it all came together when i thouhgt of using my router as print server. ..

anyway: the 8100 prints like a rocket, (it sounds like on 2)

But the parrallel port is still out, and not only on my pc, i have installed 10.04 on serveral other pc's with old hp laser printers and none of them is working. They all suffer from the same problem: the printer is recognised but if you print your document keeps on pending, processing, or looks like finalized (so disseapers, but the printer doesn't do a thing)

i think i might report a bug, cause this looks like one

thanks guys for the support

---

