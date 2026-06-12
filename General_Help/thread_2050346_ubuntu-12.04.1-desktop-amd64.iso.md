---
title: "ubuntu-12.04.1-desktop-amd64.iso"
date: 2012-08-30
forum: General Help
---

### Post by smithersnick on 2012-08-30
Hi,

I downloaded the iso, downloaded the wubi.exe. Ran the wubi exe file, got the username password bit set up, then the install failed.

I was not connected to the internet, since i have the files all extracted to the same folder as the wubi.exe.

I checked the log file i was referred to and read that image files are missing.

Any ideas where i might have goen wrong, i assume that the 600 odd mb i downloaded does not contain the image files hence the problem??

Thanks
Nicholas

---

### Post by CharlesA on 2012-08-30
Try reinstalling while connected to the internet. It probably needed to pull those files in but couldn't.

---

### Post by smithersnick on 2012-08-30
4 hours of download time, totals more than 10 hours and is going to break my isp cap.

oh well clearly i have no choice in the matter,

thanks

---

### Post by CharlesA on 2012-08-30
What is your download cap? You can use the same ISO, just be connected to the internet.

---

### Post by black veils on 2012-08-30
you surely need the .iso in one piece (not extracted).


EDIT:
dont forget you can order a disc instead [http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu)

---

### Post by smithersnick on 2012-08-30
I have a 10gb cap, i am already over 9gb, it may just stop. If so will have to redo the download and install next month

---

### Post by smithersnick on 2012-08-30
> **black veils said:**
> you surely need the .iso in one piece (not extracted).


The iso downloaded as a zip file and had to be extracted. Anyhow cap is reached, can only do this next month now anyhow

---

### Post by smithersnick on 2012-08-30
I will take a walk to their offices, its around the corner from my home, will do this in the morning rather.

---

### Post by CharlesA on 2012-08-30
> **smithersnick said:**
> The iso downloaded as a zip file and had to be extracted. Anyhow cap is reached, can only do this next month now anyhow
The ISO is meant to be burned to a cd, but you can also extract it and run, but you probably still need to be connected to the internet.

---

### Post by coffeecat on 2012-08-30
> **smithersnick said:**
> The iso downloaded as a zip file and had to be extracted.

The ISO file is not a zip. Depending how your Windows is configured, it sometimes wrongly identifies the ISO file as a zip. It was a mistake to extract it.

Simply place the unextracted ISO file in the same folder as the wubi.exe file and run wubi. My guess is that when the log mentioned a missing image file, it was referring to the ISO file that it couldn't find.

---

