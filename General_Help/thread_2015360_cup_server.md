---
title: "cup server"
date: 2012-07-03
forum: General Help
---

### Post by Rakeshvijayan on 2012-07-03
Hi friends 

firstly sorry ,

I need to know what is the use of cup server , I didn't understand what is the use of this service I had read so many reference . I need a simple explanation from your mind ...if it is single sentence I am satisfied ....

---

### Post by cipherboy_loc on 2012-07-03
CUPS(Cup?) is the Common Unix Printing System, the default method of printing on Linux and Mac OS X (for the time being, word is Apple is looking to replace it). In other words, the basis of printing on Linux. Required if you want to print.

---

### Post by Rakeshvijayan on 2012-07-04
> **cipherboy_loc said:**
> CUPS(Cup?) is the Common Unix Printing System, the default method of printing on Linux and Mac OS X (for the time being, word is Apple is looking to replace it). In other words, the basis of printing on Linux. Required if you want to print.


if I install the cup server it will automatically dictate drive for all printer .I am using 12.04 lts is it have cups default .or we need to install them on new ubuntu ...Thanks

---

### Post by prshah on 2012-07-04
> **Rakeshvijayan said:**
> if I install the cup server it will automatically dictate drive for all printer .I am using 12.04 lts is it have cups default .or we need to install them on new ubuntu 

CUPS is installed by default. To access cups (for settings, admin, etc) open a browser, and enter the below in the ADDRESS bar```
http://localhost:631
```

You can also use [http://127.0.0.1:631](http://127.0.0.1:631) .

If you are asked for a username and password in CUPS (Eg, when performing admin tasks), use your username and password.

Most common printer drivers are already built in. If your printer is not recognized, check the manufacturers website for drivers or a "PPD" file.

---

