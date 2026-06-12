---
title: "Torrent"
date: 2010-02-11
forum: General Help
---

### Post by pedrom169 on 2010-02-11
Is there anyway of running a torrent application and me check how the torrents are running remotly over the internet?

Thanks

---

### Post by tom.swartz07 on 2010-02-11
> **pedrom169 said:**
> Is there anyway of running a torrent application and me check how the torrents are running remotly over the internet?

Thanks

Transmission, Deluge, and Vuze all allow you to do that. Just check under the preferences.


Vuze and Deluge need plugins, if i remember correctly.

---

### Post by pedrom169 on 2010-02-11
Thank you. i can know view it from my internal address. How can i few it from outside using my external IP?h

---

### Post by Dayofswords on 2010-02-11
[http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient#WebUI](http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient#WebUI)

look around in deluge's faq
i know with deluge you can connect to clients and use the program just as you were sitting right there
[http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient](http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient)


if your using transmission, or ktorrent or something, on your own
> Thank you. i can know view it from my internal address. How can i few it from outside using my external IP?h 

awnser: (for deluge, but idea is the same but port may be different(which normally can be changed))
> Client Setup ¶

   1. Open your preferred web browser.
   2. Open the URL:

      http://<server>:8112

      where <server> is either the private or public ip of the server depending if you are on the server's private network or not. 

   1. Default password is "deluge". 

Congratulations! You can now access deluge on the server via the web UI. 

---

