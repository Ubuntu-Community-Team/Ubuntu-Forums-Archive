---
title: "Problems having Ubuntu 10.04 recognised by OS X"
date: 2010-07-26
forum: General Help
---

### Post by creativelies on 2010-07-26
Hello all.  Thanks for taking the time to read :)

We want a file server for the office and have installed Ubuntu 10.04 Desktop onto a PC we had laying around with the intent of having it accessible by our Macs (all-mac environment).

We followed the guide here:

[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

The server is visible (most of the time) in Finder with the Xserve icon but we cannot connect to it using the Ubuntu login/pw - it simply says "Incorrect username or password" no matter what we put in.  We can always find it with Command+K.

The content of /etc/netatalk/AppleVolumes.default is:

~/ "Home Directory"
~/ "$u" allow:cserver cnidscheme:cdb

where cserver is the sole login for Ubuntu.

We didn't follow any of the instructions under the "Time Machine" section of that guide because we assumed we wouldn't need to since we're not needing that function.

What are we missing?

---

### Post by robsoles on 2010-07-26
I just skimmed the guide you linked to and am very confident that to make it work as that guy suggests (or be sure that it doesn't and he did something that he forgot to put in his guide to make it work for himself (not that likely really)) you will have to follow every last step that he posted in his guide.

Please follow the instructions you admitted you didn't and then consider contacting that fellow if it still doesn't work.


I could instruct you on making Samba into a great file-server with domain and everything for your network but you are already some percentage of the way through making (hopefully) more functional toward your MAC based work-place.

---

### Post by creativelies on 2010-07-26
> **robsoles said:**
> I just skimmed the guide you linked to and am very confident that to make it work as that guy suggests (or be sure that it doesn't and he did something that he forgot to put in his guide to make it work for himself (not that likely really)) you will have to follow every last step that he posted in his guide.

Please follow the instructions you admitted you didn't and then consider contacting that fellow if it still doesn't work.


I could instruct you on making Samba into a great file-server with domain and everything for your network but you are already some percentage of the way through making (hopefully) more functional toward your MAC based work-place.

Thanks for your input - I had read the guide originally as having the Time Machine section being optional but re-reading it it actually doesn't explicitly state that so you have a good point.

Will start over and do the full guide and see how that goes.  I will also look into why this method is better than sharing via Samba in case this doesn't work.

Thanks.

---

### Post by robsoles on 2010-07-26
Welcome - glad you didn't take me as being harsh about it as that wasn't my intent.

I am subscribed to this thread, if you post in it with further request for help I will (at least eventually) notice and respond if I think my response is worth your while to read.

---

### Post by creativelies on 2010-07-26
> **robsoles said:**
> Welcome - glad you didn't take me as being harsh about it as that wasn't my intent.

I am subscribed to this thread, if you post in it with further request for help I will (at least eventually) notice and respond if I think my response is worth your while to read.

Went through the whole lot from a fresh install and it still didn't work - have called it a day for trying with AFP and am looking up how to make Samba play nice with OS X now in the hope that something functional can be done in a reasonable timeframe :)

---

### Post by robsoles on 2010-07-26
I realise your last post wasn' t an explicit request for help :)

The following howto should (1) work and (2) allow MACs to access the server as if they are accessing a Windows share which I know MAC OS X is capable of.

[https://help.ubuntu.com/9.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/9.04/serverguide/C/samba-fileserver.html)

---

### Post by creativelies on 2010-07-26
> **robsoles said:**
> I realise your last post wasn' t an explicit request for help :)

The following howto should (1) work and (2) allow MACs to access the server as if they are accessing a Windows share which I know MAC OS X is capable of.

[https://help.ubuntu.com/9.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/9.04/serverguide/C/samba-fileserver.html)

Beautiful - it's working already!  That was a whole lot simpler.  Shame I didn't find that before the AFP sharing - I could have saved myself a couple of days of headaches :p

Thanks very much :)

---

### Post by robsoles on 2010-07-26
Very welcome, glad to help at all - please consider marking this thread solved using the 'thread tools' above in red text.

---

### Post by creativelies on 2010-07-26
> **robsoles said:**
> Very welcome, glad to help at all - please consider marking this thread solved using the 'thread tools' above in red text.

Done. :)

---

### Post by Stefano Bragaglia on 2010-08-17
> **creativelies said:**
> We followed the guide here:

[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)


That guide is more or less 2 years old... and applies to Ubuntu 8.04 and Leopard 10.5.x...

You should follow the steps of this updated guide (Ubuntu 10.04, Snow Leopard 10.6.4):
[http://talklikeaduck.denhaven2.com/2010/07/19/ubuntu-timemachine-server-for-snow-leopard](http://talklikeaduck.denhaven2.com/2010/07/19/ubuntu-timemachine-server-for-snow-leopard)

Unfortunately I don't own a MBP (yet) and I'm just an average Ubuntu user (so I cannot grant for the final success) but according to the guide and the unique comment, it works pretty fine!

Hope it helps, let us know if it works,
    Stefano

---

### Post by creativelies on 2010-08-19
> **Stefano Bragaglia said:**
> That guide is more or less 2 years old... and applies to Ubuntu 8.04 and Leopard 10.5.x...

You should follow the steps of this updated guide (Ubuntu 10.04, Snow Leopard 10.6.4):
[http://talklikeaduck.denhaven2.com/2010/07/19/ubuntu-timemachine-server-for-snow-leopard](http://talklikeaduck.denhaven2.com/2010/07/19/ubuntu-timemachine-server-for-snow-leopard)

Unfortunately I don't own a MBP (yet) and I'm just an average Ubuntu user (so I cannot grant for the final success) but according to the guide and the unique comment, it works pretty fine!

Hope it helps, let us know if it works,
    Stefano

Thanks very much for that - once I get the system back up and running after a HDD failure I'll give it a shot :)

---

