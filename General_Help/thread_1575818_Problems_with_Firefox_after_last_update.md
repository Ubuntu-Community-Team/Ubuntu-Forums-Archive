---
title: "Problems with Firefox after last update"
date: 2010-09-16
forum: General Help
---

### Post by rva1945 on 2010-09-16
Ubuntu 9.10.
 
After last update, two days ago, I started to have problems when surfing the Web. Any site I wish to visit, most of the times I have to try twice, first I get the typical warning when the site is not available or I'm not connected to the Internet, then I click on Try again or F5 and the page is loaded.
 
The same with any link in the pages I visit.
 
I tried changing the proxy settings, No proxy or Autodetect, but to no avail. 
 
It seems as if the timeout is set to a few milliseconds (and I didn't find where to set it), because the message appears almost instantly.
 
If I boot in WXP, I don't have any problem.
 
I'd appreciate any help.

---

### Post by lovinglinux on 2010-09-16
Have you tried to disable ipv6? See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

---

### Post by rva1945 on 2010-09-16
> **lovinglinux said:**
> Have you tried to disable ipv6? See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

Thanks, but it didn't work. And it seemed to get worse (so I reset that value).

I get this (immediately) when trying to surf any page or link:

**Unable to connect**

Firefox can't establish a connection to the server at (any page)

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.
    *   If you are unable to load any pages, check your computer's network
          connection.
    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.
Try again

I click on Try Again once, sometimes twice or three times until it works.

---

### Post by lovinglinux on 2010-09-16
Try a different DNS server, like Google DNS and verify if your router MTU is set to 1492.

---

### Post by rva1945 on 2010-09-16
> **lovinglinux said:**
> Try a different DNS server, like Google DNS and verify if your router MTU is set to 1492.

 Ok, but please now tell me how to do it.

---

### Post by lovinglinux on 2010-09-17
[http://www.omgubuntu.co.uk/2010/09/how-to-switch-to-opendns-in-ubuntu-for-faster-browsing/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg!+Ubuntu!%29](http://www.omgubuntu.co.uk/2010/09/how-to-switch-to-opendns-in-ubuntu-for-faster-browsing/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg!+Ubuntu!%29)

---

### Post by saxonjf on 2010-09-18
hey lovinglinux, I actually saw that OMGUbuntu page, but the weird thing is that when I try to add the DNS servers (208.67.222.222, 208.67.220.220) in the IPv4 settings, the APPLY button won't activate, leaving me unable to continue.

Any ideas?

---

### Post by lovinglinux on 2010-09-18
> **saxonjf said:**
> hey lovinglinux, I actually saw that OMGUbuntu page, but the weird thing is that when I try to add the DNS servers (208.67.222.222, 208.67.220.220) in the IPv4 settings, the APPLY button won't activate, leaving me unable to continue.

Any ideas?

I'm not on Ubuntu right now, but have you configured the gateway? I think it won't activate until you fill all necessary fields.

---

