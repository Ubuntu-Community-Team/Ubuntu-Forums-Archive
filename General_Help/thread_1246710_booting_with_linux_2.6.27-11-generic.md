---
title: "booting with linux 2.6.27-11-generic"
date: 2009-08-22
forum: General Help
---

### Post by danbar on 2009-08-22
Although I did the latest upgrades to jaunty and had linux 2.6.27.15 installed, when I boot up I only see the 2.6.27-11.  On my laptop I see the 15 (+ all the previous ones).  On my desktop I see the 11 one only. Why?

---

### Post by zvacet on 2009-08-22
You don´t need so much kernels.Two is enough (in case that latest doesn´t work as it should).If you want to remove them in synaptic search box type linux-image and remove ones with lower number.You may try 

```
sudo update-grub
```

---

### Post by danbar on 2009-08-23
thanks for you time and patience. Sorry for taking so long to write back due to family illness.  

I did the update yet everything remained the same. when it booted, it showed the 11 one only. I agree with you that two images will suffice yet I don't have the latest one. In the synaptic manager there are many images including the latest one (15).  Can I just remove the 11th image?

---

