---
title: "Help me choose a printer?"
date: 2010-11-07
forum: General Help
---

### Post by VanillaMozilla on 2010-11-07
I'm looking for an all-in-one ink jet for light home use, that works flawlessly with Linux.  (Currently we're almost paperless.)  I ESPECIALLY want to avoid printers/scanners/etc. with flaky drivers.  So that's the Linux question.  What works flawlessly and what doesn't?

=========================
	Plus, maybe you can tell me if there are any gotchas or other things I need to know.  There's a lot of info out there, and I've done some research, but I'm interested in it from your perspective.  Any reasonable price, $100 to $300 is fine.

	I would prefer one printer combo that does it all, but I could compromise on some functions, for example, buying a separate scanner or a separate photo printer.  I might defer buying a dedicated photo printer if necessary.


Requirements
High quality
Must work flawlessly or almost flawlessly with Linux
Printing, scanning, copying
Wireless or ethernet, wireless preferred
No hassles.  OK, I'm willing to go get a driver, but it better work right.
Separate color cartridges

Optional
Long-lasting photo ink
Print CDs
High-resolution scanner for slides
Fax

Not wanted
Direct photo printing; photo editing (that's what a computer is for)

Strong dislikes (gotchas)
Excessive ink cost
Complexity
Printers that are dried out when I want to use them
Printers that refuse to print black and white if one color is low
Scanners that don't cover the whole page

Some candidates
Canon MG8120, 6120, 5229, MX7600
Epson Artisan series
HP Photosmart series

---

### Post by MyR on 2010-11-07
good luck!

---

### Post by VanillaMozilla on 2010-11-07
In other words, they're all flaky?

---

### Post by MyR on 2010-11-07
I am very happy with my printer.  However, it is largely a guessing game when you buy one due to rampant lack of reliable information on whether a printer is or is not compatible with Linux.  Does the manufacturer provide drivers?  Are there open source drivers available?  What drivers to use?  What features will work?  Will the drivers work with my distro?  Will networking function properly?  Will the colors print correctly?  Will it scan if I press the scan button?  Will I be able to configure the printer from Linux?  Will Linux be able to power-on the printer?  What program do I need to print on CDs?  Will I need to compile the drivers again if I upgrade the kernel?  As you probably already know, there is a "database" of printers, rated on their level of Linux-compatiblility.  Will a printer that works "perfectly" be able to scan/fax/network perfectly? Maybe. Maybe not.

The more features the printer has, the less likely it will be to work.  Finding the right printer for you is a nightmare already and finding the right printer that is also fully Linux-compatible is next to impossible, especially with all the features you want.

I intend to put a stop to this within the next 2 years when I re-open [The Linux Aisle LLC]("http://www.linuxaisle.com") and start some other projects I have in mind...

P.S.  Based on limited personal experience and plenty of research I tend to recommend HP, and many others would say the same.

---

### Post by mosaic2s on 2010-11-08
I would choose a printer  on the following parameters - 

1. Ability to use ink tanks - continuous ink supply system.
2. Most selling in the market - ask around, check with 2-3 vendors and users with similar work profile as yours.
3. Whether the company gives linux driver with it?  must ask the company directly.

Latest printers may not have linux drivers. But printers that sell most are likely to have CISS as well as company will release the linux driver at some stage.

Bought EPSON PHOTO STYLUS 1390. installed CISS on it. Runs on linux. Ink cost is down to minimal.
btw, canon beats this printer hands down. We had canon ix4000 before this. That had speed and sharpness in print. And it was 4 years before this one came into market.
Suggest go for canon if looking for quality. CISS is bit difficult. Epson is good for low cost.

---

### Post by VanillaMozilla on 2010-11-08
Thanks for the helpful information.  Sure enough, I did find that the Ubuntu Wiki recommends HP for extensive driver support (albeit indirect support with no guarantees), with less support for other brands.  This seems to be about as good a source as any:  [https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers) .

Thanks, mosaic.  I had not heard of CISS, but it's long overdue if it works.

I was sort of hoping that people would write in and say something to the effect of "I have X and it works well, but watch out for Y," but maybe I was asking too much.

---

### Post by gillmt on 2010-11-08
I have an HP C7280 which works fine - it is detected immediately. I set it up wirelessly without switching on any PCs and I can share it between two Ubuntu and one XP machine (one with a USB connection).

It scans both wirelessly and wired (surprised me)

I took ages to work out how to get the duplex working (A4 duplex was a paper choice I didn't know about until I poked about in paper source)

The problem I have had is in getting 6"x4" photos - I have tried setting it up as another printer and this seems to work OK.

With the HPLIP GUI installed I can even check ink levels.

---

### Post by cek on 2010-11-08
I have an HP C5580 that works flawlessly.  Print/Scan/Copy.

---

### Post by MyR on 2010-11-08
I have a fully Linux-compatible (and inexpensive) HP deskjet printer/copier/scanner that I use for documents and share over the wireless network. For photos I edit them on the computer, put them on a USB stick, and take them to my dedicated Canon photo printer (that is not connected to a computer).  The photo printer does work with printing directly from Linux but the colors are a little bit off.

I thereby avoided the hassle of finding a good photo printer with lots of features and Linux-compatiblility.  So you can get a decent $50 printer for documents and scanning, and a nice $250 photo printer.

If you're curious about the models I can answer that when I get home.  Hope this helps.

---

### Post by VanillaMozilla on 2010-11-08
Wow, great answers!  There are so many choices, and it's really hard to get everything you need/want in one or two devices.  The two HP's are obvious candidates.  Some of the Canons look great too, but so Linux-iffy.

---

### Post by blazemore on 2010-11-08
Avoid Lexmark.

In my experience, HP provide the best Linux experience.
I have an HP Deskjet F2480 and it works out of the box in Ubuntu, including ink-level reporting.

---

### Post by pricetech on 2010-11-08
My Wife's PhotoSmart works flawlessly with both Hardy and Lucid.  Ink cost is not too bad and as long as you stay away from photo paper it lasts.

---

### Post by VanillaMozilla on 2010-11-09
> **MyR said:**
> I have a fully Linux-compatible (and inexpensive) HP deskjet printer/copier/scanner that I use for documents and share over the wireless network. For photos I edit them on the computer, put them on a USB stick, and take them to my dedicated Canon photo printer (that is not connected to a computer).
Yes, I am curious about the models.  If you're the kind of person like me who tries to get everything in one or two products, it's quite a project.  To be sure, there are some very nice printers out there.

For anyone who's interested, here's what I've found in a nutshell.

* Many of the Canon drivers -- especially for the latest, fanciest models -- are nonexistent or incomplete.

* Epson apparently has a U.S. patent on printing on DVDs/CDs.  Canon can't offer it in the U.S., although some people have had luck buying a part and converting them (the parts source now appears to be shut down).  HP offered CD printing on some models (mostly Photosmart?), at least until recently.

* HP Photosmart Premium Fax has CD printing, and you can get one really cheap now, but it's ugly, and a lot of users hated it.

* HP C5280 is still available in some places (cheap), but it apparently uses a LOT more ink than more recent models.  I'm unaware of recent models that offer CD printing.  This one might be the best bet, although I really hate being held hostage over ink.

---

### Post by efflandt on 2010-11-09
Lexmark inkjet printers may be difficult.  But their network Laser printers work fine because they do common postscript and HP PCL, and Lexmark provides ppd files for cups.

I have a Lexmark C543dn network color laser with duplex at home and it works great with Ubuntu.

I also have an inexpensive Lexmark X204n multifunction mono laser/color scanner at work, which works in place of our HP printer when it goes on the fritz by simply setting its IP to the IP that the HP was using, without even having to change any PC drivers (including remote printing from our factory via VPN).  It is the same 1200 dpi and does postscript and HP PCL (but not duplex).  Although, I have not tried scanning from Linux, so I do not know if or how well that works.

---

### Post by Muskiet on 2010-11-09
I have bought a Canon MP250 which works great.
Mind you... when I bought it it was still hard to find drivers for Linux systems (found them on the European Canon site) and it took me a while to get not only the printer but also the scanner working.
But after a couple of hours of tinkering It's a great printer for little money working flawlessly with Ubuntu 10.04.
I'm sure now that it is several months later it's easier to find the drivers.

---

### Post by MyR on 2010-11-09
> **VanillaMozilla said:**
> Yes, I am curious about the models.  If you're the kind of person like me who tries to get everything in one or two products, it's quite a project.  To be sure, there are some very nice printers out there.

My main printer is the HP Deskjet F4280, which prints & scans perfectly.  Photo printer is an Epson R380.  Prints top-notch photos.  After sharing the deskjet over my wireless network, my setup meets all your requirements.

Enjoy

---

### Post by VanillaMozilla on 2010-11-09
Wow, more great suggestions.  Thanks, Myr, especially, I now have several good candidates (including some store bargain closeouts).  A quick search shows that the R380 has been replaced by the Artisan 50, which is probably discontinued.  For you cheapskates, you can plug it into a big jug of cheap ink (search for CISS).  (I don't know how fade-resistant the ink is, though.)  It appears that many (all?) of the recent Epson printers print on CDs.

I'm hoping all the information here is useful for other people.  It's not just me.

Myr, great thing about your store.  Just as a suggestion, you might consider the Digital Photography Review model, so you wouldn't have to have expensive inventory.  Of course, with Linux you wouldn't have the volume they get.

Good point about compatibility for Lexmark (and possibly other) printers.  I once needed a laser printer for a legacy 486, which was many years past its prime.  All available printers had outrageous hardware and software "requirements".  I ignored the requirements and bought a cheap Lexmark that emulated HP PCL.  It worked perfectly from a parallel part, but that's harder to do with a USB port because you somehow have to defeat Plug and Pray.

Update on Canon:  The new models apparently do not have a CD printing tray, even in Europe.

---

### Post by gordintoronto on 2010-11-09
I seldom print in colour, so I got tired of *always* having the ink nozzles clogged up. My solution is a Brother laser attached to my router (it also does wireless, but I've never tried it that way) and send pictures to Walmart for printing. The Brother installs in about four clicks on a fresh Ubuntu install, and prints flawlessly.

---

### Post by VanillaMozilla on 2010-11-09
Update on Epson

It turns out that most of them are tested to work "Perfectly".
[http://www.openprinting.org/printers/manufacturer/Epson](http://www.openprinting.org/printers/manufacturer/Epson)
[http://arcriley.blogspot.com/2010/01/epson-artisan-810-on-linux-ubuntu.html](http://arcriley.blogspot.com/2010/01/epson-artisan-810-on-linux-ubuntu.html)

Somehow I missed that on my first search.  The Ubuntu Wiki badly needs to be updated for Epson:  [https://wiki.ubuntu.com/HardwareSupportComponentsPrinters](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters) .

---

### Post by VanillaMozilla on 2010-11-11
OK, I've ordered an HP C309a, $150 from Amazon.com including shipping.  I've seen it slightly cheaper somewhere.  Bye-bye, paperless office.  Since you all were nice and helped me, I'll leave a little summary of what I found, in case it's of use to someone.


Reasons for picking the C309a:

Supposedly good Linux drivers.  Scanner with good optical resolution, 5 inks including photo black, prints CDs/DVDs, uses 564 ink, should be somewhat easy on ink cost(?).  Bad points:  terrible Windows software; terrible user reviews on Amazon; Windows software _may_ be required to print on CDs.


==================================
Runner up printers:

Dell printers.  Nice looking, inexpensive, with Ubuntu support!  Consumer Reports likes these.  Bad points:  ink only available on line; medium scanner optical resolution.

HP C5580.  Prints CDs/DVDs.  Medium scanner optical resolution; Probably uses a lot more ink than the C309a.

HP 6500 or 6500 Wireless.  Uses 920 ink (fairly cheap), no CD/DVD printing, medium resolution scanner.

Epson Artisan and NX series.  If the HP isn't good enough for CDs, maybe I'll get an Artisan 50 for about $100.  These are probably ink hogs.

Canon MP990 and MG8120.  Advantages:  nice looking; European MP990 has CD print tray, not available in U.S.; photo black and photo gray inks; backlit film adapter unit for copying slides and negatives; disadvantages:  Linux drivers cost money and lack scanning.

__The film and slide scanner may be unique in this price range.__  Someone should try it.


=====================================
Other useful information I picked up:

1. Some printers have disposable heads.  The ones with separate cyan-magenta-yellow cartridges usually do not.  I think that means you have to be careful to avoid drying out the heads.  Print a page once a week.

2. If you turn off a printer or leave it without printing for a long time, it may slurp up enormous amounts of ink trying to purge.  Leave it on standby.

3. Dye inks are said to be pretty stable now.  Pigment inks are probably more stable (some Epsons can use these), but (1) the pigment may change the gloss of the paper; and (2) it may be harder to print very light (or maybe not).

4. Some printers (mainly the "photo" ones) have photo black and sometimes photo gray ink (dye) in addition to text black (pigment, I think).  Some have also have light cyan and magenta.  These may make for better photos.

5. Check the network specs.  There is 802.11g, 802.11n, Bluetooth, ethernet, or no network.  Some are really crazy, with their own e-mail accounts.  Don't assume anything.  Some wireless printers are said to be very hard to set up, and I suspect it might be helpful to set them up first with ethernet.

6. As said before, HP is supposed to have good Linux drivers; Epson may be good too (but I can't verify this); Canon is supposedly poor.  Others, well, do your own research.

7. My own, previous experience with inkjets drying out has been miserable.  We'll see this time.

---

### Post by VanillaMozilla on 2010-11-17
Initial impressions and setup information for the C309a (and similar HP printers)

I was dreading getting the printer and scanner running, but **it couldn't have been easier** on Ubuntu. :D If you've had some experience with this, you don't even need the manual.  Everything is about as automatic as it can be.  For a direct connection, just plug in a USB cable.  Done!  For a wireless network connection, the setup menu on the printer gives you the MAC address, if you need that (some of you may have your router set up to require it), and it allows you to choose a network and enter the password.  Very easy.  On the Ubuntu side, System>Administration>Printing> add network printer, and after about half a minute the printer just appears.  Bling!  Done.

Scanning?  It's already connected and set up!  Applications>Graphics>Simple Scan and you're on your way.

I haven't tried printing a CD yet, but it looks like it will be easy.

Checking ink levels is easy but it required a bit of ingenuity to discover.  For some reason the Printing dialog doesn't report ink levels.  I found out that HP support is in a package 'hplip'.  Right clicking on it in the Synaptic Package Manager gives me a list of files in the package, one of which is 'hp-levels'.  Just type **hp-levels** into a terminal and you get the levels.  For what it's worth, that is a link to a Python script in /usr/share/hplip, which contains a bunch of HP stuff.  EDIT:  you don't need software.  You can also do all the service from the menu on the printer.

Windows XP?  :confused:  It can't find the printer on the network.  But there's a solution, thanks be to Google.  Follow these directions:  [http://uis.georgetown.edu/software/documentation/winxp/winxp.network.printer.html](http://uis.georgetown.edu/software/documentation/winxp/winxp.network.printer.html) , but *instead of the IP address use the host name (use the menu on the printer to print out the network configuration).*  You can use the IP address, but if that changes at a later time you will lose the connection.  It's better to use the "Hostname".  Bill Gates' little joke is that to install to a network, you pretend to install it as a local printer.  Then you create a new, standard TCP/IP port and when the time comes, select standard, generic network card.  You need the CD for the driver, but probably not for all the other stuff on it.  For ease of setup, Linux definitely wins.  :D

---

### Post by MyR on 2010-11-17
Great, thanks for sharing!

---

### Post by underquark on 2010-11-17
I have an HP 930C sitting unloved and unused at the back of my desk.

I got a used HP2200 Laserjet which had over 100,000 pages on the clock complete with network module for free as my local library had a clear-out.  I have it plugged into a "HomePlug" to connect to home network.  Access it from two Linux machines with no problems and two Windows XP machines with occasional glitches with large files.  Toner/drum unit costs £65 each to replace but are good for thousands of pages.

It's the overall cost that matters really.

In terms of reliability, driver availability, ease of setup I'd go for HP

---

### Post by VanillaMozilla on 2010-11-17
> **MyR said:**
> Great, thanks for sharing!
You're welcome.  I always try to give something back, and to help other people.

Underquark, yes, I've also had good service from HP laser printers.

---

### Post by JDorfler on 2010-11-18
I'm rocking the HP Photosmart Plus.  I have no issues with it on my Linux network.  Even have the scanner shared out via Sane.d.  However, the Windows boxes on my network can only see the printer and not the scanner.  I'll probably install the web gui on my server to issue it out.

---

### Post by stefcep on 2010-11-18
Brother also have a fairly large list of Linux drivers for printers and multi-function centres.

---

### Post by VanillaMozilla on 2010-11-21
> **JDorfler said:**
> However, the Windows boxes on my network can only see the printer and not the scanner.
Same here.  The windows driver for the scanner will not install from the CD.  Also the Web site has the drivers as an .EXE file, but that executable hangs.  (I'm installing to the E: drive, so maybe that blows its mind.)  Not gonna try more.  I don't need it on Windows anyway.

---

### Post by VanillaMozilla on 2010-12-16
Sure enough, it's using ink at a horrendous rate.  After about 10 to 15 pages, most of them test pages, I have 60% of the black cartridge left, and 80% of cyan.  Just how should I handle this?

The way we print, we could sometimes print a page or two a week, or even less.  Almost every time it prints, it clunks and grinds for about a minute before printing.  I assume it's using my ink to clean itself.

I haven't seen any clear guidelines on how to handle that, to keep it from drying out.  Has anyone found a good way?  I'm thinking of leaving it turned off most of the time (from the front panel, of course), and printing a minimal test page once a week.  Does leaving it off use less ink than leaving it on?  Does anyone have a better idea?

---

### Post by MyR on 2010-12-16
I think many times the ink cartridges that come with the printer are not full cartridges.
I have also heard that photo printers use ink to clean themselves every time they are turned on, so depending on how frequently you print it may be better not to turn it off.

---

### Post by VanillaMozilla on 2010-12-16
The cartridges WERE full, not those funny little donut spares like on cars.  I haven't yet turned it off, but it appears to clean itself every time I use it.

---

### Post by maureenc on 2010-12-18
> **gordintoronto said:**
> I seldom print in colour, so I got tired of *always* having the ink nozzles clogged up. My solution is a Brother laser attached to my router (it also does wireless, but I've never tried it that way) and send pictures to Walmart for printing. The Brother installs in about four clicks on a fresh Ubuntu install, and prints flawlessly.

Gordon..... Any chance you could give me the model number of your laser printer? I have just become a Ubuntu user and have discovered that I don't have a hope of using my Lexmark X1100 (which I hate anyway)..

I need a printer that I can just plug in as I don't trust myself yet with the commands..... I also want laser rather than ink and only need mono....

Would be grateful for your help

Cheers..... Mo

---

### Post by klyndt on 2010-12-20
I just purchased a monochrome (b&w) laser printer from Brother (MFC-7440N). It has been well reviewed and comes with Linux support drivers.  For only $200 it is a great deal and I don't have to worry about ink wells drying up!

Klyndt

---

### Post by maureenc on 2010-12-21
Hi Klyndt - That's a bit on the pricey side for me.

I've been looking at the Brother HL2035 Mono Laser which also gets good reviews and is under £100.  

Does anyone have an Ubuntu 10.4 review for this one please?

Cheers

Mo

---

### Post by theasprint on 2010-12-21
Hi,

I have a HP OFFICEJET J5508 printer
Everything works on Ubuntu (Print, Scan, Copy & Fax)

You just need to install the HP Linux software/manager in Ubuntu software center.

---

### Post by maureenc on 2010-12-21
Unfortunately that one is o longer available Theasprint.

---

### Post by brookie on 2010-12-21
Brother printers are the way to go. They have Linux support and I have had no problems installing various models with their linux drivers. 

Here is their linux driver site:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

---

### Post by rburkartjo on 2010-12-21
i use a hp all in one. i have never had a problem with any hp printer. they are not expensive. i usually just buy at walmart.

---

### Post by maureenc on 2010-12-21
Thank you for all your help... The deed is done.... OH has ordered a Brother HL 2035 Mono Laser Printer for my Christmas present.... I may not receive it until next year, but.....

Merry Christmas
Mo

---

### Post by ussndmac on 2010-12-21
Couple weeks back I was at Sam's Warehouse Club and they had Epson NX127 for $39.97.

Couldn't past it up. Checked the forums and it looked like similar model #'s were supported. So I took a chance.

Short story: printer worked out of the box, had to install Avasys image scan to get the scanner running.

So far it's working just fine. I posted details on my blog: [https://iaworkshop.wordpress.com/](https://iaworkshop.wordpress.com/)

---

### Post by VanillaMozilla on 2011-01-18
I have an update on ink use for the HP C309a (PhotoSmart Premium Fax All-in-One).  I can summarize it with one word:  unacceptable.  Horrendous.

After 50 pages the black cartridge was reporting empty.  I got 64 pages before it actually ran out, at which point the CMY color cartridges were also reporting empty.  After cleaning the head (necessary to clear the streaking), they lasted another 14 pages before I had streaking on two colors.  That's 74 pages.  Photo gray was reporting empty a few pages later.

HP claims 300 pages of text for black, and 250 pages for color.  They claim 100 to 160 4x6 inch photos per cartridge.  My printing was mostly text; one page had a 4x6 photo on it--the others had much less or zero photo coverage.  These were the size 564 cartridges but not the [new, small 564 cartridges.]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02435884&cc=us&dlc=en&lc=en")  Part numbers for black and magenta were CB316W and CB319W.  It seems like the coverage is blatantly overstated, almost to the point of being fraudulent.

At $12 for black, that's 19 cents per page just for the black ink, **AND** another 38 cents per page for three color cartridges.  That's 57 cents/page, running the cartridges all the way dry.  Counting the gray cartridge, the total cost was about 70 cents/page for mixed text and graphics with light coverage.  That's double the cost of a 4x6 print.  Outrageous.

Refilling is interesting.  The cartridges consist of just a sponge full of ink.  You can refill them, but the cartridges use a nonresettable chip, so you can't tell how much ink is left.  You'll make a mess if you overfill, and you don't really want them to run dry.  You can buy empty aftermarket cartridges with transparent sides and cloned chips, but you don't get the patented HP sponge.  One more thing.  The printer will pester you endlessly about empty cartridges unless you turn off ink monitoring (you can do it from the printer menu).

I bought a set of the large cartridges ($102), but that's all.  Does anyone have any experience with InkTec ink?  They have a nice filling system, with no drilling.

---

### Post by VanillaMozilla on 2011-01-18
Duplicate post removed.  This site is melting down.

---

### Post by Adrian Challinor on 2011-01-23
Don't choose KODAK. I am waiting for DHL to collect the  KODAK ESP 7250. Its slow, it looses connection, stops printing, virtually no Linux support. 

Apart from the fact that the ink is cheap, there is nothing to recommend it. 

Anyone know if the HP Photosmart CN503B will work on Linux?

---

### Post by maureenc on 2011-01-24
Just a quick update on the Brother HL2035.

It worked beautifully straight out of the box on Ubuntu Lucid Lynx with the HL2030 series driver automatically selected.

Lovely neat little printer that does everything it says on the box perfectly.

Mo

---

### Post by MyR on 2011-03-12
First I want to thank you all for taking the time to post helpful tips for people looking for printers.  I owe special thanks to VanillaMozilla for starting this thread and giving me the motivation to create a website designed specifically for Linux users looking for a compatible printer.

On behalf of the Linux community I would greatly appreciate it if you could take two minutes to [share your printer experience]("http://linuxdeal.com/add-printer.php") on the site I have created over the last four months.

I would also appreciate any feedback you may have about the site.

With gratitude,
Adam

---

