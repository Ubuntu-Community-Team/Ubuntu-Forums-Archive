---
title: "Apache2 vitrual hosts"
date: 2011-12-19
forum: General Help
---

### Post by louis vitton on 2011-12-19
Hey guys,

I am having some issues with the apache2 virtual hosts.
I appear to have set them up correctly but when i try and go to the sites it displays the default index.html page on it.

the root for the subdomains i am using the vitrual hosts for it
root/subdomains/sub1

this is ubuntu 11.04

---

### Post by matt_symes on 2011-12-20
Hi 

Can you post what you have done so far, including all files you have edited ?

Kind regards

---

### Post by mikaelcrocker on 2011-12-20
Do you have this locally on the same server?  You may want to edit your etc/hosts file.

This is for setting up Munin, but I think it still touches on Apache 2 virtual hosts
[http://www.debuntu.org/how-to-monitoring-a-server-with-munin-p2](http://www.debuntu.org/how-to-monitoring-a-server-with-munin-p2)

Hope this moves you further to your goal.



-Mike

---

### Post by louis vitton on 2011-12-23
Hey,

Sorry i have been away for the Christmas period with no internet :(

I created new files for each of the subDomains i wished to use in sites-available and filled in the details.
I edited the apache config file adding in VirtualNamedServers to make it look for them and when i did this the first virtual host worked only and took over all defaults for apache so instead of seeing the standard welcome html no matter what i hit eg one of the subdomains or the main domain it still displayed it.

Atm i have changed all configurations back to the way apache2 comes so that the subdomains still exist but are not been used atm.

---

