---
title: "Google Earth"
date: 2012-04-11
forum: General Help
---

### Post by tc101 on 2012-04-11
I installed Google Earth from the web site, but when I go back to the google earth page, it still comes up with a box saying "Install Google Earth"  and I can't get it to run.  I went to Synaptic Package manager and the box beside google earth is green, which I assume means it is installed.

---

### Post by Cpierce on 2012-04-11
I had issues with google earth as well. I read a bunch and found a solution that worked for me. 

Uninstall google earth, then open up a terminal and run this :

sudo apt-get install lsb-core

Then go back to the website and download the deb package and install it. I guess you need the lsb-core files for it to run properly.

---

### Post by woxuxow on 2012-04-11
the google earth repository of ubuntu is

[http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/)

---

### Post by tc101 on 2012-04-11
> he google earth repository of ubuntu is
[http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/)

I get:

404. That’s an error.

The requested URL /linux/earth/deb/ was not found on this server. That’s all we know.

---

### Post by tc101 on 2012-04-11
> Then go back to the website and download the deb package and install it. I guess you need the lsb-core files for it to run properly.

Thanks.  Should I use the 32 or 64 bit version?

---

### Post by oldos2er on 2012-04-11
> **tc101 said:**
> I get:

404. That&#8217;s an error.

The requested URL /linux/earth/deb/ was not found on this server. That&#8217;s all we know.

[s]You need to add the line ```
deb http://dl.google.com/linux/earth/deb/ stable main
``` to your sources.list.[/s]

---

### Post by oldos2er on 2012-04-11
> **tc101 said:**
> I get:

404. That’s an error.

The requested URL /linux/earth/deb/ was not found on this server. That’s all we know.

You need to add the line ```
deb http://dl.google.com/linux/earth/deb/ stable main
``` to your sources.list.

---

### Post by dcstar on 2012-04-12
> **oldos2er said:**
> You need to add the line ```
deb http://dl.google.com/linux/earth/deb/ stable main
``` to your sources.list.

**Don't.**

Google Earth no longer keep that repository up to date, and they have deleted all references to it from their download site.

That repository currently has the out of date 6.0.3 version while the current .deb downloadable from the Google Earth site is 6.2.1

---

### Post by dcstar on 2012-04-12
> **tc101 said:**
> Thanks.  Should I use the 32 or 64 bit version?

That depends totally on what version of Ubuntu **you** have installed - 32 or 64-bit.

---

### Post by oldos2er on 2012-04-12
> **dcstar said:**
> **Don't.**

Google Earth no longer keep that repository up to date, and they have deleted all references to it from their download site.

That repository currently has the out of date 6.0.3 version while the current .deb downloadable from the Google Earth site is 6.2.1

Thank you dcstar, I wasn't aware of that.

---

