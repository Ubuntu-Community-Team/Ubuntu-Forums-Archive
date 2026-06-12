---
title: "Linux and printer/scanners install/use any brand?"
date: 2012-06-27
forum: General Help
---

### Post by rapattack1 on 2012-06-27
Hi i have had a few printer/scanners plus MFC's and never seem to get this working. Is that normal? I am able to get the printer part working but never the scanner. Tried so many models because i often find printers on the street in an area nearby that is full of rich people that throw away a lot of good stuff...anyway i know they are working because i try them with windows and it works. 
Now for the printer that a friend has. She has a HP PHotosmart printer/scanner. Can't remember the model...maybe a C5180 as i did a google search and that looks like it. I think i installed it right using some site i googled(sorry don't remember which as it was a few days ago and i am not at the friends place. I had to download something from memory and there was a set of linux drivers amongst the file. Anyway turns out she doesn't have any ink so we can't proceed for now. That will take time to get as she and i don't have jobs. So thought i would try and find out what the norm is with these types of printers and maybe someone has some additional info so next time i know what  to advise....thanks

---

### Post by dino99 on 2012-06-27
by default ubuntu install the required driver(s), so no need to google then download etc, aka cups, gutenprint and hplip

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)
[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

---

### Post by rapattack1 on 2012-06-27
Yeah never found that the case with printer/scanners...well most of the time i can't get the scanner to work....in this case though the printer wasn't installing by default...ubuntu looked but didn't find it(usb connected) so i found some site and that got it installed but then we found out the ink had run out...it showed on the printer at that point not before

---

### Post by Cheesemill on 2012-06-27
Linux printer compatibility database:
[http://www.openprinting.org/printers](http://www.openprinting.org/printers)

Linux scanner compatibility page:
[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

---

### Post by rapattack1 on 2012-06-27
Yeah i think i have seen these lists but i am talking about when they are combined...printer/scanner together in one unit

---

### Post by dino99 on 2012-06-27
> **rapattack1 said:**
> Yeah i think i have seen these lists but i am talking about when they are combined...printer/scanner together in one unit

then google around "ubuntu+the modelUtry2workwith"

---

### Post by rapattack1 on 2012-06-27
yes thats what i did...anyway will report when i find out the model number if this girl ever replies to facebook messages he he...then i can progress to see if anyone else has had luck with this model. Also after we install the cartridges...ekkkk i hate being the local geek amongst the poor lol

---

### Post by JKyleOKC on 2012-06-27
Just FYI, in general scanners (including those combined with printers as all-in-one units) are not much more standardized than they were 20 years ago. In the 1990s I was professionally developing scanner and printer interfaces for graphics use as opposed to text, and we had to write different low-level drivers for every different model of scanner. Printers were a bit more standardized at that time, although inkjets required totally different drivers from laser printers, and not all lasers used HP's Printer Control Language.

Printers have now standardized to a much greater extent, but scanners are still a wild and wooly mess. Windows users have TWAIN which offers a semi-standard interface, but the Linux equivalent, SANE, doesn't always mesh with a scanner picked at random. Sometimes it will allow use of the scanner but not of most advanced features, too...

Epson's units have pretty good drivers but require the scanner and the printer to be treated as separate devices. I'm using an Epson Stylus NX305 at the present time, with the Epson drivers. HP units are a bit more problematical. Your best bet is to Google with the manufacturer's name and "SANE" as the search terms.

You mentioned finding one on the curb with dead cartridges; it's amazing how many people these days simply replace the printer when the ink runs out, since manufacturers often sell the hardware at a loss intending to make their profit on the ink refills!

---

### Post by rapattack1 on 2012-06-27
Thanks so much for that info!
No this is not a curbside printer that my friend has. It is a working printer she got from a friend that had upgraded. The friend of her friend never said the ink had run out.
I find stacks of printers but i usually only take lasers and never had to put a toner cartridge in yet...i am pretty fortunate that way.

---

### Post by pbrane on 2012-06-27
I use HP printers and scanners. GNU/Linux seems to have good support for HP devices as most device drivers from HP are open source. So far installing and using HP printers has been painless.

I have an HP OfficeJet 4500 MFD and installation was a 30 second process. I don't have any problems using the scanner/copy/fax devices. I use simplescan for scanning. FYI the 4500 is networked. I gave Add Printer the IP address and the rest was done automagically mostly.

As JKyleOKC pointed out the drivers for MFD units are usually separate for each device and in GNU/Linux the apps used to access each device are mostly separate as well.

---

### Post by rapattack1 on 2012-06-28
OK just got a message back and the printer is a HP Photosmart C5180 [http://h10025.www1.hp.com/ewfrf/wc/product?cc=us&lc=en&dlc=en&product=1153481](http://h10025.www1.hp.com/ewfrf/wc/product?cc=us&lc=en&dlc=en&product=1153481)
so will take a look at that list in a sec...thanks for that info pbrane

---

### Post by rapattack1 on 2013-01-05
Well i upgraded to 12.04 so my latest printer worked. I got rid of the MFC one but who knows i might give one a try if i come across another one now :0)

---

### Post by kurt18947 on 2013-01-05
If buying new, I go to a manufacturer's web site.  If the manufacturer doesn't mention linux support for the model I'm considering,  that manufacturer has a brief stay on my 'possibles' list.  For 'found' devices, I think HP, Brother and Epson are the best candidates.  Lexmark inkjets are difficult to impossible, Canon's support seems spotty and not as straight forward.  This is just my opinion/observation.

for HP devices, if you haven't done so you might want to install hplip-GUI found in the repositories.  It's a GUI front-end for hplip that makes some utilities easier to find/use.

---

### Post by rapattack1 on 2013-01-05
No i come across secondhand machines. I also run a separate wndows machine so i know when they are working or not :0) Yes i have had more success with HP laser printers. Never had any issue with any bubblejet/inkjet brand. I never buy new as near where i live there is a rich area where they throw away so much good stuff :0) I will refer back to this post thought when i find any future machines as it would be good to have a laser MFC. As i don't have much workspace i tend to like to upgrade even if it is from the streets he he.

Yeah that HP thing happened automatically with this distro upgrade and the previous 10 version i had to install it but it didn't work. Tried twice and gave up. Thats with this latest printer but i tried to install 3 other laser printers with no sucess and even do a print share ...no success. The injet printer though it did work.

---

### Post by kurt18947 on 2013-01-05
> **rapattack1 said:**
> No i come across secondhand machines. I also run a separate wndows machine so i know when they are working or not :0) Yes i have had more success with HP laser printers. Never had any issue with any bubblejet/inkjet brand. I never buy new as near where i live there is a rich area where they throw away so much good stuff :0) I will refer back to this post thought when i find any future machines as it would be good to have a laser MFC. As i don't have much workspace i tend to like to upgrade even if it is from the streets he he.

