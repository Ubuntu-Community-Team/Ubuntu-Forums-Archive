---
title: "unison + encfs as dropbox replacement??"
date: 2012-02-25
forum: General Help
---

### Post by jebus_beler on 2012-02-25
I've been trying to use an ssh accessible server to sync my desktop and laptop.  I would like the data on the server to always be encrypted.  This website provides instructions to this effect using unison + cryptosync:

[http://www.pedramhayati.com/thoughts/linux/275-how-to-setup-your-real-dropbox-file-service-using-shared-hosts](http://www.pedramhayati.com/thoughts/linux/275-how-to-setup-your-real-dropbox-file-service-using-shared-hosts)

Unfortunately cryptosync seems to be giving me problems so I'm looking for another solution.  Encfs seems like it might work but i'm not sure if it supports the kind of behaviour I want.

If I setup encfs on my desktop and laptop and then use unison (via a third server) to sync the encrypted directories will this work?  I.e. when unison updates the encrypted directories will encfs push the changes to the unencrypted copy and is this safe or is encfs only good for backup?  

I've heard people use encfs with dropbox so it sounds like this should work but no one mentions using it with unison so I wanted to check.

Thanks

---

### Post by ottosykora on 2012-02-25
[http://wuala.com/en/](http://wuala.com/en/)


wuala is also cloud storage, but is in one important point different from others. The data is highly encrypted *before* any part of it leaves your computer. Also the password /key will never leave your computer, so all is encrypted on the cloud server and nobody except you have any kind of access to the files, not even the server operator.

Software av for win, mac, linux and android, web access by a java applet only (so password does noeed to be transmitted over internet)

---

### Post by jebus_beler on 2012-02-26
Thanks for the response but waula isn't exactly what I was looking for because its closed source.  If they were open source I would consider it but I'm trying to avoid running closed source software, particularly when it comes to encryption and data sharing.  That's why I'm looking to build an in-house alternative with encfs and unison.  Has no one tried this?

---

