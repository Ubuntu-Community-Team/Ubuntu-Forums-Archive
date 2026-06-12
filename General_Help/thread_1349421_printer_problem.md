---
title: "printer problem"
date: 2009-12-08
forum: General Help
---

### Post by Wim De Winter on 2009-12-08
Hi all. My printer is behaving very weird. It keeps on feeding paper: it takes a paper from the tray and just rolls it through. Then another and another and so on. The CUPS-gui tells me this:

> 	Description: Standaard Printer HP DeskJet 615C
Location: Desktop Wim
Printer Driver: HP DeskJet Series, 1.3
Printer State: idle, accepting jobs, published.
Device URI: file:/dev/lp0 

I've been doing some looking-up on the internet, but found nothing. I don't know what's wrong. Some more information that might be useful:

```
lpq
``` gives:
> lp is ready and printing
Rank   Owner      Job  Files                                 Total Size
active wim        0    (standard input)                      802458 bytes

```
cat patch-lp > /dev/lp0
``` gives:
> bash: /dev/lp0: Device or resource busy

```
lsmod | grep lp
``` gives:
> lp                     12324  2 
parport                37832  3 ppdev,lp,parport_pc
```

ls -la /dev/lp*
``` gives:
> crwxrwxrwx 1 root lp 6, 0 Dec  8  2009 /dev/lp0

All this MIGHT be the result of me trying to print a pdf file a while back. That didn't work. I just turned off the printer back then. But now, during boot with the printer turned on, it just starts feeding paper from the moment the line with "lpd" shows up in the boot log. I'd like that to stop. Can someone help?

---

### Post by Tamlynmac on 2009-12-08
I've had similar problems with my HP all-in-one, until installing [this]("http://hplipopensource.com/hplip-web/install.html") driver directly from HP.

I used the installation wizard and after the completion of installation I rebooted both my PC and my printer. Since that time I've had zero problems with my HP printer.

Good Luck.

---

### Post by Wim De Winter on 2009-12-09
Thanks for your answer, but I don't think hplip is the problem. My printer, an old DeskJet615C, used to work in both older and newer versions of ubuntu with the repository hplip installed. I think the problem has something to do with me trying to print that pdf. That did not work and I think printer and/or parallel port and/or system are in some kind of loop I can't seem to get out of...

---

### Post by Tamlynmac on 2009-12-09
> Wim De Winter

OK - Good Luck. Sorry I couldn't help.

---

### Post by JKyleOKC on 2009-12-09
> **Wim De Winter said:**
> All this MIGHT be the result of me trying to print a pdf file a while back. That didn't work. I just turned off the printer back then. But now, during boot with the printer turned on, it just starts feeding paper from the moment the line with "lpd" shows up in the boot log. I'd like that to stop. Can someone help?I suspect that you've got an instance of a problem I encountered often while trying to develop some graphics programs nearly 20 years ago! If you do, here's what is happening:

The PDF file was sending its content to your printer as a graphics bitmap rather than as text; your "lpq" report showing more than 800,000 bytes in the current job tends to confirm this. When you turned off the printer, that forced an error but did NOT cancel the job. Now, each time you boot up, the printer comes up in text mode -- and automatically tries to start the aborted job over. Apparently the bitmap has a lot of bytes with binary value of 12, which in text mode means "eject the page and start a new one."

To stop it you need to force cancellation of the aborted job; I'm not familiar enough with all the CUPS commands to tell you how to do this but with this information I'm sure someone else will give you the details. Back in 1992 I was doing the work in Windows 3.1 and it was necessary to open the printer control dialog, "pause" the print job while it was still spitting paper, then "cancel" the job to get the queue cleared. I think the same sequence should work with CUPS but don't know the exact commands/buttons/options to do so...

---

### Post by plucky on 2009-12-09
> To stop it you need to force cancellation of the aborted job; I'm not familiar enough with all the CUPS commands to tell you how to do this but with this information I'm sure someone else will give you the details. Back in 1992 I was doing the work in Windows 3.1 and it was necessary to open the printer control dialog, "pause" the print job while it was still spitting paper, then "cancel" the job to get the queue cleared. I think the same sequence should work with CUPS but don't know the exact commands/buttons/options to do so...


Open firefox and input ```
http://127.0.0.1:631/jobs/
``` which will open the jobs page in the CUPS interface.You should then be able to delete the job.

Good Luck

---

