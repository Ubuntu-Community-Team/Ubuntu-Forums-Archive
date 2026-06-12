---
title: "office keeps crashing"
date: 2011-05-18
forum: General Help
---

### Post by BravoDelta65 on 2011-05-18
I have Libreoffice as the default install on Ubuntu 11.04. I use Writer and Calc daily, and both crash often. whilst the recovery service works, it's frustrating as it can happen a dozen times a day, and for no discernable reason.

I have attached an image of the syslog entry, which shows the problem lies with soffice.bin and names something called segfault.

Can anyone help?

---

### Post by cyrus_the_virus on 2011-05-19
Hi,

I have a similar problem, however I could not find an entry in the syslog. Furthermore, writer seems to crash with some particular documents only (when I create a new empty document it doesn't seem to happen). 

Since when do you have this problem? LibreOffice is never been really stable on Natty for me, but it was still "usable". However, yesterday some updates were installed for LibreOffice by the update-manager and since then it has become totally unusable.

The CPU usage goes up to 100% and I have to kill the process. This happens about every 5 minutes.

---

### Post by BravoDelta65 on 2011-05-19
I haven't had any problems with CPU used going up that high as a result of running LibreOffice.

I'm not convinced my issue is directly to do with LibraOffice of this version (11.04) version of Ubuntu, as I remember I had similar issues with openoffice under Ubuntu 10.10. Given that there has not been many people chiming in with help on this, I suspect the problem is not a common one and so issues may lie with individual  conflicts within the local environments or something.

---

### Post by cyrus_the_virus on 2011-05-19
I think I've solved my problem. I removed a package called *lo-menubar* which enables global menu support for Libre Office. This package isn't installed by default. If you have it installed, you can try to remove it. However, I don't think your problem is related to mine considering your previous post.

---

### Post by john j jumpsticks on 2011-07-08
I'm having the same problem with LibreOffice Writer. Sometimes It runs just fine but usually it crashes at least 2 or 3 times, arbitrarily, during use.

---

### Post by aeronutt on 2011-10-15
Libra was crashing infrequently with 11.04 for me, but now in 11.10, it's bad. Every 5-10 edits of a spreadsheet, and my system hangs. I have to power-off.

Anyone else?
Any ideas?

---

### Post by techvish81 on 2011-11-20
in my system with ubuntu oneiric libo writer  keeps crashing frequently , it just closes while typing .  really somebody should advice us what to do .. 
i have a question ? 
how is aby word , i have to create simple documents with some tables and images . is it usable or not?

---

### Post by techvish81 on 2011-11-20
bump

---

### Post by Johees on 2011-11-22
Using Kubuntu 11.10 
Same problem (seemingly) as OP, LibreOffice (spreadsheet) crashes when I try to move a cell.
Syslog more or less the same: > xxx-desktop >> kernel >> [56403.127024] soffice.bin[26441]: segfault at 24 ip 00007fcab1ddfc68 sp 00007fca9f850e80 error 4 in libQtGui.so.4.7.4[7fcab1afa000+a8a000]

There seems to be a myriad of bugs logged around it, I'll have a look at them and see if I can make any sense out of them.

PS: I see that I don't have the "actual libreoffice" packages installed, only the openoffice transitional packages that are (I assume) openoffice reworked to libreoffice for kubuntu.
I'm removing all the openoffice packages and installing the "proper" Libreoffice packages from synaptic (on the repositories).
I'll let you know what the results are; I hope it is this easy to solve...

---

### Post by Jacobonbuntu on 2011-11-22
.....did you upgrade from another LO-version?
it may help if you removed the (invisible) .libreoffice-directory from your personal folder, forcing Libreoffice to rebuilt it. some of the settings-files may be corrupted.

---

### Post by digithal on 2011-11-22
Can anyone confirm the same issue when using libreoffice from it's [**ppa**]("https://launchpad.net/%7Elibreoffice/+archive/ppa")?

---

### Post by Jacobonbuntu on 2011-11-22
> **digithal said:**
> Can anyone confirm the same issue when using libreoffice from it's [**ppa**]("https://launchpad.net/%7Elibreoffice/+archive/ppa")?

nope, I downloaded the latest version of LO (deb), removed the old version completely, had a lot of issues, crashes, until I deleted the .libreoffice directory. never had one issue since.

---

