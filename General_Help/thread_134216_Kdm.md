---
title: "Kdm"
date: 2006-02-21
forum: General Help
---

### Post by phantasma on 2006-02-21
Ok i just installed kubuntu and i keep getting an error : temporary failure in name resolution..

I have an ati x800pro pci-e and an amd 3200 venice.. i dont know what is going wrong... and the KDM doesn't feel like loading any reso even though i installed all..

---

### Post by eylisian on 2006-02-21
So you just installed and at first boot you are getting this? Or have you been fiddling? =)

The name resolution fail is networking and KDM is well... we need more info.

```
dmesg |cat|grep kdm 
```

or look in;

```
cd /var/log/kdm
```

look for the most recent log file and tail (or cat) it

```
cat \:0.log
```
note: the \ is to escape the :

Please cut and paste the results of your sleuthing.

Thanks.

---

### Post by phantasma on 2006-02-21
ya this is at the first boot, i tried the

```
sudo app-get install KDM start
```

and all the other attributes, i just wanna be able to configure it and select certain reso's. I have tried running my live copy of hedgehog, same prob with the gdm, Im thinking it mnust be something with my video card.

---

