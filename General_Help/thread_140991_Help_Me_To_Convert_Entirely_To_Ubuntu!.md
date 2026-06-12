---
title: "Help Me To Convert Entirely To Ubuntu!"
date: 2006-03-07
forum: General Help
---

### Post by sooqing on 2006-03-07
Hi Everybody! 

I had been running Ubuntu for some time already. I am unable to get rid of my Windows XP since my printer, Epson EPL-6100L, though Ubuntu 5.10 claimed to support it (its in the driver list) and was even able to detect my printer, does not work at all (unable to print test page, etc.. with no error messages). I have to boot to Windows each time I wish to print something. 

I can print in Fedora Core 3 since there is a driver in .rpm format and I can install it.

Can anyone help me to get rid of Windows once and for all so I will only have my lovely Ubuntu on my PC! \\:D/ 

PS: Will the coming version of Ubuntu in April helps?

---

### Post by meborc on 2006-03-07
have you tried installing the .rpm driver in ubuntu? using alien you can convert it to deb package...

---

### Post by taurus on 2006-03-07
How exactly did you configure your Epson printer anyway?  Maybe if you give step by step, I am sure somebody can figure out what's wrong with it...  ;)

---

### Post by BarfBag on 2006-03-07
On my system, converted .rpm files don't always work right.  I think it's worth a try, though.

1.  Check to see if you have Alien installed.  Do so by opening a terminal window, and typing:

> sudo apt-get install alien

If it isn't already installed, it will install automatically.

2.  Download your .rpm package to your Home folder.

3.  Open up a terminal window, and type:

> sudo alien File Name.rpm

This will concert it to a .deb file.

4.  Then, all you have to type is:

> sudo dpkg -i File Name.deb

That will install the newly converted package.

Hope this helps!

---

### Post by sooqing on 2006-03-10
No, this doesn't work. Anymore ideas?

---

### Post by az on 2006-03-10
Someobody has writted a driver for this printer, but I do not know under what licence they have released it.  That may be why it is not in debian or ubuntu.

[http://linuxprinting.org/show_driver.cgi?driver=epl6100l&fromprinter=Epson-EPL-6100L](http://linuxprinting.org/show_driver.cgi?driver=epl6100l&fromprinter=Epson-EPL-6100L)
[http://epsonepl.sourceforge.net/](http://epsonepl.sourceforge.net/)
[http://epsonepl.sourceforge.net/?page=howto](http://epsonepl.sourceforge.net/?page=howto)

---

### Post by sooqing on 2006-03-11
oh, thats where i gotten the drivers.. still, its doesnt work..  :(

---

