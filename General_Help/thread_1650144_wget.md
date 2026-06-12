---
title: "wget"
date: 2010-12-21
forum: General Help
---

### Post by c2tarun on 2010-12-21
can we use recursive download of wget to download all the wallpapers on a web page?

---

### Post by karthick87 on 2010-12-21
Yes,give a try to -r switch

```
wget -r <URL>
```

---

### Post by c2tarun on 2010-12-21
> **karthick87 said:**
> Yes,give a try to -r switch

```
wget -r <URL>
```

i tried :(

```

wget -r http://www.santabanta.com/wallpapers/category.asp?catname=deepika%20padukone

```
it downloaded some text files and nothing else.
Can u please check the link and please tell what i am doing wrong?

---

### Post by karthick87 on 2010-12-21
```
wget -r -A.jpg http://www.santabanta.com/wallpapers/category.asp?catname=deepika%20padukone
```

---

### Post by c2tarun on 2010-12-21
> **karthick87 said:**
> ```
wget -r -A.jpg http://www.santabanta.com/wallpapers/category.asp?catname=deepika%20padukone
```


here is the output i got.
```

$ wget -r -A.jpg http://www.santabanta.com/wallpapers/category.asp?catname=deepika%20padukone
--2010-12-21 16:47:17--  http://www.santabanta.com/wallpapers/category.asp?catname=deepika%20padukone
Resolving www.santabanta.com... 174.123.173.34
Connecting to www.santabanta.com|174.123.173.34|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17 [text/html]
Saving to: `www.santabanta.com/wallpapers/category.asp?catname=deepika padukone'

100%[======================================>] 17          --.-K/s   in 0s      

2010-12-21 16:47:24 (2.11 MB/s) - `www.santabanta.com/wallpapers/category.asp?catname=deepika padukone' saved [17/17]

Removing www.santabanta.com/wallpapers/category.asp?catname=deepika padukone since it should be rejected.

FINISHED --2010-12-21 16:47:24--
Downloaded: 1 files, 17 in 0s (2.11 MB/s)

```

I think it saved a file of name "catname=deepika padukone". but they are not the wallpapers.
Can you please explain what is the meaning of -A.jpg?

---

### Post by karthick87 on 2010-12-21
Check this link,

[http://www.thegeekstuff.com/2009/09/the-ultimate-wget-download-guide-with-15-awesome-examples/](http://www.thegeekstuff.com/2009/09/the-ultimate-wget-download-guide-with-15-awesome-examples/)

---

