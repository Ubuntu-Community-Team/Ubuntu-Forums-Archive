---
title: "kmess won't connect to MSN !!!"
date: 2011-01-14
forum: General Help
---

### Post by rostom_zer on 2011-01-14
have some of our members the sollution of my problem ???

when i try to connect to msn, after connecting, and loading the contacts

1 second later... it disconects immediatlly and a popup notification appears telling me " network connection lost "

here is what terminal wrot

> 
8.392> kmess(7500) RoamingService::updateDisplayPicture: Missing profileResourceId, not updating display picture 
18.079> kmess(7500) MimeMessage::splitLine: Couldn't split line ' "" ' 
18.079> kmess(7500) MimeMessage::splitLine: Couldn't split line ' "" ' 
39.209> kmess(7500) RoamingService::updateProfile: Missing profileResourceId, not updating profile 
39.209> kmess(7500) RoamingService::updateProfile: Missing profileResourceId, not updating profile 
39.517> kmess(7500) MsnNotificationConnection::slotError: MSN Notification Connection error type 4 : "The remote host closed the connection"


---

### Post by oxan on 2011-01-20
This is a known bug that's fixed in upstream commit dcfbdfd. I've created updated 2.0.5 packages for Lucid, Maverick and Natty, both i386 and amd64, in my [PPA](https://launchpad.net/~oxan/+archive/misc).

---

