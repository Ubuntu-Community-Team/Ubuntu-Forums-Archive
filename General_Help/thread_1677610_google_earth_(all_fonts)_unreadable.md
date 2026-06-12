---
title: "google earth (all fonts) unreadable"
date: 2011-01-29
forum: General Help
---

### Post by irwan_up on 2011-01-29
can anyone help me how to solve my google earth problem ?
it was all fine, but this just happens today :( 
i'm using ubuntu 10.10.
thanks[U]

[[img]http://www.freeimagehosting.net/uploads/b54d54afb3.png[/img]](http://www.freeimagehosting.net/)
[/U]

---

### Post by rickbrice on 2011-01-29
Same problem. Recent builds of Ubuntu and recent builds of GE 5.2 and 6. Fonts  are unreadable. Many old bug fixes out there, but nothing works. I dusted off the windoze machine. It still works.

---

### Post by irwan_up on 2011-01-31
i found this link [http://www.google.com/support/forum/p/earth/thread?tid=60e399d9f613c8b8&hl=en](http://www.google.com/support/forum/p/earth/thread?tid=60e399d9f613c8b8&hl=en), and i followed every steps in it. it fixes all the fonts, but makes google earth crash :confused: (google earth always close itself). any solution for us please ?

---

### Post by dmitry424 on 2011-01-31
I had the same problem when I installed Ubuntu 10.10. I searched how to solve it, but since I didn't find any advice that worked more or less without exceptions, I simply decided to live with bad fonts. 

Today I launched GE and found there is no more problem with fonts. Most probably, this is because yesterday I installed additional fonts to my system. 

I think, "step 1" of
[http://tutorial.downloadatoz.com/install-microsoft-text-fonts-in-ubuntu-10-10.html](http://tutorial.downloadatoz.com/install-microsoft-text-fonts-in-ubuntu-10-10.html)

should solve the problem (I installed "msttcorefonts" with apt-get). Probably, it will be also necessary to perform "Method 2" from here,
[http://www.oooninja.com/2008/01/calibri-linux-vista-fonts-download.html](http://www.oooninja.com/2008/01/calibri-linux-vista-fonts-download.html)

Hope this will help.

---

### Post by ElrohirMacBeorn on 2011-02-06
I had the same problem and solved it a minute ago: 
the missing fonts are the microsoft-core-fonts (arial, times, etc...). Since the package ttf-mscorefonts-installer has been installed, they should have been available, but my font-installation-module told me otherwise. 

Simple removing and reinstalling ttf-msocorefonts-installer solved the problem

```
sudo apt-get remove ttf-mscorefonts-installer
sudo apt-get install ttf-mscorefonts-installer 
```

---

### Post by MinSung on 2011-02-21
> **ElrohirMacBeorn said:**
> I had the same problem and solved it a minute ago: 
the missing fonts are the microsoft-core-fonts (arial, times, etc...). Since the package ttf-mscorefonts-installer has been installed, they should have been available, but my font-installation-module told me otherwise. 

Simple removing and reinstalling ttf-msocorefonts-installer solved the problem

```
sudo apt-get remove ttf-mscorefonts-installer
sudo apt-get install ttf-mscorefonts-installer 
```

Thank you very much!:D I had the same problem and solved it with your instrucions.

---

### Post by RENOO on 2011-02-22
Thanks a lot, I was lost with all those wierd symbols !

---

### Post by tegwilym on 2011-03-26
Worked for me too!  Thanks for sharing the tip.  Google Earth is again usable!  ):P

---

### Post by W5WMW on 2011-04-20
[SIZE=3][FONT=Courier New]I hope someone will report this bug.  It shouldn't be too big of a problem for the maintainer considering the fix is just re-installing the "ttf-mscorefonts-install" package,[/FONT][/SIZE][SIZE=3][FONT=Courier New] but I don't know personally how to report this.[/FONT][/SIZE]

---

### Post by rgururaj on 2011-04-20
Nice google earth works on 64 bit ubuntu.

---

### Post by old_codger on 2011-05-12
I had to log-out and log back in again for it to work properly, ie. without corrupted text.

---

### Post by samMD on 2011-05-19
> **ElrohirMacBeorn said:**
> I had the same problem and solved it a minute ago: 
the missing fonts are the microsoft-core-fonts (arial, times, etc...). Since the package ttf-mscorefonts-installer has been installed, they should have been available, but my font-installation-module told me otherwise. 

Simple removing and reinstalling ttf-msocorefonts-installer solved the problem

```
sudo apt-get remove ttf-mscorefonts-installer
sudo apt-get install ttf-mscorefonts-installer 
```

Thank Thank You! Had this problem for a week looking through forums I did exactly what you posted plus logging in and out just to make sure and now the font is fixed in Google Earth Thanks !

---

