---
title: "Network printing problems"
date: 2012-10-05
forum: General Help
---

### Post by foxuser on 2012-10-05
Hi,

I have a HP printer connected to a router (USB).
I can print from Windows 7 and from Ubuntu 10.04 without any problem.
I can not print from Ubuntu 12.04. Everytime I print I have an error asking if the printer is on at the print queue .

I tryed everything I know to solve the problem but without sucess
I'm using IPP protocol

---

### Post by daslinkard on 2012-10-05
When you set up the printer with your PC did you verify the correct network IP addy for the printer?

---

### Post by foxuser on 2012-10-05
The printer is connected to the router (USB) and works well with Ubuntu 10.04 and win7.
I only have problems with Ubuntu 12.04, can not print from there.

---

### Post by daslinkard on 2012-10-05
How I have connected my HP printer in the past (multiple PC's/multiple times) was as follows:

1. Go to printers
2. Hit Add located below "There are no printers configured yet"
3. Select Network Printer
4. Select Find Network Printer
5. Enter in the IP addy for my printer in the "Enter device URI"
6. At this point in time it should find your printer and guide you through downloading the correct drivers for your printer.

Hope this helps you....

---

### Post by owise1 on 2012-10-06
You can also install HPLIP Tools from he software centre - It has network connected printer discovery and set up

---

### Post by daslinkard on 2012-10-06
Just wondering if you have been able to get this resolved?

---

### Post by foxuser on 2012-10-07
> **daslinkard said:**
> How I have connected my HP printer in the past (multiple PC's/multiple times) was as follows:

1. Go to printers
2. Hit Add located below "There are no printers configured yet"
3. Select Network Printer
4. Select Find Network Printer
5. Enter in the IP addy for my printer in the "Enter device URI"
6. At this point in time it should find your printer and guide you through downloading the correct drivers for your printer.

Hope this helps you....

This works in Ubuntu 10.04, in Ubuntu 12.04 does not work

I will try to find what is happening and will post the results

---

### Post by foxuser on 2012-10-07
> **owise1 said:**
> You can also install HPLIP Tools from he software centre - It has network connected printer discovery and set up


I will try that

---

### Post by daslinkard on 2012-10-07
> **foxuser said:**
> This works in Ubuntu 10.04, in Ubuntu 12.04 does not work

I will try to find what is happening and will post the results

Interesting as 12.04 is what I have on my desktop PC's that are hooked into my HP Network Printer.

---

### Post by foxuser on 2012-10-07
Finally, working!!!

The cups server in the router is a lower version than Ubuntu 12.04
The path to the printer needs to be:


[B]ipp14://xxx.xxx.xxx.xxx:631/printers/OfficejetJ5700series

[/B]The 14 after the ipp gives the compatibility
is not possible to see the version installed in the router but I think will be 1.4.x
[B] 

Thanks for your help ;)
[/B]

---

### Post by daslinkard on 2012-10-07
> **foxuser said:**
> Finally, working!!!

The cups server in the router is a lower version than Ubuntu 12.04
The path to the printer needs to be:


[B]ipp14://xxx.xxx.xxx.xxx:631/printers/OfficejetJ5700series

[/B]The 14 after the ipp gives the compatibility
is not possible to see the version installed in the router but I think will be 1.4.x
[B] 

Thanks for your help ;)
[/B]
I'm glad you were able to get this solved!!  Any time you have any questions we are here for you!

---

### Post by foxuser on 2012-10-08
> **daslinkard said:**
> I'm glad you were able to get this solved!!  Any time you have any questions we are here for you!


Thanks

---

### Post by hurrican on 2012-11-19
If you are using windows 7 then you must go into network after doing that you must click on add a new printer. You must follow the instruction step by step. After doing that your printer will be share through network and will processing well.

---

### Post by wijit on 2013-02-01
For those who use Gnome desktop, the menu "Printers" under the on-off button may be useful.

---

### Post by sujitbikash on 2013-02-01
Now a days the world is like wire less and printing create problem.
how it create problem and why check it and it is very important to find out the error so that we can solve it easily.

---

