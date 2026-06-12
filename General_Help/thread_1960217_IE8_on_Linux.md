---
title: "IE8 on Linux"
date: 2012-04-17
forum: General Help
---

### Post by jebaearnest on 2012-04-17
Hi,

I need to install ie8 or ie 9 on ubuntu.
Is there a way to install it?

Thanks

---

### Post by QIII on 2012-04-17
You might be able to use Wine, but have a look at how well it works:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=25](http://appdb.winehq.org/objectManager.php?sClass=application&iId=25)

The other option would be to install a LICENSED, RETAIL copy of Windows in a virtual machine (using something like VirtualBox) and use it from there.

If I may ask, why do you need to install it?

---

### Post by Mark Phelps on 2012-04-17
You're not going to be able to install IE9 on Linux.  You may be able to install IE8, but the latest version that appears to install OK is IE7.

If you need to use IE9, you need to use MS Windows.

---

### Post by Frogs Hair on 2012-04-17
Even MS suggests not running any browser older than IE8 anymore.

---

### Post by ojdon on 2012-04-17
Web developers still need to test for IE users though. Which, I'm assuming, is why OP is asking how to run it under Linux. WINE is your best bet, to install simply search for WINE in the Ubuntu Software Centre. 

There used to be a browser based on IE's engine that came preinstalled with WINE, however I haven't used WINE in a long time so I don't know if it's still in the latest versions. Normally, IE users don't have much technical knowledge so they might not even know Internet Explorer needs updating every now and then.

---

### Post by mike555 on 2012-04-17
if you want to test your site in different browsers you can do it here;
[http://browsershots.org/](http://browsershots.org/)

---

### Post by Mark Phelps on 2012-04-17
> **ojdon said:**
> Web developers still need to test for IE users though. Which, I'm assuming, is why OP is asking how to run it under Linux. WINE is your best bet ...

NO .. it is NOT! As I already mentioned, IE7 is the last version that installs OK.

Look at the page below from the WineHQ site for versions of IE:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=25]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=25")

And before anyone points out the Bronze ratings -- this means the app barely works at all -- NOT a situation you want when you're using that for testing.

The "best bet" for testing anything based on IE is STILL using MS Windows -- dual boot or virtualbox.

---

