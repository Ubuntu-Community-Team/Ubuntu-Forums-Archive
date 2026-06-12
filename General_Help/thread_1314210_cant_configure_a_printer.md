---
title: "cant configure a printer"
date: 2009-11-04
forum: General Help
---

### Post by ealvarado on 2009-11-04
I try Ubuntu 9.10 yesterday because the printer does not work under win so i resolved to boot with the ubuntu live cd, it work fine, the file i need to print resides on an ntfs partition but i can print the file without problems.
With this situation i decided to install ubuntu to the hard drive, when the installation process ends i try to configure the printer but the window to do this cant open, it shows like is minimized but the minimized icon go away
The printer is HP 710c conected with a parallel interface
What can i do

---

### Post by danill2008 on 2009-11-04
> **ealvarado said:**
> I try Ubuntu 9.10 yesterday because the printer does not work under win so i resolved to boot with the ubuntu live cd, it work fine, the file i need to print resides on an ntfs partition but i can print the file without problems.
With this situation i decided to install ubuntu to the hard drive, when the installation process ends i try to configure the printer but the window to do this cant open, it shows like is minimized but the minimized icon go away
The printer is HP 710c conected with a parallel interface
What can i do

Try System > Administration > Printing or go to CUPS ( [http://localhost:631/](http://localhost:631/) )

---

### Post by ealvarado on 2009-11-04
I do that
the problem is - the window is not opening at all-

---

### Post by danill2008 on 2009-11-04
I have no idea why it does that, maybe you must reinstall Ubuntu and see if that works...

---

### Post by hal10000 on 2009-11-04
> I do that
the problem is - the window is not opening at all-
Are you sure your cups is running?

```
sudo /etc/init.d/cups status
```
and, if it'd not running 
```
sudo /etc/init.d/cups start
```

---

### Post by nikgare on 2009-11-04
What happens if you run **system-config-printer** from a terminal window

---

### Post by Old Codger on 2010-08-10
> **hal10000 said:**
> Are you sure your cups is running?

```
sudo /etc/init.d/cups status
```
and, if it'd not running 
```
sudo /etc/init.d/cups start
```
Many thanks for the line code. It fixed the CUPS problem. When I still couldn't print. I reinstalled the printer and PRESTO--I could print!

---

