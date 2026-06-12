---
title: "How do I get rid of some weird stuff in a text file?"
date: 2011-11-09
forum: General Help
---

### Post by lethalfang on 2011-11-09
I've made a .csv out of some spreadsheet, and it seems like there are a couple of trailing spaces that I need to get rid of. 
So here is the weird thing. What appears to be a couple of trailing spaces, aren't exactly space characters. 

```
cat textfile

AAK1
AATK
ABL1
ABL2
ACTR2

```


```

cat -v textfile

AAK1M-BM-  
AATKM-BM-  
ABL1M-BM-  
ABL2M-BM-  
ACTR2M-BM-  

```

Now, the question is, what the heck is "M-BM-" and how do I get rid of it?

Thanks in advance.

---

### Post by papibe on 2011-11-09
It looks like the representation of non graphic character. I dug a little and it seems to be a 0x96 byte/character. If you open the file on vi or vim, you should see something like:
```
AAK1<96>
AATK<96>
ABL1<96>
ABL2<96>
ACTR2<96>
```
Also you can try the command 'od -x' to get the right hex number.

If that's the actual character, you may use 'tr' to change it to whatever you need. For example an space
```
 cat textfile | tr "\227" " "
```
\227 is 0x97 in octal.

Hope it helps,
Regards.

---

