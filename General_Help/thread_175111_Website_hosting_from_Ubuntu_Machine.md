---
title: "Website hosting from Ubuntu Machine"
date: 2006-05-12
forum: General Help
---

### Post by jflash on 2006-05-12
I am trying to run a website from my Ubuntu computer. It's main use would be to provide a way for me to access the programs I have running on my computer (Ubuntu Center, Webmin, etc.) I have Apache installed, but I have no clue how to use it. I know the basics of web design, but I have never run my own server. If anyone can help me out, I'd appreciate it. I mainly just need to know any further configuration of Apache necessary and where to put my files. Thanks!

---

### Post by encompass on 2006-05-12
If you have apache installed lets check if it is working right off...
goto your ipaddress... that is your local one if you have one.
Something like 192.168.0.1 in your browser. Anything?

---

### Post by jflash on 2006-05-12
Yes, I've checked and it works. I get the standard page for directories with no index page. The page lists a folder entitled "apache2-default". When I click on it, I get a page with the Apache logo telling me I have had a successful installation. I have an account set up with DynDNS, so you can go to jflash.homeip.net to confirm this if it would help.

---

### Post by henriquemaia on 2006-05-12
If you have the default install, your document root (the default page location) is  /var/www .

If you put an index page there, it will work as expected.

---

### Post by jflash on 2006-05-12
Worked perfectly, thanks.

---

### Post by jflash on 2006-05-12
Worked perfectly, thanks.

---

