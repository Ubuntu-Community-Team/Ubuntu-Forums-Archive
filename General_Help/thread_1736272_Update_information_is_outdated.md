---
title: "Update information is outdated"
date: 2011-04-22
forum: General Help
---

### Post by sandy0594 on 2011-04-22
Hi all, I am very new to Linux platform,recently installed Ubuntu 10.10..Today,i am getting a warning like symbol in the top right panel..it says that 

> 
The update information is outdated.This may be caused by network problems or may be caused by a repository that is no longer available.Please update manually by clicking this icon... 

 I clicked it but nothing is installing and the icon stays there..Any idea what to do?
See the attachment for the icon

---

### Post by coffeecat on 2011-04-22
Try this: open System > Administration > Update Manager and click on the "check" button.

---

### Post by sandy0594 on 2011-04-22
It is saying [B]check your Internet connection
[/B]As u can see i am browsing the net..why it is saying like that?

---

### Post by ivanovnegro on 2011-04-22
Maybe you are using an outdated PPA?
Had this once, could be outdated, no longer supported or they have server problems and just wait. Can you update normally apart from this message?

---

### Post by sandy0594 on 2011-04-22
Sorry for my ignorance,how should i do that..As i am new to this i am unaware of it

> 
W:GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8, W:Failed to fetch [http://ppa.launchpad.net/weather-indicator-team/pp/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/weather-indicator-team/pp/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/weather-indicator-team/pp/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/weather-indicator-team/pp/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old



Those are the error messages

---

### Post by ivanovnegro on 2011-04-22
> **sandy0594 said:**
> Sorry for my ignorance,how should i do that..As i am new to this i am unaware of it



Those are the error messages

Hm, you have a deb file in your sources list from Lenny, strange. I would remove it and install Opera from their site but for [Ubuntu]("http://www.opera.com/browser/download/"). Maybe this is the culprit.

Ah, and remove the two weather indicators from your sources list also, they are showing a 404 error message. Then try to update again.

---

### Post by sandy0594 on 2011-04-22
Removed that and tried again..
> 
Failed to fetch [http://ppa.launchpad.net/weather-indicator-team/pp/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/weather-indicator-team/pp/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/weather-indicator-team/pp/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/weather-indicator-team/pp/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead
.

---

### Post by coffeecat on 2011-04-22
Open System > Administration > Synaptic. Now Settings menu > Respositories. Now Other Software tab. Untick the entries for deb.opera.com lenny and for ppa.launchpad.net/weather-indicator-team and close that window. Now click on the reload button.

---

### Post by sandy0594 on 2011-04-22
Yup,right on the track..Updated
Thanks for the reply
:)

---

