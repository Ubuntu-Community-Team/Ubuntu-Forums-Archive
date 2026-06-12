---
title: "HP LaserJet 1000 Not Printing on Lucid?"
date: 2010-08-17
forum: General Help
---

### Post by neu5eeCh on 2010-08-17
I posted this question under Hardware & Laptops but that might have  been the wrong section. So... I'm trying it here. I'm converting my  coworker to Linux (who loves it) and I've gotten  everything working but this %$#@ printer! I've tried the various  solutions posted on these forums (over the past 4 or 5 years). But none  of them seem to work.
 
 
 Has anyone solved this problem with Lucid (10.04)? Are there some new steps that pertain to 10.04?

---

### Post by earthpigg on 2010-08-17
hi,

HP printers, in general, have outstanding Linux support in one way or another. So much so that my general advice to friends & family using ubuntu is this:

> "need a printer? look on craigslist, pick any used HP USB printer that has the features you want, and have the seller show you that it works by printing something on his computer before you purchase. once you buy it, plug it in and play around in system -> admin -> printing. if you can't get it, ill come over and set it up"

The ultimate authority on all Linux printing is openprinting.org.

Here is what they have to say about this printer: [http://www.openprinting.org/printer/HP/HP-LaserJet_1000](http://www.openprinting.org/printer/HP/HP-LaserJet_1000)

it looks like there is a package in the software center that comes up when you search for "foo2zjs".

If advice from them fails, HP has this to say: [http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

> You have selected Ubuntu 10.04 using the HP LaserJet 1000 Printer.

Ubuntu 10.04 supplies HPLIP 3.10.2 and it does support your printer.

As the version of HPLIP supplied with your operating system supports your printer, you may continue to use that version of HPLIP.

You may now optionally download the latest version of HPLIP to get access to new features and bug fixes.


so, here is what we have:

according to openprinting.org, you need to install the "foo2zjs" package and run the command > cat /usr/share/foo2zjs/firmware/sihp1000.dl > /dev/usb/lp0 or possibly > sudo cat /usr/share/foo2zjs/firmware/sihp1000.dl > /dev/us/lp0


according to HP, you only need to install the 'hplip' package from software center and click around a bit in system -> preferences -> hplip toolbox or system -> administration -> printing. notably, it can't hurt to start the hplip toolbox and go to configure -> preferences and try messing with a few of those options, if needed.


please let us know which one ends up working, so others can benefit from your experience. i would try the hplip method first, but you could also decide by flipping a coin. if you do the openprinting.org method first, remember to uninstall the package before trying the hplip method.


one final thing: sometimes my computer decides to be retarded and forget that there's a printer installed & plugged in. don't ask me why. restarting cups fixes that.

```
sudo /etc/init.d/cups restart
```

unplugging the printer from the USB port and plugging it back in also works, but typing that is less work.

---

### Post by neu5eeCh on 2010-08-17
That's a great answer and you took a lot of time to provide it. Thank you! I'm going to print it out and the next time I'm sitting at his computer, I'll give it a shot. I've tried some of the solutions you offered, but not all of them. I know this printer works on other Linux systems, so it's just a matter of getting the right combination.

---