Yeah that HP thing happened automatically with this distro upgrade and the previous 10 version i had to install it but it didn't work. Tried twice and gave up. Thats with this latest printer but i tried to install 3 other laser printers with no sucess and even do a print share ...no success. The injet printer though it did work.

Possibly the new distro worked because it contained the newest hplip version. I don't know that, just a thought.

---

### Post by 1clue on 2013-01-05
FWIW if you come across secondhand inkjets and then buy new cartridges, you're almost paying the price of a new printer.  In one case in my past, a newer, better printer was cheaper than the cartridges for my old one.

Do yourself a favor.  Go get a laser printer that you know has good support.  You at least get more than a single cartridge of life out of them, and it's worth buying the toner.

The same basic approach could be used with a laser, you just need to drive down different alleys to get them.

---

### Post by Rebelli0us on 2013-01-05
> **Cheesemill said:**
> Linux printer compatibility database:
[http://www.openprinting.org/printers](http://www.openprinting.org/printers)

Linux scanner compatibility page:
[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

Thank you, interesting list. I found an error on the first listing under Brother -- **MFC-4550**, it says, "Black & White laser printer, max. 600x600 dpi, **this is a Paperweight**".  I have one and it works just fine with the driver for Brother **HL-720** since they're the same engine.

---

### Post by 1clue on 2013-01-05
I think the openprinting page is useless.  Just an opinion, but every time I used it they said whatever I had would never be supported, and then later i find out that my printer IS supported, by some other driver.

Not only that, they wouldn't unsubscribe me from their mailing list.  I had to cancel the email address and start over.

---

### Post by t0p on 2013-01-05
I want to add my tuppence' worth here.  The openprinting site says that my HP Deskjet D2660 printer works with Linux.  But I've tried it with a few Ubuntu releases now, and it won't work.  Ubuntu sees the printer, even queues jobs, but no printing ever happens.  I'm currently running my laptop as a Windows/Ubuntu dual-boot so I can print using Windows 7.

Anyone here actually have any joy with the HP Deskjet D2660 and Ubuntu?  It's a good few years old, not a top-of-the-range latest thing.  I'm using Ubuntu 12.04.

Oh, and I just wanna add how jealous I am that the OP finds decent kit dumped in the street.  Best thing I ever found was an ancient laptop with a dead battery.  Plugged it in, and it had Windows 98 on it!  Wasn't I lucky?

---

### Post by rapattack1 on 2013-01-05
I downloaded that thing just recently so if it was version distro dependant i dunno.
No i throw away machines or pass to someone else before they run out of ink....i mainly use lasers not inkjets/bubblejets. I have one of those right now but rarely use it. I haven't bought ink for over 10 years and never bought toner at all.
Yeah i was getting the printer installing and not printing just like you. Wouldn't do a test page or anything. I don't have those models i am afraid.

Ha ha yeah i even found an iphone 3g....i am real good at my finds :) I mostly sell the tech stuff even if it is not working because people buy stuff for parts on ebay. I amanaged to sell so much i bought an ebike, escooter, new mobo and several other things in the last 3 years. I am on a pension so not much money to buy tech toys. I have a bluetooth mouse, wireless router, modem adsl 2+, my windows machine, lcd monitors, headphones, external(500gb) hard drive, too many other things to name that i kept for myself...all working and i am one happy ameteur techie. OH i find heaps of lappies too. The newest had winxp on it but i do find a lot of old Toshibas...those big ones...so cool :0)

---

