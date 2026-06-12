---
title: "htaccess help"
date: 2010-08-03
forum: General Help
---

### Post by Four20 on 2010-08-03
Hello all 
First i wanna say thank you for ubuntu itself , as I have grown to hate the policies and practices of greed by microsoft. 

I have ubuntu installed with a lamp server. I have recently been under probe and attacks from hackers. The majority being located outside of the U.S.A.  I am only looking for U.S traffic so i want to know how i can only allow U.S. ip ranges with htaccess.  Any advice will be appreciated as I am noob. If you want to know why only U.S. I deal with firearms and cannot ship or service anything outside of the U.S.

---

### Post by chopinhauer on 2010-08-04
You have for example the [mod_geoip](http://www.maxmind.com/app/mod_geoip) module for Apache which allows you to deny access based on geographic position.

However denying access to Apache doesn't protect you from other types of attack. You should probably install an Intrusion Detection System like Snort.

---

