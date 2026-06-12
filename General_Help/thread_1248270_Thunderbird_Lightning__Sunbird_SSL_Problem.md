---
title: "Thunderbird Lightning / Sunbird SSL Problem"
date: 2009-08-24
forum: General Help
---

### Post by discodan on 2009-08-24
Help,

I'm using Sunbird to connect to a Caldav server via https.  When I was setting up the connection, I accidentally clicked the option to decline the certificate.  Now no matter what I do now, I cannot get Sunbird to re-request the ssl certificate.  I can connect OK from other machines, so I know the server is OK, and I have the credentials correct.  I think it's got to be something simple where this server certificate has now been blacklisted.  But I can't figure out how to reverse this.  I have tried the following with no effect:

*  apt-get purge sunbird 
*  rm -rf ~/.mozilla ~/.mozilla-thunderbird 

Also, as a test, I install Thunderbird and Lightning on an WinXP pc, and the same symptoms occur if I click decline when I am first prompted for the certificate.  Now I cannot connect to the caldav server from 2 pcs.  

Any help anyone can provide would be greatly appreciated,

:confused:

-disco-

---

### Post by discodan on 2009-08-24
Ok... nevermind.

I must have been super super tired last night, because when I looked at it again this morning, I realized I had been mis-typing the url.  I kept forgetting the port.  

DOH!

---

