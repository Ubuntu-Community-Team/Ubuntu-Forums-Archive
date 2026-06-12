---
title: "Server strange problem lighttpd"
date: 2011-03-02
forum: General Help
---

### Post by ThaDoctor99 on 2011-03-02
Well I got a VPS for a website.
Hadn't really dapple a lot with server configuration before, but I am quite sure I have not done anything wrong since lighttpd says that my syntax is OK
and it also makes no complain when I start it
I do 
/etc/init.d/lighttpd start
The system says 
Starting server
Lighttpd start                                                     [OK]


In essence that is what it says. Not the correct words.
But the strange things happens when I then check the server
46.4.135.54
via that IP.
Then it just throws an error at me, as when I then request a status through the init.d command it says 
lighttpd is NOT running

I thought it was strange as I had just done something with adding fastcgi, and had it running with that then I tried to add some php handling and it did run, however that was with a html page, then I thought I would have to check whether that helped the problem that I could not see the php page on with 
```

<?php
echo "hello world"
?>

```
just for testing
but that really put the server off.
So now it wont even start.

---

### Post by ThaDoctor99 on 2011-03-03
BUMP!
Just making this one relevant again... After the 24 hour period. Or about that.

---

