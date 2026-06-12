---
title: "Synaptic Package Manager - complete removal"
date: 2010-08-07
forum: General Help
---

### Post by fterh on 2010-08-07
I just installed VLC player 1.1.2, but during installation it says it requires a whole bunch of other packages to be installed as well (dependencies is the word for it I think). So I installed them. So if I want to remove VLC player 1 day, and I mark it for complete removal, will the dependencies be uninstalled as well?

---

### Post by oldsoundguy on 2010-08-07
> **fterh said:**
> I just installed VLC player 1.1.2, but during installation it says it requires a whole bunch of other packages to be installed as well (dependencies is the word for it I think). So I installed them. So if I want to remove VLC player 1 day, and I mark it for complete removal, will the dependencies be uninstalled as well?

they should.  But there are some clean up options if it does not including the third party program of Ubuntu Tweak .. nice program if for other things, too!

---

### Post by Revolutionary101 on 2010-08-07
No they will not be removed. In order to remove the dependencies after you have done a complete removal of VLC, you have to type this command into Terminal (Applications>Accessories>Terminal)
```
sudo apt-get autoremove
```
That will get rid of any dependencies that are not being used.

---

### Post by fterh on 2010-08-07
Good old terminal huh I guess? Useful command, must remember this :D

---

### Post by linux18 on 2010-08-07
```
 sudo apt-get -f purge && sudo apt-get autoremove 
```

---

### Post by fterh on 2010-08-08
I just uninstalled Empathy IM client via aptitude. Then I run "sudo apt-get -f purge && sudo apt-get autoremove", but it prints 0 for everything. What does this mean? No dependencies to remove? But then I have several packages such as empathy-common installed.

---

### Post by fterh on 2010-08-08
> **fterh said:**
> I just uninstalled Empathy IM client via aptitude. Then I run "sudo apt-get -f purge && sudo apt-get autoremove", but it prints 0 for everything. What does this mean? No dependencies to remove? But then I have several packages such as empathy-common installed.
Bump!

---

### Post by fterh on 2010-08-08
> **fterh said:**
> I just uninstalled Empathy IM client via aptitude. Then I run "sudo apt-get -f purge && sudo apt-get autoremove", but it prints 0 for everything. What does this mean? No dependencies to remove? But then I have several packages such as empathy-common installed.
Bump! Any ideas?

---

### Post by linux18 on 2010-08-08
try:

```
  sudo killall synaptic && sudo killall aptitude && sudo killall mintinstall && sudo killall software-center && sudo rm /var/lib/dpkg/lock && sudo rm /var/cache/apt/archives/lock && sudo rm /var/lib/apt/lists/partial/* && sudo rm /var/cache/apt/*.bin 
sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' ') 
sudo apt-get -f install && sudo apt-get clean && sudo apt-get autoclean 
sudo apt-get autoremove && sudo apt-get update && sudo apt-get --fix-broken upgrade 
  
```

---

### Post by giddyup306 on 2010-08-08
> **fterh said:**
> Bump! Any ideas?
Did you try Ubuntu Tweak?  That program is awesome!  I wish I would have known about it 8 months ago when I started getting serious with Linux.

---

### Post by bodhi.zazen on 2010-08-08
> **fterh said:**
> I just uninstalled Empathy IM client via aptitude. Then I run "sudo apt-get -f purge && sudo apt-get autoremove", but it prints 0 for everything. What does this mean? No dependencies to remove? But then I have several packages such as empathy-common installed.

It means you are good to go =)

---

