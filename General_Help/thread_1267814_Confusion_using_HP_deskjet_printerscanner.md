---
title: "Confusion using HP deskjet printer/scanner"
date: 2009-09-16
forum: General Help
---

### Post by DavidFourer on 2009-09-16
I hope this story shows why Linux is sometimes hard to use, especially for non-expert desktop users.

I just got my new HP deskjet F4480 all-in-one printer/scanner working.  The open source drivers and front-ends give full support for this inexpensive printer.

The drivers supplied with Ubuntu 9.04 were a little out of date.  Once I installed newer drivers, everything worked automatically.  An HP Device Manager appeared in my Applications>Accessories menu.  From there I could launch Xsane and run the scanner, with full support.  Every kind of printer setting, head cleaning, testing, were available from the device manager.  Applications like Open Office showed the new printer in the print menu.  What more could I want?

However, what should have been a simple plug-and-play kind of deal turned into hours of work.  Cups tried to install my printer, but didn't list my model.  I chose an older similar model and went on to try the scanner.  Xsane said no device found.  I went to an xsane web site, where I learned that sane is the driver side of Xsane.  At the Sane web site, I looked up supported printers.  None of the HP deskjet printers were listed at all, either supported or unsupported.  

I went to the main HP web site and naturally I learned that Mac OS X and Windows are supported.  

I installed something called "IRC Chat Gnome" and visited an IRC channel called #sane.  No one was home.  I joined a listserv for sane (scanner access now easy) development and posted a question about this.  I got a reply directing me to a web site for HPLIP, which stands for "Hewlet Packard Linux Image and Printing"  It seems that HP is actively involved in making the drivers.  I found drivers for just about every HP printer ever made.  I also learned that these were already installed by default on Ubuntu.  

Next I went to a question-and-answer page that determined if my installed package of drivers was up-to-date.  The Ubuntu-approved (and Synaptic installed) software is so often behind the latest release.  The HPLIP site reported that my Ubuntu approved drivers supported my deskjet F4480.  I did not need to update hplip drivers.  I looked in Synaptic Package Manager and found something called hplip-gui, not installed.  I could see not harm in that so I installed it.  I also started a search for help files.  

The best FAQ page was an html file on my hard drive.  I discovered it kind of by accident.  I did some very detailed investigation on the terminal, and learned a few things.  I thought I might post all my information on the the sane developer mail list and see if I could get some help.  Stuff about USB ports and reported devices--but all that turned out to be irrelevant.  

I took a rest and then went back to the HPLIP web site.  snooping around, I found a list of products that differed from the information I found earlier.  It said I needed a newer driver download.  HPLIP offered an install script that worked perfectly.  It was quite a lot of detail, running automatically for maybe 10 minutes, adding compile-time dependencies, compiling source, installing.  The script instructed me to re-boot, start the printer, and run HP-setup in a terminal.  

Well that's it.  Everything is working perfectly.  As I said, the printer control front-end and Xsane front end are very very nice.  Support for the printer appears complete. 

---David

---

### Post by hansdown on 2009-09-16
Hi DavidFourer.

Glad you got it working. Nice job.

I think it's great that HP decided to supply drivers foe linux; so many other printer companies don't.

Most HP printers i've bought work the first time it is turned on.

Very new printers may not work right away, if the version of ubuntu was released 6 months before the printer was released.

Good work on getting it going.

---

### Post by dannyman on 2009-10-05
Thanks for this note about your experience.  My Canon i250 does not work at all well with Ubuntu and a lot of it seems to stem from Canon not making things easy.  I'll jump through a few hoops if need be with 9.10 beta but its good to hear that at the end of the day, this MFC works for you.

-danny

---

### Post by colin.p on 2009-10-05
I had some problems getting my wireless Officejet 6500 E709n to get recognized, then when I got that fixed, it kept losing the connection.
However, after a few days and several postings to various newsgroups, it works like a champ. I find that the HP Device Manager works a whole lot better in Jaunty, than the windows version on my wife's Vista Laptop.
It took awhile, but I knew that sooner or later I would be able to get it working.
Yup, a whole lot better than the Lexmark X1185 it replaced;)

Colin

---

### Post by superzorro on 2009-11-24
I also had the same problem with the HP F4480, and got to this post looking for an answer.

For those who also will end up here, I just did what you did, however I think it was pretty straight forward. Just download something and every thing is pretty simple and automatic. Obviously this should be just plug and play.

Anyway you forgot to mention the webpage for the HPLIP wizard, so for anyone that is having a hard time it is:

[HPLIP wizard]("http://hplipopensource.com/hplip-web/install_wizard/index.html")

There you select your distro, mine is 9.04 and afterwards it stated that it was already supported; I continued selected next until I got to the page where you download the file. Download it and just follow the instructions of that page.

At the end you will have your printer working. 

Hope someone find this useful.

---

### Post by pmooney78 on 2010-01-29
> **superzorro said:**
> I also had the same problem with the HP F4480, and got to this post looking for an answer.

[...] 

Hope someone find this useful.

I did. Thank you very much, Superzorro!

---

### Post by DavidFourer on 2010-01-29
In Karmic/9.10, the pre-installed drivers are version 3.9.8, which should include the HP Deskjet F4480.  If you are running the latest version of Ubuntu, I think it will plug in and go.

---

### Post by mscir on 2010-01-31
Thanks very much for this very useful post. A buddy of mine owned an XP laptop that refused to boot after the SD Cardreader port light remained on (m/b problem?) and after we tried disabling the port and a few other things XP still hung during boot. I talked him into installing Ubuntu before buying a new laptop and now he's happy as can be. He needed scanner support for his home office, and your post was just what the doctor ordered. Thank you for giving us the benefit of your persistence.

---

### Post by BentSlightly on 2010-02-12
I got the printer working almost immediately, but the scanner is a complete mystery. Even with the updated drivers. 

Anyone got some advice on this error?

[Failed to open device  v4l:/dev/video0': Invalid argument.]

---

### Post by Yoknapatawpha on 2010-07-10
just set up an old 600MhZ Dell Dimension PIIm with half a gig of ram and a coupla' old hard drives, for my mom.  
relied on the reputation of HP working with Linux.
Installed Xubuntu 9.04.
Searched for help.
Sucess!

Thank you Ubuntu Community. :KS

---

