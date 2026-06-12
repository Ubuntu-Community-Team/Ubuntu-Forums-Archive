---
title: "Google Earth 6 can't start"
date: 2010-11-30
forum: General Help
---

### Post by Marzata on 2010-11-30
I installed Google Earth 6 on Ubuntu 10.04.1 LTS (lucid). After the installation I was not able to start Google Earth 6 neither from the menu, nor from the command line (on the same PC the old Google Earth 5 runs without problem). Any idea how to fix this problem? Thank you!

---

### Post by Marzata on 2010-11-30
Installing lsb-core fixed the problem:  

```
sudo apt-get install lsb-core
```

Now Google Earth 6.0.0.1735 (beta) works fine on Ubuntu 10.04.1 LTS (lucid). Thanks to: [http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html]("http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html")

---

### Post by dcstar on 2010-12-16
The Natty version of googleearth-package now has this new dependency included, so using it will automatically install it for anyone wanting to make their own googleearth package. It can be downloaded from here and should work on other Ubuntu releases:

[http://packages.ubuntu.com/natty/googleearth-package](http://packages.ubuntu.com/natty/googleearth-package)

---

### Post by Marzata on 2010-12-16
Thank you! Good to know that.

---

### Post by netgooroo on 2010-12-17
> **Marzata said:**
> Installing lsb-core fixed the problem:  

```
sudo apt-get install lsb-core
```

Now Google Earth 6.0.0.1735 (beta) works fine on Ubuntu 10.04.1 LTS (lucid). Thanks to: [http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html]("http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html")

Thanks for posting this..  helped out str8 away.  Been tryin to get GE to work for a couple days.  

This done the trick. 

Cheers!  :D

---

### Post by Marzata on 2010-12-19
Welcome! Cheers!

---

### Post by Foxcow on 2010-12-19
> **Marzata said:**
> Installing lsb-core fixed the problem:  

```
sudo apt-get install lsb-core
```

Now Google Earth 6.0.0.1735 (beta) works fine on Ubuntu 10.04.1 LTS (lucid). Thanks to: [http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html]("http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html")




Thank you!  That worked perfectly for me on 10.10 64-bit.

Also, I noticed that on the Google Earth site, one has the option to chose .deb or .rpm for in either 32 or 64 bit flavour.  No more .bin

---

### Post by Marzata on 2010-12-19
Sounds really nice. Thank you!

---

### Post by dcstar on 2010-12-20
> **Foxcow said:**
> 
.........
Also, I noticed that on the Google Earth site, one has the option to chose .deb or .rpm for in either 32 or 64 bit flavour.  No more .bin

I have updated the Wiki to reflect that:

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by odavyarmstead on 2011-01-07
Many thanks, worked immediately!

---

### Post by Marzata on 2011-01-07
Super!

---

### Post by jobsworth on 2011-01-14
Thank you all:-

sudo apt-get install lsb-core

It is so easy when you know how.


Now what about sendmail - postfix - dovecot - 
certificate signing?
That no doubt would be easy too if you know how only I don't.

And as for WUBI well forget it -
something to do with 2 ^ 32 = 4 gigabytes -
anyone remember windows 98 had a similar problem with 
large disks (>4GB).

:popcorn: now popcorn was a good game on windows 98.

---

### Post by Monrizzy on 2011-02-27
Awesome!!! Worked like a charm!

---

### Post by Kir_B on 2011-04-19
Thanks guys. You are truly awesome.

Kirby ):P

---

