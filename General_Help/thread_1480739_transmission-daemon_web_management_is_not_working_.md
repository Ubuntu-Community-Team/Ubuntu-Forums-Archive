---
title: "transmission-daemon web management is not working out of the box on 9091"
date: 2010-05-11
forum: General Help
---

### Post by bgabga on 2010-05-11
Can anybody give me 1,2,3 instrunctions on how to setup transmission-daemon web interface on port 9091?

I did:
sudo apt-get install transmission-daemon

On the same PC (as  transmission-daemon)  I tried [http://127.0.0.1:9091/](http://127.0.0.1:9091/)  but is not working. 
Why is not working out of the box ???



Thank you,

---

### Post by bgabga on 2010-05-12
I found:

You have to edit 

 vim /home/transmission/.config/transmission-daemon/settings.json

disable white list:  rpc-whitelist-enabled": false,

or add remote PC IP address to rpc-whitelist

then start 


transmission-daemon -g /home/transmission/.config/transmission-daemon

---

### Post by alecz20 on 2010-08-23
I wasn't able to add any torrents using the web interface.

I tried via Open > Browse > Upload, but nothing happens.

Trying via command line works, but I want to be able to to this from the Web Interface.

---

