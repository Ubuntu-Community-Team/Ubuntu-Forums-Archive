---
title: "backtrack 4 pre on virtulabox ose drivers problem"
date: 2010-03-28
forum: General Help
---

### Post by sky net on 2010-03-28
hi guys

lenovo r500 , intel wireless card : iwl5100

i installed backtrack pre 4 on virtualbox ose

i have ubuntu 9.10

but i cant see my wireless card !!

with iwconfig :

lo
eth0

where is wlan0 ??

how can i configure my wireless card on bt4 on virtualbox ??

someone can help ?

---

### Post by Megafag on 2010-03-28
> **sky net said:**
> hi guys

lenovo r500 , intel wireless card : iwl5100

i installed backtrack pre 4 on virtualbox ose

i have ubuntu 9.10

but i cant see my wireless card !!

with iwconfig :

lo
eth0

where is wlan0 ??

how can i configure my wireless card on bt4 on virtualbox ??

someone can help ?

Backtrack has pretty crappy driver support.

---

### Post by sky net on 2010-03-28
so , there is no solution ???

---

### Post by Megafag on 2010-03-28
> **sky net said:**
> so , there is no solution ???

You can get the programs for "testing security" and run them on ubuntu you know.

---

### Post by sky net on 2010-03-28
i dont care for testing on bt ~~
i have my aircrack-ng package works good on ubuntu , with the best wireless card (iwl5100) and i crack wpa using the silliest tools ever like spoonwpa and so ~~ 
but really i need to have bt4 working on my virtualbox , just for all the rest of tools which backtrack can provide me with ~~
i wish i could get the all the tools on my ubuntu
just if i could get the dist tools somewhere else except of : repo.offensive-security.com ~~

---

### Post by DaveInPhx on 2010-03-29
I spent some time kicking myself for not seeing this on a thunbdrive problem I had before, so putting it up here so you can save yourself some kicking (just in case!).

Open virtualbox but don't start up the OS yet. Click on settings. In your case you go to the network menu and click on the adapter tab - make sure it is enabled! In my case it was the USB tab - the USB reader wasn't enabled! ><

Hopefully your problem will be as simple as that to resolve - I now check there very carefully any time I change any hardware!!

---

### Post by sky net on 2010-03-29
> **DaveInPhx said:**
> I spent some time kicking myself for not seeing this on a thunbdrive problem I had before, so putting it up here so you can save yourself some kicking (just in case!).

Open virtualbox but don't start up the OS yet. Click on settings. In your case you go to the network menu and click on the adapter tab - make sure it is enabled! In my case it was the USB tab - the USB reader wasn't enabled! ><

Hopefully your problem will be as simple as that to resolve - I now check there very carefully any time I change any hardware!!

you got it right !!

i compared the options for my windows 7 virtual machine (where wireless card works ) with options of backtrack virtual machine and i had a mistake !!

i corrected it!! i'm reinstalling the system now !!

---

### Post by sky net on 2010-03-29
i have the same problem till now !!

---

