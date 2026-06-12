---
title: "recommendations best printer"
date: 2012-07-31
forum: General Help
---

### Post by choochoousmc on 2012-07-31
Ok BEST but reasonably priced. 
Was using 11.04 since release.
Acer aspire 5532
Epson NX515
Worked great up until couple months ago. Then various things went wrong.
Opened up a thread asking for help, many replied with suggestions, but no cure.
Printer would activate sometimes sometimes not. Print graphics perfectly, would not print plain text. Or if there so faint you can't see it.
Tried new printer HP3522  never did get it to connect to router. HPLIP needs upgraded in repository to the newest version.
Finally did a complete FRESH install to 12.04. If I had a corrupted system, should be clean now.
Printer still will NOT print text.
Went to walmart and wrote down all available printers in stock
which one of these or alternate would you suggest.
Direct install, no software disk need, no drivers needed to download (special proprietary), reliable (last more than two years)
Want a plug and play all in one!!
Hewlett Packard
office jet  4622                 deskjet  2050   deskjet 3052  photosmart  5512

Epson  nx330      work force  545     

Canon  pixma MG2120  MG 3122  MG 5320

Someone recommended a HP4500 but currently non available locally.

I really need the information quickly. Have several document I need to get printed.

---

### Post by davidvandoren on 2012-07-31
Brother MCF series with the refill cartridges.
10 000 pages and not a single failure. Linux driver available on their website. 
The cartridges have no moving parts and don't have to be removed for refilling. The printer cleans itself every week so it has to be kept on the grid. 

[IMG]http://www.infozone.com.tw/catalog/image/data/J410-2.jpg[/IMG]

---

### Post by jonesyp on 2012-07-31
Hi,

You could check out the following links for supported models.  I tend to go for low cost Black & White Laser printers as the per page cost is lower than ink jets.  I have a Kodak Ink Jet and I seem to be forever changing the ink.

Best wishes

[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters)

---

### Post by choochoousmc on 2012-07-31
> **davidvandoren said:**
> Brother MCF series with the refill cartridges.
10 000 pages and not a single failure. Linux driver available on their website. 
The cartridges have no moving parts and don't have to be removed for refilling. The printer cleans itself every week so it has to be kept on the grid. 

[IMG]http://www.infozone.com.tw/catalog/image/data/J410-2.jpg[/IMG]

Thanks but you're saying I have to go get a proprietary driver.
I would prefer not to do that. But will consider it.
Refillable cartridge? Do you just buy bulk ink?
Mine is turned off many times when not being used.
Self cleaning every week?  Brother sends a web signal to clean it?
TIA

---

### Post by choochoousmc on 2012-07-31
> **jonesyp said:**
> Hi,

You could check out the following links for supported models.  I tend to go for low cost Black & White Laser printers as the per page cost is lower than ink jets.  I have a Kodak Ink Jet and I seem to be forever changing the ink.

Best wishes

[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters)

thanks for the reply.
I was hoping for peoples personal thoughts on what they have found to work.

---

### Post by davidvandoren on 2012-07-31
> **choochoousmc said:**
> Thanks but you're saying I have to go get a proprietary driver.
I would prefer not to do that. But will consider it.
Refillable cartridge? Do you just buy bulk ink?
Mine is turned off many times when not being used.
Self cleaning every week?  Brother sends a web signal to clean it?
TIA

You just buy the ink which is very cheap.
One printed page all color is going to cost you two or three pennies. 
You can schedule it to clean every Friday or when ever you wish. 

I am not sure about using the proprietary driver but I think you could choose to use Adobe postscipt 2

---

### Post by squaregoldfish on 2012-07-31
I go through periods of not printing much then doing large chunks at a time. I've tried various brands in the past but always gone back to HP DeskJets. They seem mechanically rock solid and don't seem to use ink at an alarming rate. The sporadic workload doesn't seem to upset them either.

There's a good enough range of models to find one to match your budget, and Linux support is pretty much perfect in my experience.

Steve.

---

### Post by cogier on 2012-07-31
HP provide an open source driver that works for many of their printers. This should already be loaded on a standard installation.

You can install the HPLIP Toolbox from the **Software Centre** for extra control. Installation of my Photosmart on my network was just a couple of clicks using the Toolbox.

A list of supported printers is available here (Check that all the features you want are supported)[http://hplipopensource.com/hplip-web/supported_devices/index.html]("http://hplipopensource.com/hplip-web/supported_devices/index.html") 

The choice of printer is then fairly big.

---

### Post by Cheesemill on 2012-07-31
To see if a specific printer is compatable check the OpenPrinting website:

[http://www.openprinting.org/printers/](http://www.openprinting.org/printers/)

---

### Post by gifford on 2012-07-31
My recommendation would be Brother MFC series. Great printers/all-in-one with good Linux support from Brother. Many of the drivers are available through synaptic and others on the website.

Having used several of them over the years, I have had no complaints nor problems.

---

### Post by kurt18947 on 2012-07-31
> **davidvandoren said:**
> Brother MCF series with the refill cartridges.
10 000 pages and not a single failure. Linux driver available on their website. 
The cartridges have no moving parts and don't have to be removed for refilling. The printer cleans itself every week so it has to be kept on the grid. 

[IMG]http://www.infozone.com.tw/catalog/image/data/J410-2.jpg[/IMG]

Oh yeah!  I got the smaller cartridges so I can close the door and don't print big jobs.  The install using Brother's installer has been brain-dead simple on the print side.  The scanner install has a couple peculiarities.  They're documented but it helps to know they exist and where to find the solutions.  Also note that Brother's install is via the command line.  I don't know that the newer Brother MFDs have drivers available in the repositories yet.

I will note one problem I had with the refillable cartridges.  I bought an prefilled LC61 set off ebay.  I was having problems with nozzles plugging.  I bought another set, this time empty and filled them with bulk ink from a local supplier.  No problems to date with 2 printers using locally acquired bulk ink and the refillable cartridges.  Cost for ink is about $11 for 8 ounces for black and $6 for 4 ounches of color ink.  Most people use a lot more black than color of course.  

Something else to consider re printheads.  Some - not all- HP's use cartridges with print heads built into the cartridge.  Change the cartridge, change the printhead.  The Brothers I have use a fixed print head, the cartridges are really just ink tanks with no electronics or kill-me chips.  Downside is if the printhead has problems that cleaning won't fix, a new printer is probably cheaper than a new print head plus labor to install it.  There are pluses and minuses on both sides.

Our local Staples flier has the MFC-J430W on sale this week for $49.99.  If I wanted to buy 2 HP cartridges for the retired 940C deskjet, it'd run me over $55.00

---

### Post by choochoousmc on 2012-07-31
Thanks for the info today guys.
I went to Office depot, have a pretty knowledgeable tech guy.
Explained the situation to him as in other thread about needing help.
He believed a power surge or a sudden loss of power,
Likely corrupted either a circuit board or a firmware hard file
in the printer.
Recommended a couple printers HP.
went with the HP office jet 6600/6700 A little fancier than what I really needed.
But it was same price as a cheaper model(on sale).
This one does NOT require a cable connection or software disk to connect to the router,
although the disk is recommended. But the disk is for Windows and mac only.
We need a write in campaign to tell HP to stop doing this or to include Linux on the disk.

I am now up and running. If the first HP I bought would of connected automatically I would have been spared a lot of headaches.

The tech says Brother printers have more failure rate in his store than any other brand.

But again guys thanks for the input and will mark as solved!

---

