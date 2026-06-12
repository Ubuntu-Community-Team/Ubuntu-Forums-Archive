---
title: "hp laserjet 4100 49.4CO2 service error"
date: 2012-03-05
forum: General Help
---

### Post by astroclast on 2012-03-05
Hi all,

I'm not sure this is the proper place for this thread, so apologies in advance.

I use Ubuntu 10.04 (Lucid Lynx) for the following.  Note that a colleague with 11.10 has no problem using the very same printer.

I have been trying to get to print on a HP LaserJet 4100 printer at work and I keep failing miserably.  I can set up the printer (described below) and print a test page, but after that point I keep getting "49.4CO2 service error" messages on the printer's screen.

For the setup I do the following:
- System->Administration->Printing;
- On the GUI, click on the "+ Add" button (or Ctrl+N);
- On the next window, click on the "AppSocket/HP JetDirect" on the left, and enter the printer's IP address on the right (and use the recommended port 9100);
- On the next GUI, I "Select printer from database", and pick "HP";
- On the next GUI, I pick the "LaserJet 4100" model with the recommended driver "LJ 4100 series v.3010.107 Postscript [en] (rec)" or the foomatic driver;
- On the next GUI I pick the memory for the default driver (doesn't come up for the foomatic);
- Finish, print a test page and that's the last time I can use it.

From a google search I gather that this is a communication error, but I'm not sure how to address it.  I'd look into it in more detail myself, but I'm in the middle of writing my dissertation, so I don't have any time to spend on it, and on top of that I need it to work ASAP.

Has anyone encountered this before?

Thanks for your time.

Cheers!

---

### Post by ajgreeny on 2012-03-05
As you have already googled the problem I presume you have already found the information that a restart of the printer can get rid of that message, and that you have done this, ie turned off at the mains electricity supply, and left it for a few minutes before turning back on again.

It seems that it may also be a corruption of something in the instructions from computer to printer.  Have you tried installing, or totally removing then reinstalling hplip in your system as it appears that it should work with that printer;
See [http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_4100_series.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_4100_series.html)

---

### Post by astroclast on 2012-03-05
Hi ajgreeny,

Thanks for the response.  I've followed your advice, and it looks like I may have found a problem with Chrome.

I unistalled cups and purged hplip and then reinstalled them.  I was able to print a couple of test pages from the Printing GUI, like before.  I was also able to print local files from evince, and even Chrome.

The problem I guess kicks in when I try to print an online PDF through Chrome.  After that, no printing may be done, unless I reboot the printer.

So, this may be it.  I'll keep an eye on it over the next couple of days to see how it goes.

Thanks for your help!

---

### Post by astroclast on 2012-03-05
Then again, I cannot print from the command-line either, so it looks like it's something systemic.

At least now I know I can print with the good old (Windows) method: turn off, turn back on.

Any ideas/suggestions/hunches are welcome.

Cheers!

---

