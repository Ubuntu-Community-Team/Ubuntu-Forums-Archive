---
title: "Open DNS updater on linux"
date: 2011-07-12
forum: General Help
---

### Post by anton706 on 2011-07-12
Hi I have OpenDNS set up on my router and openDNS updater on my windows 7(I'm dual booting) but I dont have it set up on my ubuntu 11.04 and I didn't found practical instructions which tell me how to make it work on linux all I found  was a script which does the same as openDNS updater for windows and mac but I dont know how to use it here is the script:
[http://bassmadrigal.com/blog/2008/08/opendns-dynamic-ip-update-script-through-linux/](http://bassmadrigal.com/blog/2008/08/opendns-dynamic-ip-update-script-through-linux/)

I'd appreciate it if someone will tell me how to make it work automaticlly just like in windows and mac.

---

### Post by oldos2er on 2011-07-12
Is this what you're looking for? [https://store.opendns.com/setup/operatingsystem/ubuntu](https://store.opendns.com/setup/operatingsystem/ubuntu)

---

### Post by anton706 on 2011-07-13
It didnt work....
is there any other way?

---

### Post by oldos2er on 2011-07-13
What exactly didn't work?

---

### Post by anton706 on 2011-07-14
It doesn't filter any web site that I told it to filter on the openDNS website.

---

### Post by gandaran on 2011-07-14
> **anton706 said:**
> It doesn't filter any web site that I told it to filter on the openDNS website.
do you mean opendns dynamic dns service? if correct you can use ddclient, (install from package manager) see instructions for [ddclient here]("http://ideabank.opendns.com/story.php?title=ip_updating_software_for_linux")
if your router supports opendns ddns setup you don't need any updater installed, the router should keep the IP updated on opendns website.

---

### Post by anton706 on 2011-07-14
I installed DDclient using the link that has been given me but when I run:
 sudo gedit /etc/ddlient.conf

the text file is empty and according to the link it should not be empty 
what's happening?

---

### Post by gandaran on 2011-07-14
> **anton706 said:**
> I installed DDclient using the link that has been given me but when I run:
 sudo gedit /etc/ddlient.conf

the text file is empty and according to the link it should not be empty 
what's happening?
check if that file exists in the root file system, isn't there a typing error here? shouldn't it be 
```
 sudo gedit /etc/dd[COLOR="Red"]c[/COLOR]lient.conf
```

---

### Post by anton706 on 2011-07-17
Thanx it worked,one question:
it will be automatic now I mean will if my ip changes it will work like openDNS updater?

---

