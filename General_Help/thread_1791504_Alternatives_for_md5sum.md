---
title: "Alternatives for md5sum?"
date: 2011-06-26
forum: General Help
---

### Post by NormaJean on 2011-06-26
Ahoy, 

I've been finding that md5sum is fairly slow when doing larger files (~200gb). I've had a sticky beak around, but couldn't find anything but maybe one of you lovely people could point me in the way of an alternative or perhaps a fix for this? 
Cheers :) 

Sys Specs: 
xeon x5460 
8gb ram

---

### Post by Ozymandias_117 on 2011-06-27
There's shasum.  Depending how secure you want it, there is sha1sum sha224sum sha256sum sha384sum sha512sum (From least secure to most, but the more secure, the more processing power required)

---

### Post by CharlesA on 2011-06-27
> **Ozymandias_117 said:**
> There's shasum.  Depending how secure you want it, there is sha1sum sha224sum sha256sum sha384sum sha512sum
+1.

I use sha1sum all the time.

---

### Post by NormaJean on 2011-06-27
Thanks guys, I'm using it put across production work so I want to be certain, that what I copied across is the same as what was on the server. 

But, hopefully this might be better then md5 :)

---

### Post by NormaJean on 2011-06-27
Sorry guys, just another question. 
Have a directory, with 4 sub directories, that all have say 200 files a piece. 
I want to create a sha1 for each file without too much hassle. The man page isn't very helpful :( 

Would I be better off creating a script?

---

### Post by Vaphell on 2011-06-27
```
find . -type f -exec sha1sum "{}" \;
```

if you want to create a file with the list
```
find . **! -name 'sha1.lst'** -type f -exec sha1sum "{}" \; > sha1.lst
```
bolded part excludes the result file itself in case you want to rerun the command (already existing file with previous sums would be included)

---

### Post by NormaJean on 2011-06-27
Thank you very much :D

---

