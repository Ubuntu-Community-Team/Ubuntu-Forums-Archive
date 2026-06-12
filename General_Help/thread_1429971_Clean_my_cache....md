---
title: "Clean my cache...???"
date: 2010-03-14
forum: General Help
---

### Post by robertcoulson on 2010-03-14
Is there a cache in Ubuntu...???
1 - Where do I find it...???
2 - How do I clear it...???
Robert

---

### Post by blueridgedog on 2010-03-14
Do you mean cached items in system memory?

How about this:

[http://linux-mm.org/Drop_Caches](http://linux-mm.org/Drop_Caches)

---

### Post by robertcoulson on 2010-03-14
Well... I thought cache was stuff left over like in Windows that you delete...???...Is that what you send me...???
Robert

---

### Post by colobix on 2010-03-14
If you mean internet cache you go to the tool menu and there you will see "delete private data" or something.
Pr of mean temp files then you can use
sudo apt-get clean
But memory temp will be cleaned automatically when you shut down the system.
If you want to know where the browser cache is located;
/home/username/.mozilla/firefox/knv55of6.default/Cache

---

### Post by robertcoulson on 2010-03-14
Oh, Ok...It cleans itself after shutdown...Great, thanks.
Robert

---

