---
title: "Why do I get a blank page when printing?"
date: 2009-07-05
forum: General Help
---

### Post by oxf on 2009-07-05
This is most frustratiing!  I have gone the printer setup, i.e System/Administration/Printing.
Printer cofig window pops up and my printer has been detected and is displayed right there.
 
But when I go to print test page it sends the job to the printer and starts printing, except one problem..... the page comes out blank! (exactly the same thing happens if I print a document also) Before anyone asks, yes there IS ink in the cartridge and I can switch to windows and print just fine. Any ideas whats going on?

I'm using Jaunty 9.04 and the printer is an HP Deskjet D1460

Thanks

---

### Post by kilowattradio on 2009-07-05
Do you know what driver you are using with the printer? Are you using CUPS or LPR?  

[http://hplipopensource.com/hplip-web/models/deskjet/deskjet_d1400_series.html](http://hplipopensource.com/hplip-web/models/deskjet/deskjet_d1400_series.html)

According to this if you have hplip installed it should work fine in Ubuntu 9.04

---

### Post by oxf on 2009-07-05
> **kilowattradio said:**
> Do you know what driver you are using with the printer? Are you using CUPS or LPR?  

[http://hplipopensource.com/hplip-web/models/deskjet/deskjet_d1400_series.html](http://hplipopensource.com/hplip-web/models/deskjet/deskjet_d1400_series.html)

According to this if you have hplip installed it should work fine in Ubuntu 9.04

Yes it says my printer is suported. Driver? hmm? Well I installed from the Live CD so whatever the default is I guess. I have not downloaded anything yet. How do I check?

---

### Post by oxf on 2009-07-06
> **oxf said:**
> Yes it says my printer is suported. Driver? hmm? Well I installed from the Live CD so whatever the default is I guess. I have not downloaded anything yet. How do I check?

I'm assuming I'm using LPR since I've not downloaded anything extra. This is very weird since it goes through all the motions of printing but just doesnt do the ink bit!

---

### Post by coffeecat on 2009-07-06
According to [this OpenPrinting page]("http://openprinting.org/show_printer.cgi?recnum=HP-Deskjet_D1460") your printer is supported, which means that the necessary drivers will have come in the tin, so to speak, with a Jaunty install. Usually, HP printers 'just work' with Ubuntu (that's certainly my experience) so a couple of suggestions.

Open System > Administration > Synaptic and install the package hplip-gui. Hplip will already be installed, but hplip-gui will give you a useful GUI frontend. Now go to System > Preferences > HPLIP Toolbox, and have a look under the various tabs, particularly the "Action" one, where you can try to print a test page. Check all the settings.

If you can't fix the problem with the hplip-gui, go to System > Administration > Printing and delete the installed D1460 printer. Make sure you have the printer plugged in and switched on, click on 'new' and go through the wizard to reinstall it. Try a test page when prompted. Sometimes a simple reinstall of the printer does the trick. It's even been known to be necessary in Windows. :wink:

Lastly, if you're still stuck or want a more sophisticated printer config utility than the System > Administration > Printing one, open firefox, type 'localhost:631' in the address bar (no quotes) and you'll get the CUPS configuration page.

---

### Post by stinger30au on 2009-07-06
to proce if it a hadrware or s/w issue, print to a pdf file first

if you dont have a pdf printer installed on the linux box fireup shell and type in

sudo apt-get install cups-pds

then go sysem, admin, printing and install the pdf printer


now print to the pdf creator and check the output

if there is a blank page first before the print, then its a s/w issue

---

### Post by oxf on 2009-07-06
> **coffeecat said:**
> According to [this OpenPrinting page]("http://openprinting.org/show_printer.cgi?recnum=HP-Deskjet_D1460") your printer is supported, which means that the necessary drivers will have come in the tin, so to speak, with a Jaunty install. Usually, HP printers 'just work' with Ubuntu (that's certainly my experience) so a couple of suggestions.

Open System > Administration > Synaptic and install the package hplip-gui. Hplip will already be installed, but hplip-gui will give you a useful GUI frontend. Now go to System > Preferences > HPLIP Toolbox, and have a look under the various tabs, particularly the "Action" one, where you can try to print a test page. Check all the settings.

If you can't fix the problem with the hplip-gui, go to System > Administration > Printing and delete the installed D1460 printer. Make sure you have the printer plugged in and switched on, click on 'new' and go through the wizard to reinstall it. Try a test page when prompted. Sometimes a simple reinstall of the printer does the trick. It's even been known to be necessary in Windows. :wink:

Lastly, if you're still stuck or want a more sophisticated printer config utility than the System > Administration > Printing one, open firefox, type 'localhost:631' in the address bar (no quotes) and you'll get the CUPS configuration page.

OK finally got it sorted. I tried all of the above and still had the same result of printing a blank page. The CUPS page revealed that for some reason (stll unknown) it kept reverting to using the colour cartridge even after I'd selected B/W (I dont have a colour one installed at the moment). I did what you sugested and deleted and then reinstalled the printer and now it stays with the B/W cartridge and prints properly

Thanks for the help!

---

