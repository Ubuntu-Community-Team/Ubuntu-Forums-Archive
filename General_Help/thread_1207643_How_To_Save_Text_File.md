---
title: "How To Save Text File?"
date: 2009-07-08
forum: General Help
---

### Post by antdgar on 2009-07-08
I'm trying to edit httpd.conf for a web server.

How do you save the file in terminal using vi?

---

### Post by ktmom on 2009-07-08
to get to the vi command line use the colon character ":"  A lowercase "w" after the colon and a return will write the file.  A lowercase "q" after the colon will quit vi.

They can be combined thus ----  :wq

use "man vi" for more information

Although I've used vi in years past, I'm finding "nano" to be easier ;-)

---

### Post by nateperson on 2009-07-08
ZZ will usually work if all your doing is editing and saving.

Get yourself a vi cheat sheet, it will really help...

[http://www.lagmonster.org/docs/vi.html](http://www.lagmonster.org/docs/vi.html)  is the top one from google...

---

### Post by mbeach on 2009-07-08
and not that it matters tremendously, but you may find the following file of interest.

/usr/share/doc/apache2/README.Debian.gz

It outlines a description of the files with apache2 on Ubuntu/Debian.

---

### Post by antdgar on 2009-07-14
THIS IS MAKING ME CRAZYYY

Can someone please tell me how I can edit a text file???? 
This has to be done in command line since it needs sudo privileges

I did:
sudo vi /etc/ssh/sshd_config

but you cannot edit it...

---

### Post by nikhilk on 2009-07-14
> **antdgar said:**
> Can someone please tell me how I can edit a text file???? 

My advise is do not use vi. Use nano instead
```
sudo nano /etc/ssh/sshd_config
```

---

### Post by masux594 on 2009-07-14
Neither 
```
sudo gedit /etc/ssh/sshd_config
```?

Sysc, A

---

### Post by nikhilk on 2009-07-14
> **masux594 said:**
> Neither 
```
sudo gedit /etc/ssh/sshd_config
```

Shouldn't gksudo used when launching a GUI application with root privileges? Or is this no longer recommended?

---

### Post by t4thfavor on 2009-07-14
its the same, you just get a gui prompt, and a darkened screen with gksudo. I recommend using nano, or gedit as neither are as cryptic as vi :)


Oh, you have to press "i" or insert in vi if you want to edit something. then esc :wq

---

### Post by nikhilk on 2009-07-14
> **t4thfavor said:**
> Oh, you have to press "i" or insert in vi if you want to edit something. then esc :wq

Sorry for the off-topic post but IMHO vi is really, REALLY productive after you tackle the initial, admittedly quite steep, learning curve :)

---

