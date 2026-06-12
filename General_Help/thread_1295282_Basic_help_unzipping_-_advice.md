---
title: "Basic help unzipping - advice?"
date: 2009-10-19
forum: General Help
---

### Post by shaunsmith_99 on 2009-10-19
Hey,
 
I'm spending time each day and getting pretty comfortable with my bash terminal - I can do *almost* whatever I want but I've run into a problem I can't solve.
 
I just downloaded the Map_Pack.zip file for Open Arena. I've made plenty of add-ons for Open Arena with no problem.. I usually expand the extra goodies to the /baseoa/ folder a-like-a-this...
 
-----------------------------------
**unzip map_pack.zip -d /usr/share/games/openarena/baseoa/**
---------------------------------------
 
I downloaded the extra mappack from Gameupdates and it pumped out the 546mb moster zip file. When I try to look what's in there, I get an error
 
 
----------------------------
 
7-Zip 4.58 beta Copyright (c) 1999-2008 Igor Pavlov 2008-05-05
p7zip Version 4.58 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)
 
Error: /home/shaun/Desktop/map_pack.zip is not supported archive
 
Errors: 1
--------------------------
 
and it won't expand from the shell either....
 
 
-----------------
*End-of-central-directory signature not found. Either this file is not*
*a zipfile, or it constitutes one disk of a multi-part archive. In the*
*latter case the central directory and zipfile comment will be found on*
*the last disk(s) of this archive.*
*unzip: cannot find zipfile directory in one of map_pack.zip or*
*map_pack.zip.zip, and cannot find map_pack.zip.ZIP, period.*
--------------------------------------
 
 
Can anyone give me a pointer here??!?!

---

### Post by BitJunkie on 2009-10-19
It sounds like the file might be corrupt. What's the output of "file map_pack.zip"?

---

### Post by shaunsmith_99 on 2009-10-19
Hmm, what does that mean? If I run the file command, this is what I have..


-----------------------------------------------------
shaun@shaun-laptop:~/Desktop$ file map_pack.zip
map_pack.zip: data
------------------------------------------------

---

### Post by -Zeus- on 2009-10-19
> **shaunsmith_99 said:**
> Hmm, what does that mean? If I run the file command, this is what I have..


-----------------------------------------------------
shaun@shaun-laptop:~/Desktop$ file map_pack.zip
map_pack.zip: data
------------------------------------------------
Your file is corrupt, I suggest redownloading. (note the file type as 'data', a correct zip should show up as file: : Zip archive data, at least v2.0 to extract)

---

### Post by shaunsmith_99 on 2009-10-19
Thanks Stewie. Good to know. Oh-boy, getting a good download from Torrents is going to be F-U-N.

---

### Post by BitJunkie on 2009-10-20
> **-Zeus- said:**
> Your file is corrupt, I suggest redownloading. (note the file type as 'data', a correct zip should show up as file: : Zip archive data, at least v2.0 to extract)
+1, agreed

---

