---
title: "update canceled, now firefox doesn't start and gives parse errors - please help!"
date: 2010-09-17
forum: General Help
---

### Post by Hachi-Roku on 2010-09-17
Hey guys,

Been a while since i posted... thats because my ubuntu has been SOLID for ages! :)
[B]
Background;[/B]
So last night i was doing an update, normal update manager stuff, was updating firefox. I canceled the update because i noticed it was patheically slow (were talking 800 B/s) and then all hell broke loose.
[B]
symptoms;[/B]
firefox icon vanished. 
over night its came back. still same errors.

before it vanished, when started it gave a XML parse error: chrome:// something something browser / browser location line 33 column 1. and firefox doesnt start.
( i took a screenshot but its on a diff partition atm). 

trying to update again i get a 'broken packages' message.

**what ive tried;**
searched many forums... on my phone (heinous process).

done the; sudo apt-get -f install. And many variations read in forums with no luck. 

went into Synaptic and checked broken packages for re install.
that gives a "subprocess dpkg exit error 2."

I've now temporarily gone to the last-resort-darkside to use the net etc. and i notice everything internet is fast as usual. strange.

Of course this happens when my honours thesis draft is due in a weeks time. 

**wishes;**
I'd like to somehow recover firefox. without doing a complete OS reinstall.

I'd like to understand why im getting an error when i try to reinstall the broken packages.

Can anyone help?

---

### Post by rockachu2 on 2010-09-17
Try:
A) 
sudo -i
apt-get autoclean
apt-get clean
apt-get autoremove

b)
sudo dpkg --configure
then 
sudo apt-get remove --purge firefox 
if doesn't work: 
    sudo dpkg --remove -force --force-remove-reinstreq firefox
sudo apt-get install firefox

---

