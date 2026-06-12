---
title: "Search and replace"
date: 2010-10-18
forum: General Help
---

### Post by hunterlove22 on 2010-10-18
I have a file contains 

```
//app/[COLOR="Red"]com.modmyi.classicui[/COLOR]/XXX
//app/[COLOR="Red"]com.modmyi.classictheme[/COLOR]/XXXdd
//app/[COLOR="#ff0000"]com.modmyi.civilairpatrol[/COLOR]/UUU
//app/[COLOR="#ff0000"]com.modmyi.citytheme[/COLOR]/ddddd.d
//app/[COLOR="#ff0000"]com.modmyi.cityofchampsls[/COLOR]/cxxx.l
//app/[COLOR="#ff0000"]com.modmyi.thephoenixandthefalcon[/COLOR]/dddd
```

Here is the cut. I want to find and cut the string in the middle. Here i highlighted. I use sed and find but I am not successful. Please help me. Thanks.

---

### Post by Vaphell on 2010-10-18
i put your example in pattern.txt and 
```
cat pattern.txt | sed 's/\/com.modmyi.[a-z]*//' > result.txt 
``` seems to work just fine

---

### Post by hunterlove22 on 2010-10-18
Thanks. It works!:P

---

