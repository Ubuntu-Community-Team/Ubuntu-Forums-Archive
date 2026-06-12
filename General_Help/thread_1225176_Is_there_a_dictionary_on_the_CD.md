---
title: "Is there a dictionary on the CD?"
date: 2009-07-28
forum: General Help
---

### Post by crest on 2009-07-28
I have tried to find a guide on how the dictionary works but no luck. Is there a dictionary installed on the CD? Or does the Accessories>Dictionary only work with an internet connection?  ( The PC being used is not connected to internet )

---

### Post by kornyam on 2009-07-28
When connected to the internet, my dictionary works fine, but when I disconnect, I get the following error:

```
Error while retrieving the definition

Lookup failed for host 'dict.org': Unknown error
``` 

So I'm guessing it works based on getting definitions from "dict.org"

---

### Post by crest on 2009-07-28
Ok thanks, that is out then. However, there is the following file on the CD: /usr/share/myspell/dicts/th_en_US_v2.dat  and an associated index file.  Can that be accessed somehow?

---

### Post by pmlxuser on 2009-07-28
have you tried copying the same to the harddisk structure
ie
```

cp media/cdrom0/usr/share/myspell/dicts/th_en_US_v2.dat   /usr/share/myspell/dicts/th_en_US_v2.dat


```
plus the index file.

i think if the cd library has data you will be able to access it. haven't tried it yet but it works for some other things...

---

