---
title: "Printing Problems"
date: 2011-07-15
forum: General Help
---

### Post by ddjolley on 2011-07-15
I am trying to help a friend get started with Ubuntu by working from the live CD untill we have convinced ourselves that we can get everything that we need to work.  Once we have achieved that we will install Ubuntu to the hard drive.

Our one remaining problem seems to be printing.  She has an HP OfficeJet 6500 USB printer.  We have the computer conntected.  Strangely, when I boot from the CD the printer shows up as installed even though I did nothing to install it.  After having submitted a print job it shows the printer status as "idle" and the print queue is empty.  I tried deleting that printer and re-installing.  The installation went as one would expect.  However the results are the same.  I'm beginning to think that somehow the problem is related to the fact that we are operating from the live CD.  Any suggestions for getting this thing to print from the live CD.

Thanks for any input.

          ... doug

---

### Post by CatKiller on 2011-07-15
Not that it helps you test it from the live cd, but it is supposed to be [fully supported]("http://hplipopensource.com/hplip-web/models/officejet/officejet_6500_e709a.html").

---

### Post by ddjolley on 2011-07-16
I should have mentioned that the printer works OK when I boot the system from the hard drive so that XP is the OS.

I'd really like to get this one figured out because I'm afraid that I'm going to loose this potential user to the i-mac if I can't get this problem solved.  Thanks.

          ... doug

---

### Post by Matt__ on 2011-07-16
[]("http://img13.imageshack.us/img13/6163/hplipexample.png")that printer will work perfectly once you have installed HPLIP with its gui toolbox
[I][http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

enter details of OS version and printer, download the file, then follow the easy instructions.(you may have to go back one page to see the instructions, not that theyre really needed)

the .run will do all the work and resolve any dependency problems.

[example image of HPLIP GUI](http://img13.imageshack.us/img13/6163/hplipexample.png)
[/I]

---

### Post by varunendra on 2011-07-16
At the risk of being judged a "troll", I couldn't help but jump in to share my opinion/advice. If your friend can afford an imac, why don't you consider investing in a dedicated network print server?

Not that I doubt the aforementioned printer's compatibility with linux, but a print server would be especially useful if she has more than one computer on a network with whom she may later wish to share the printer. I'm using an extremely cheap one : TP-Link's [TLPS310U]("http://www.tp-link.com/PRODUCTS/productDetails.asp?pmodel=TL-PS310U"), which is not a real dedicated print server at all, although is advertised as the same. But with a little tweaking, I have managed to use my HP LJ3050 MFP, Samsung SCx4300 MFP and Samsung SCX-3201 -all multifunctional usb printers- as normal nework printers with its help (only one of them connected at a time, I haven't tried all of them connected simultaneously, as I don't have a fast USB hub). More elegant ones from Belkins or Netgear may be more capable and easier to be recognized.

But forget all of the above if she has only one computer and this printer with no plans of its sharing in future. :)

---

### Post by CatKiller on 2011-07-16
hplip is installed by default. I'm pretty sure the GUI is in the repositories.

---

### Post by Matt__ on 2011-07-16
from my recent experience there are problems with hp-toolbox from the repos, it [requires python dependencies]("http://ubuntuforums.org/showthread.php?p=11043172#post11043172") that are older than the ones in the current kernel and throws a hissy fit on install :P so the .run download is an easy way to fix it.
Maybe its been resolved in the last few days.

---

### Post by ddjolley on 2011-07-16
> that printer will work perfectly once you have installed HPLIP with its gui toolbox

It sounds like you have the solution.  I'm just not sure what I'm doing.  We are using Ubuntu 11.04.  When I went through the procedure that you described to do the download I got a message indicating that the desired software was also available in the Ubuntu Software Center.  Sure enough, the Software Center seems to have "HP Linux Printing and Imaging System" and HPLIP toolbox.  Which of these do I need; or, do I need both?

Then, I'm tying to get a feel for what I am doing.  Then, to print do I no longer use "File Print"; or, what exactly do I need to do to print?

Thanks so much.  I'd really like to get this person setup using Ubuntu.  I think that once she gets started using Ubuntu her interest in the Mac will face pretty rapidly.  However, printing is important to her and I know that I will not be able to win her over unless I can get the printing thing to work.

Thanks for the input.

            ... doug

---

### Post by ddjolley on 2011-07-16
> why don't you consider investing in a dedicated network print server?

All in due time.  Right now my objective is to get this person converted to Ubuntu working with what she has so that she doesn't have to incur any front-end costs.  Once I have her converted, I'm sure that she would be receptive to such a suggestion.  Thanks for the input.

          ... doug

---

### Post by Matt__ on 2011-07-16
try installing the toolbox from software centre first, if it fails, then use the link I gave you.

I think the dependency error I got from it after update may have had something to do with the older version I had installed not purging completely.

---

### Post by ddjolley on 2011-07-16
> try installing the toolbox from software centre first, if it fails, then use the link I gave you.

OK.  It appears that the HP Imaging and Printing system is installed by default so apparently I only need to install the toolbox.  I'll try to install the toolbox package from the Software Center first.  If that fails, I'll download the file that you suggested and source it to install it.  (I always get a bit nervous about installing things that aren't packages.)

Then, when I'm done, I guess I am done.  I am not sure exactly what I have accomplished.  However, my big remaining question is that when I'm done with the installation and I want to print a document do I do that with File => Print as I normally would; or,or do I need to somehow use the toolbox to get the printing done?

Thanks.

           ... doug

---

### Post by Matt__ on 2011-07-16
you can print viewed images directly from the 'image' menu and text documents from the 'file' menu.
you can also print from the toolbox, buts its main use is settings, calibration, head cleaning, adjust gamma/brightness & check ink levels.

---

### Post by ddjolley on 2011-07-17
I finally got this issue resolved.  I want to share exactly what happened.

I never did get things to work right from the live CD.  Attempts to install HPLIP from the Software Center failed and I had problems getting the download while running from the live CD.  Then, I remembered that I can install Ubuntu along side of an existing Windows installation.  So, I did that and applied the Ubuntu updates.  Here's the important part:  Once I had Ubuntu installed on the hard disk with the updates in place, I was able to install HPLIP from the Software Center.  From there on it was a piece of cake.

Thanks to all who helped me with this challenge.  I'm hoping that we will be gaining a new Ubuntu user as a result.

             ... doug

---

