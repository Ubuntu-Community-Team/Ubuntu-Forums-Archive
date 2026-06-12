---
title: "Canon PIXMA MG4100 Series Printer Driver"
date: 2012-04-09
forum: General Help
---

### Post by Hankers on 2012-04-09
Has anyone found a printer driver for the Canon PIXMA MG4100 Series printer that will work with Ubuntu 12.04?

---

### Post by Hankers on 2012-04-10
I take it the crickets means no one has found or knows of a driver that will work with this printer.

---

### Post by xc3RnbFO8P on 2012-04-10
Have you tried to connect the printer?
This printer should work according to this (if you are using 12.04 beta):
[https://answers.launchpad.net/ubuntu/+source/cups/+question/191711]("https://answers.launchpad.net/ubuntu/+source/cups/+question/191711")

---

### Post by Hankers on 2012-04-10
Have tried printing wireless only. Selecting any of the other Canon MG series drivers will only print a blank page. Using a Generic Postscript driver will print but not centered on page correctly.

---

### Post by xc3RnbFO8P on 2012-04-10
You could try this:
sudo add-apt-repository ppa:michael-gruz/canon  
sudo apt-get update

sudo apt-get install Canon MG4100
or
sudo apt-get install Canon MG4100 Ubuntu Driver

---

### Post by Hankers on 2012-04-10
Thanks but get "unable to find driver".

---

### Post by Hankers on 2012-04-21
It would appear that selecting the Canon PIXMA MG3100 printer driver will print in B&W only. Better than nothing until someone comes up with a proper driver.

---

### Post by Nath A on 2012-04-22
you may find a driver for lnux on cannon's website :- [www.cannon-asia.com](www.cannon-asia.com)
I did the same for my cannon image class printer for ubuntu 11.10

---

### Post by Hankers on 2012-04-29
> **Nath A said:**
> you may find a driver for lnux on cannon's website :- [www.cannon-asia.com](www.cannon-asia.com)
I did the same for my cannon image class printer for ubuntu 11.10

Found a driver on the canon asia site.

IJ series 4100 linux driver works

Thanks

---

### Post by lorqvonray on 2012-05-13
[www.canon-asia.com](www.canon-asia.com) had a MG3100 series driver that works perfect with my MG3120 wireless printer!

Thanks for the link! (although the link above is broken/wrong)

---

### Post by scottbomb on 2012-08-03
Where did you guys get the drivers for this? I'm searching canon-asia.com and I can't find anything for MG3120 or IJ series 4100. I have the 3120 but it only prints in b/w, not color. This printer is going back to the store if it won't print color.

---

