---
title: "Dansguardian blocking Google Image Results"
date: 2011-05-06
forum: General Help
---

### Post by jamesloker on 2011-05-06
Hi All,
Got a weird one for you.
Ubuntu Server installed with NTLM authentication. All works fine except for google images
With the filter turned off, it will display the images (of course it will) with the filter turned on it returns the google images results page as normal but without any images. (Please See Attached which was a simple search for FOOD)

I have 3 groups F1 (unfiltered) F2 (teachers) and F3(pupils)
F1 and F2 arent in use yet but F3 is.

Please help!

---

### Post by Jordy_224 on 2011-05-17
Hey, 
 Is this problem specific to the Google images web search or do others preform the same? It follows... what about web galleries, and blogs (picsearch.com, blogs, flickr.com, etc)?

If so, one suggestion, is that a "ban" in placed on downloading certain image extensions like .jpg .png .bmp. 
Check this by editing the following file: ```
/etc/dansguardian/lists/exceptionextensionlist 
``` 

-Jordy

---

