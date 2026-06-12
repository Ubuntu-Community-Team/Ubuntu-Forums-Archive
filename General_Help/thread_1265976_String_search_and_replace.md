---
title: "String search and replace"
date: 2009-09-14
forum: General Help
---

### Post by unavenged on 2009-09-14
Hi,

I would like to know if there is a sh script that can go through a bunch of php files to search for a string(like a url) and change it?

Thanks in advance

---

### Post by unavenged on 2009-09-14
Ok so i found this script
```
#!/bin/bash
OLD="xyz"
NEW="abc"
DPATH="/home/you/foo/*.txt"
BPATH="/home/you/bakup/foo"
TFILE="/tmp/out.tmp.$$"
[ ! -d $BPATH ] && mkdir -p $BPATH || :
for f in $DPATH
do
  if [ -f $f -a -r $f ]; then
    /bin/cp -f $f $BPATH
   sed "s/$OLD/$NEW/g" "$f" > $TFILE && mv $TFILE "$f"
  else
   echo "Error: Cannot read $f"
  fi
done
/bin/rm $TFILE
```

But how do i get it to look through subfolders aswell?

---

### Post by geirha on 2009-09-14
```
find ~/foo -type f -name "*.txt" -exec sed -i~ 's/xyz/abc/' {} +
```

Check the man-page of (gnu) sed to see what the -i~ does. «man sed»

See this for other handy uses of the find command 

[http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

---

### Post by unavenged on 2009-09-14
Thanks... That helped alot :D

---

### Post by andrew.46 on 2009-09-16
Hi geirha,

> **geirha said:**
> 
See this for other handy uses of the find command 

[http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

A very nice page! I have taken the liberty of adding this page to the Ubuntu Community Documentation:

[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

Don't forget to to look at the truly amazing Nixie giving her own spin on using find, also linked from this page.

Andrew

---

