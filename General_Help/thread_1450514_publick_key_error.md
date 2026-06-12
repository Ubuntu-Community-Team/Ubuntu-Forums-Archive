---
title: "publick key error"
date: 2010-04-09
forum: General Help
---

### Post by shahzadah on 2010-04-09
Hi! 

     I was trying to update my pc using this comand : '[COLOR=Blue]sudo apt-get update[/COLOR]' in terminal.
     its look every thing went fine ecept in last i have a msg in my terminal : '[COLOR=Blue]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE[/COLOR]'. can anyone please guide mw what this problem is... and if please anyone explain me too why it is occuring... actually i was trying to setup evolution mail for my hotmail account and i was following procedure from '[COLOR=Blue]www.ubuntugeek.com/send-and-receive-your-hotmail-messages-through-evolution.html[/COLOR]' this site.... its looks to me bit tough so i went for youtube and searched for '[SIZE=1][SIZE=1][COLOR=Blue]Set Up Evolution E-mail in Ubuntu 9.10[/COLOR][/SIZE]'  			[/SIZE]of 'ubuntuhelpguy'... but it gives error 'error while fetching mail'... please if someone tell me how to set up my evolution too..
best regards

---

### Post by oldos2er on 2010-04-09
You need to install the public key for that repository. ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E871C4A881574DE
```

---

