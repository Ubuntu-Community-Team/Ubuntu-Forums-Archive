---
title: "wireless problem PLEASE help"
date: 2011-03-15
forum: General Help
---

### Post by ermanaltind on 2011-03-15
Hi, I have a problem with connection via wireless. 
I can see wireless networks and select mine, then enter password , it tries afew minutes and asks again password I tried many things but none of them did work, I changed my wireless password even, but no no n connection. 
I read many arrticles but none of them is helpfull for me
can you please advise me something ?
my wireless card is atheros and ubuntu 10 newest.
thanks

---

### Post by flaak_monkey on 2011-03-15
Have you updated your Atheros Drivers?

---

### Post by 5149.5 on 2011-03-15
> **ermanaltind said:**
> Hi, I have a problem with connection via wireless. 
I can see wireless networks and select mine, then enter password , it tries afew minutes and asks again password I tried many things but none of them did work, I changed my wireless password even, but no no n connection. 
I read many arrticles but none of them is helpfull for me
can you please advise me something ?
my wireless card is atheros and ubuntu 10 newest.
thanks

You might have an encryption mismatch. e.g. your AP is running WPA and your card is setup for WEP?

---

### Post by ermanaltind on 2011-03-16
Ubuntu selects auto encrypting shows me wpa/wpa2 
originaly, it matches encrypting. 
I can connect to wireless if connection without password :(

I try to find newer driver, but I can not find anything at atheros's page.

thanks for your interests

---

### Post by plucky on 2011-03-16
> **ermanaltind said:**
> Ubuntu selects auto encrypting shows me wpa/wpa2 
originaly, it matches encrypting. 
I can connect to wireless if connection without password :(

I try to find newer driver, but I can not find anything at atheros's page.

thanks for your interests

Connect up wired to the internet and open **System > Administration > Hardware Drivers** and see what drivers it finds and installs.

Good Luck

---

### Post by ermanaltind on 2011-03-17
thanks  everybody
I find out a way and now it works for me 
I changed encryption from wpa/wpa2 to only wpa2 in settings of modem and now I can login to network
but I dont know what gonna happen when I  use in a different place :)

---

