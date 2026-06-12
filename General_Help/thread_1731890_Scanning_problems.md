---
title: "Scanning problems"
date: 2011-04-17
forum: General Help
---

### Post by Enigmaman on 2011-04-17
I am running Maverick Meerkat and having problems using XSane and Simple Scan. I have meanwhile installed HPLIP. 

I get various error messages, such as "Unable to connect to scanner" por "I/O error" or "Failed to open device:hpaio:/usb/officejet_4200series?serial=CN482FHOYJ. Error during device I/O". 

Raely, totally randomly, it will work.

Is this some kind of USB port problem? This-all-i-none prints OK so I don;'t understand what's goingon.

Any ideas, please?

---

### Post by Leppie on 2011-04-17
did you select the correct drivers when adding your printer?
you're talking about an all-in-one printer, but the system claims it's an officejet here:
> **Enigmaman said:**
> "Failed to open device:hpaio:/usb/**[COLOR=Red]officejet[/COLOR]**_4200series?serial=CN482FHOYJ. Error during device I/O". 


if changing the drivers does not work, you could try downloading the latest hplip version here: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by Port 80 on 2011-04-18
Is it possible to get a CanoScan to work in 10.10?  I have tried to no avail.

Thanks.

---

### Post by Enigmaman on 2011-04-18
How do I install new drIvers please?

---

### Post by Leppie on 2011-04-18
there is a step by step walkthrough: [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

### Post by Enigmaman on 2011-04-26
Thansj
ks - I am getting an error message:  "Can't open hplip-3.11.3a.run"

when type the command sh hplip-3.11.3a.run

---

### Post by Leppie on 2011-04-28
into which folder did you save the script?
if it was the download folder, you have to amend the command like this:
```
sh Download/hplip*.run
```

---

### Post by Enigmaman on 2011-05-01
Thanks - I had thought of that and copied the downloaded HPLip files to the Desktop.

There must be some other reason why this is not working, but I cannot see what.

I though the beauty of Linux was that it automatically scanned for devices and installed them? This is getting messy.

---

### Post by Leppie on 2011-05-02
> **Enigmaman said:**
> Thanks - I had thought of that and copied the downloaded HPLip files to the Desktop.

There must be some other reason why this is not working, but I cannot see what.
what is the exact error message? i think the message is a bit longer than just "Can't open hplip-3.11.3a.run"


> **Enigmaman said:**
> I though the beauty of Linux was that it automatically scanned for devices and installed them?
well, if the drivers are available. it kind of works like the windows pre-installed drivers, you won't find drivers for all devices.

---

