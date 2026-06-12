---
title: "Print jobs are extremely slow to print; CUPS log errors..."
date: 2010-06-01
forum: General Help
---

### Post by killabee44 on 2010-06-01
Guys,

I am  having an issue with my Lucid 10.04 new install and a Brother 2170w printer. The printer lights up but stays flashing. The printer status shows the que moving extremely slow (about 2% every 10-30 seconds). 

A big job will print some pages then as the que moves slooowly it will print more pages and then stop again and so on..

I read somewhere that it might be a permissions issue. Im not sure how to diagnose it though. Wish there was a utility I could run. 

This printer is a wireless network printer that prints fine from Jaunty and windows machines. 

Here is:  -l /usr/lib/cups/backend/lpd

```
-rwxr--r-- 2 root root 44056 2010-05-14 11:55 /usr/lib/cups/backend/lpd
robert@robert-desktop:~$ sudo service cups restart

```

Edit: Here are two errors I found in my cups error log at var/log/cups/error_log:

```
E [01/Jun/2010:14:21:47 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [01/Jun/2010:14:51:16 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
```

Thanks.

---

### Post by killabee44 on 2010-06-01
Ok, teh printer status seems to be stuck at: 

```
Printer state: Processing: Spooling LPR job, 11% completed...
```

Like I said, it seems to take a really long time to print just one page. 

Regular text files print fine. Almost anything else has a problem.

---

### Post by killabee44 on 2010-06-02
Ok, I finally have a fix thanks to johnny_vc...

It is really a workaround but it works so who cares.

> I think this a bigger issue than just with that printer, I found a workaround solution which is to reinstall the printer using :

Device URL : socket://IP_of_the_printer:9100

Make and Model : Generic PCL 5e Printer Foomatic/gutenprint-ijs-simplified.5.0

I did it through the CUPS web interface on Lucid 10.04 so it was slightly different.

1. Log on to the cups web interface: [http://localhost:631/admin]("http://localhost:631/admin") (for username and pw I used the sudo for this pc).

2. Select "**Add Printer**"
3. From "Other Network Printers:" I selected:** LPD/LPR Host or Printer **
4. under "Connection" put in: **socket://IP_of_the_printer:9100** (of course, substitute in the IP of your printer)
5. Name, description, location: fill those out as you wish without spaces
6. Sharing: I did not check this box.
7. Make: Select **Generic** and click Continue
8. Model: [B]Generic PCL 5e Printer Foomatic/hpijs-pcl5e (recommended)
[/B] (this model is the closest by name to what Johnny_vc told me to use. I figured mine is different because I'm using Lucid) 
9. Click "Add Printer" and you're done.

I hope this helps someone else. Good luck.

---

### Post by Andras888 on 2010-11-28
Thank you killabee44, this fixed my problems.

---

### Post by GOREMEISTER on 2010-12-14
Worked for me too on my Brother HL-2170W.

I just pulled up the properties of my printer and changed the driver to the Generic one listed above.


Thanks!

---

### Post by killabee44 on 2010-12-14
As I said before, I got this fix from somewhere else, but very glad it has helped some of you too.

---

