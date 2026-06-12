---
title: "Hi all Im new to ubuntu and i cant watch mpg(videos) files"
date: 2006-04-18
forum: General Help
---

### Post by salman16 on 2006-04-18
Hi all Im new to ubuntu and i cant watch mpg(videos) files, someone help me please!! any 1 knows why i cant watch videos I tryed to open with Totem Movie MAker Its giving me this error

 "Totem could not play 'file:///home/salman/Desktop/fener1denizli0.mpg"

There were no decoders found to handle the stream, you might need to install the corresponding plugins.

---

### Post by croak77 on 2006-04-18
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by damu on 2006-04-18
To sort out mulitmedia codecs, DVD issues and so on, I would really suggest you to install and use Automatix, or EasyUbuntu

If you want to install Automatix, go to Applications/Accessories/Terminal. It wil open a termainal window, copy and paste (go to edit/paste in the terminal window...don't use short cut "Ctrl V", it won't work) :

> wget [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)

and, once it is downloaded, to install it, copy and paste


> sudo dpkg -i automatix_5.7-3_i386.deb

Once the installation is done, just go to applications/System tools/Automatix

In Automatix, just tick any of the softwares, functionnalities that you need, and click OK ...let Automatix do the job for u...that's it, u should be sorted!

---

### Post by Tsm on 2006-04-19
A good idea would be to go- 

System->Help->Ubuntu 5.10 Starter Guide->Applications->Music and Movies

Helps with pretty much all multimedia codecs! :D

---

### Post by salman16 on 2006-04-19
Its working now i can watch videos and i can listen mp3's thanks for your helps;)

---

### Post by lshawmd on 2006-04-23
[QUOTE=damu]To sort out mulitmedia codecs, DVD issues and so on, I would really suggest you to install and use Automatix, or EasyUbuntu

If you want to install Automatix, go to Applications/Accessories/Terminal. It wil open a termainal window, copy and paste (go to edit/paste in the terminal window...don't use short cut "Ctrl V", it won't work) :



and, once it is downloaded, to install it, copy and paste




Once the installation is done, just go to applications/System tools/Automatix

In Automatix, just tick any of the softwares, functionnalities that you need, and click OK ...let Automatix do the job for u...that's it, u should be sorted![/QUOTE]
Hi folks - brand newbie.  Trying to install Automatix.  What am I doing wrong????

lshawmd@Home:~$  wget [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)
--10:36:03--  [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)
           => `automatix_5.7-3_i386.deb'
Resolving beerorkid.com... 208.97.133.175
Connecting to beerorkid.com|208.97.133.175|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
10:36:03 ERROR 404: Not Found.

---

### Post by damu on 2006-04-23
The new version of Automatix is 5.8-1

so try : 

> wget [http://beerorkid.com/automatix/automatix_5.8-1_i386.deb](http://beerorkid.com/automatix/automatix_5.8-1_i386.deb)

;)

---

