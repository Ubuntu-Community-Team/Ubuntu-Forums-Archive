---
title: "Virtualbox"
date: 2009-09-23
forum: General Help
---

### Post by HalfCrackedTech on 2009-09-23
Virtualbox will not install guest additions.  I have tried restarting and reseting the box but nothing any help?

---

### Post by bmorency on 2009-09-23
what OS are you using as the guest? I ran into a similar problem with a windows guest. I ran virtualbox from the command line and when I tried to install the guest additions it told me it couldn't find the file it needed so i had to download the gzip file and put it the right folder.

But if you have a linux guest it could be something different.

---

### Post by Chronon on 2009-09-23
With Windows guest I believe I was able to simply download the guest additions software from within the guest and install.  For linux guests I have always been able to just select "install guest additions" from the drop down menu at the top of the virtual machine window.  This seems to download and mount an .iso containing the guest additions software.  Then just run the appropriate script from inside of the guest.

---

### Post by HalfCrackedTech on 2009-09-23
I got it fixed i forgot to unmount my cd/dvd rom

---

