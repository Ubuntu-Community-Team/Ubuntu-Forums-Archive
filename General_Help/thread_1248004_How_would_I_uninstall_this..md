---
title: "How would I uninstall this."
date: 2009-08-23
forum: General Help
---

### Post by cptrohn on 2009-08-23
These are the commands that I used to get my TVtuner to work...

I am thinking that if perhaps I uninstall this and then re-install them using the correct kernel information that I will be able to get my TV tuner to work correctly again..

```
 wget http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
 wget http://www.steventoth.net/linux/xc5000/extract.sh
 sh extract.sh
 cp dvb-fe-xc5000-1.1.fw /lib/firmware

```


So would sudo apt-get uninstall work with these?

---

### Post by wojox on 2009-08-23
I think:
```
sudo apt-get --purge remove <package>
```

Would work better.

---

### Post by credobyte on 2009-08-23
Um, it looks like you've just copied some files, not installed ( Aptitude, .deb, etc. ) something. 
 
Try:
```
 
sudo rm /lib/firmware/dvb-fe-xc5000-1.1.fw

```

---

### Post by michy99 on 2009-08-23
Nope, apt doesn't know anything about this. I think you just have to delete the dvb-fe-xc5000-1.1.fw file from /lib/firmware, but to be sure, post the extract.sh file here.

---

### Post by cptrohn on 2009-08-23
Ok.. thanks for the help guys.. got things working correctly again...

I guess I will have to do this to get it working after every kernel upgrade then eh?

---

