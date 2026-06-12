---
title: "how to add medibuntu repo in 10.10 ?"
date: 2012-08-27
forum: General Help
---

### Post by paichkash on 2012-08-27
hi
i want to add the medibuntu repo in my ubuntu .. i tried the instructions on the following site

[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

but i  was unsuccessfull. 
```

r@rDR:/home$ sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
[sudo] password for r: 
--2012-08-27 09:50:35--  http://www.medibuntu.org/sources.list.d/maverick.list
Resolving www.medibuntu.org... 88.191.127.22
Connecting to www.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-08-27 09:50:36 ERROR 404: Not Found.
```


here is the result of the first command from that article..

Thanks

---

### Post by pqwoerituytrueiwoq on 2012-08-27
ubuntu 10.10 is EOL and no longer supported which is why you are getting a 404 error
if you must use gnome 2 there is 10.04 which has the next April 
xubuntu 12.04 is customizable like gnome 2

---

### Post by paichkash on 2012-08-27
hmm..
isnt there anyway to still use medibuntu repo ?
i think there was a trick to add the word old to url in sources.list and u uld be able to access that..
i m realy pissed by these day in day out installs / updates of ubuntu ... and this version is the only one that is working somehow the way i wnt .. 
also i m using old p3 1ghz,cpu so idealy i should be using ubunbtu 4.1 .. but anything above 8.04 is an overkill for it ..

---

### Post by pqwoerituytrueiwoq on 2012-08-27
can that thing even play a 320p video?
i know my old pentium III 512Mhz can't 
you may be able to use lubuntu
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

---

### Post by oldos2er on 2012-08-27
> **paichkash said:**
> hmm..
isnt there anyway to still use medibuntu repo ?
i think there was a trick to add the word old to url in sources.list and u uld be able to access that..
i m realy pissed by these day in day out installs / updates of ubuntu ... 

I wouldn't call every six months (or two years or more for LTS) "day in day out." Sounds like a different distro with lighter system requirements would suit you much better than the *buntus.

---

### Post by mc4man on 2012-08-27
try - 
[https://answers.launchpad.net/medibuntu/+faq/537](https://answers.launchpad.net/medibuntu/+faq/537)

---

### Post by paichkash on 2012-08-29
thanks all .. i have done nothing and the medibuntu repo as added aBOVE IS WORKING OK..
):P

---

