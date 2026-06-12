---
title: "Saving BMON internet speet to TXT"
date: 2010-11-23
forum: General Help
---

### Post by dansku on 2010-11-23
Hi, I would like to know how can I save the internet speed shown from the bmon program to a txt file. any ideas?

thanks

---

### Post by TeoBigusGeekus on 2010-11-23
```
bmon -o ascii| tee ~/Desktop/networktraffic.txt
```

---

### Post by Goldfissh on 2010-11-23
Is there anything Linux CAN'T do? :D

---

### Post by shahraeini on 2011-02-07
I've tried bmon more than 100 times to export its report on a html file and try a example explain in man page like this: 
"bmon -I distribution:multicast -o null -O html:path=/var/istats/" 

but it said: 
"fopen(/var/istats//layout.css) failed: No such file or directory"

I really need this kind of report.
I wonder if someone could help me... thanks....

---

### Post by dcstar on 2011-02-07
> **shahraeini said:**
> I've tried bmon more than 100 times to export its report on a html file and try a example explain in man page like this: 
"bmon -I distribution:multicast -o null -O html:path=/var/istats/" 

but it said: 
"fopen(/var/istats//layout.css) failed: No such file or directory"

I really need this kind of report.
I wonder if someone could help me... thanks....

**You** cannot write to system folders like /var - and **you** never should.

---

### Post by shahraeini on 2011-02-07
> **dcstar said:**
> **You** cannot write to system folders like /var - and **you** never should.

thanks for your quick reply, it's a example on man page, I tried different location and sudo for root access, I got the same error ...

---

### Post by shahraeini on 2011-02-11
> **shahraeini said:**
> thanks for your quick reply, it's a example on man page, I tried different location and sudo for root access, I got the same error ...

no answer?!

---

