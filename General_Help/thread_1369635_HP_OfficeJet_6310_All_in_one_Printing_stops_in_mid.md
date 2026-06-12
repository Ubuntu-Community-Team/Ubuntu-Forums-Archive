---
title: "HP OfficeJet 6310 All in one Printing stops in midway"
date: 2010-01-01
forum: General Help
---

### Post by mickcalcara on 2010-01-01
Hi,

I have had  good success with the HP OfficeJet 6310 printing and Karmic. However, recently when printing, the print job stops after a certain amount of pages ( when printing a multiple page document ). The first page almost always prints immediately.  This issue occurs with PDFs, OO Writer documents and OO Spreadsheet documents.  The printer status window on the printer shows "printing" and the print manager in Gnome shows printing. Sometimes the printing completes after several minutes. Other times I end up killing the job and powering down the printer.
Thanks..

---

### Post by mickcalcara on 2010-02-17
bump... I am still having this problem. I installed the HP Linux Imaging and Printing manager ( HLIP ) which I thought had helped but I am still having issues with print jobs completing.

---

### Post by robertneville777 on 2010-02-17
Hey dude! I have one of those all in one HP printers too (a C5580 photosmart). My problem: it was spitting out paper, but with a log of errors printed instead. So I went to "printers" and deleted it off the list, and reinstalled the printer drivers, using ubuntu's program. After I did that, everything worked fine.

So first off, you're wired right, USB? You're not connecting through bluetooth or LAN are you?

Secondly, did you install ubuntu's drivers for it, or did you go to HP's site and install them?

And one more thing. Is this a recent problem; did it work fine before and now it's acting up, or has it always been like this?

Okay...that's the best I can do for now. Let us know how it goes! Good luck!:D

---

### Post by mickcalcara on 2010-02-18
Thanks for the reply. to answer your questions:  

1. It is USB.
2. I have done both. I started off using installing the printer **without** HPLIP then after I had these problems I installed HPLIP.
3. I have had intermittent problems ( before Karmic ) but now they are more frequent. 

I always appears to print the first page without a problem. The second page gets half way complete before it stops. It then either never finishes or takes about twenty minutes and then  resumes.

---

### Post by philinux on 2010-02-18
> **mickcalcara said:**
> Thanks for the reply. to answer your questions:  

1. It is USB.
2. I have done both. I started off using installing the printer **without** HPLIP then after I had these problems I installed HPLIP.
3. I have had intermittent problems ( before Karmic ) but now they are more frequent. 

I always appears to print the first page without a problem. The second page gets half way complete before it stops. It then either never finishes or takes about twenty minutes and then  resumes.

How about trying to print each page on its own one at a time. It could be the printer.

Hard to diagnose.

---

### Post by robertneville777 on 2010-02-18
> **philinux said:**
> How about trying to print each page on its own one at a time. It could be the printer.

Hard to diagnose.

Hey good idea phil! :) Yeah mick I'd try that first. Try printing one page, and then if that goes fine print two. How many pages can it print before it starts acting up?

---

### Post by stuzzie20 on 2010-03-13
Found a solution!
Visited [http://hplipopensource.com]("http://hplipopensource.com")
Downloaded the correct and updated driver, followed the installer instructions.
Made sure i had all dependencies. Whamo! It was fixed.
What a nightmare it has been and now i'm done with it.

Hope this helps.

---

### Post by robertneville777 on 2010-03-13
Awesome, nice work! Mark this sucker as solved!

---

### Post by mickcalcara on 2010-03-16
I have the latest version of HPLIP and still have the issue.

---

### Post by cm.squared on 2010-03-27
I also have this problem with a hp officejet 6310.  It prints the first page of a document and stops partway through the second page.

I had the problem with hpijs 3.9.8 and now with the most recent driver from the hp website, hpcups 3.10.2

Is there any more information that I could provide that might help diagnose this problem?

---

### Post by nigels on 2010-08-17
Also broken for "HP Officejet 6300 Series, hpcups 3.10.6".
This printer used to work for previous Ubuntu versions, but not 10.4.

- Nigel

---

### Post by DrReaper on 2010-09-02
Same problem with the printing stopping.

I ended up using the LAN port on the printer instead of the USB and it is working now. No other fixes worked for me. I tried the HP Printer driver.

---

### Post by mickcalcara on 2010-09-02
I am still having this problem even with the latest drivers. What I notice is that when I go to the printer administration screen the hp officejet all in one printer ( during this issue ), the printer enabled box is unchecked. I simply check it and then it retries the print job that stopped. And it seems to be successful in completing.

---

### Post by hugoestr on 2010-09-14
I am having the same problem. I suspect that a recent update must have broken the driver since it was working well until a couple of weeks ago.

Update: I just got it to work. It seems that I needed to run sudo hp-setup program. After I finished, I ended up with two set of drivers: the older ones, that don't work, and new ones. After identifying which one was working, I got rid of the older ones.

---

### Post by nigels on 2010-09-22
Connecting the printer to the network solved the problem for me, in combination with installing the latest version of the driver from HP.  (not via a .deb)

- Nigel

---

### Post by hugoestr on 2010-12-04
Strange, the problem came back. Anyone else has any ideas on how to solve this?

---

### Post by United Records on 2010-12-11
I am having the same problem.  Some pages print fine, others just stop in the middle of the page.  And it's not consistent.  Sometimes a doc will print fine, but then if you print it again it doesn't work.  Seems like the driver is overflowing a buffer or something so print might work one time but then next time fails (even with the same document).  printer then has to be restarted in order for it to be able to print again.  fyi This printer always worked fine with Ubuntu 7, this problem started after upgrading to 10.04.

---

### Post by jfmoran on 2011-04-03
Re hp6310- I have this problem in spades-have tried two different systems using 10.10 and nothing works in ubuntu. Using PclinuxOS 2010 there is no problems with the printer. What does work is printing using 'lp'. Example:
$lp -d officejet_6300 anyfile.pdf. This seems to be because lp does not use cups backend. However, if u save a file from open office and then try to print it using lp it spits out pages of garbage and has to be powered off to stop. The only way with open office is to save a file as a pdf or text and then print it using lp. This is a bad problem as it does not seem to be addressed as one at all and this printer is damned nearly useless on ubuntu.

---

### Post by herdivet on 2011-04-20
I was fighting with this, and searching for solutions.  I tried reinstalling hplip, downloading it from the web, etc.

I was about to give up when I saw the recommendation to try going to [http://localhost:631](http://localhost:631) and adding the printer through the CUPS interface.  Nothing else worked, so I figured I'd try it.  Dunno why, but that fixed it for me.

The post is here:

[http://forums.linuxmint.com/viewtopic.php?f=51&t=25762&p=411191#p411191](http://forums.linuxmint.com/viewtopic.php?f=51&t=25762&p=411191#p411191)

Hope that helps.

As always, your mileage may vary.

---

