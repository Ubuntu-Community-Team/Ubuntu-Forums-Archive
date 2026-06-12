---
title: "Delete duplicate files with different names"
date: 2010-08-18
forum: General Help
---

### Post by t0p on 2010-08-18
There are some files on my computer which have the exact same content but have different names.  How do I go about tracking them down?

---

### Post by sydbat on 2010-08-18
> **t0p said:**
> There are some files on my computer which have the exact same content but have different names.  How do I go about tracking them down?I don't know if there are any scripts for this. You might have to do it (ugh) manually.

Another thing to try is a content/keyword search.

---

### Post by sq7bti on 2010-08-18
[fdupes]("http://linux.die.net/man/1/fdupes")

---

### Post by t0p on 2010-08-18
> **sq7bti said:**
> [fdupes]("http://linux.die.net/man/1/fdupes")

Thanks for the tip. I shall check it out later today/tomorrow.

---

### Post by Manubundu on 2010-10-08
fdupes is awesomely simple and effective. Just used it to clean out my music folder, which has always been a mess. You know how it goes, somebody has a cool music library and you just copy his/her folder into yours. In the end you are stuck with lots of duplicates.

At first I run fdupes like this:

```
fdupes -R -d ../music
```I wanted to be safe and ran it with prompting me before every delete. But after 10 times making a ridiculous decision of which one of two identical file is better than the other. A just hit ctrl+c and run again without the prompt: 

```
fdupes -R -d -N ../music
```I went to get some coffee and by the time I got back I have gained about 6GB.

---

### Post by linux-hack on 2010-10-08
you can use a simple command like (diff) try a man diff

---

### Post by linux-hack on 2010-10-08
or something like this :

```

cd /path/to/wherever
for file in `ls *`
do
      cksum $file
done | awk '{ 
         arr[$1]++
         if(arr[$1]>1)  {print $0 }
         } ' > ./duplicate.files

```

---

### Post by linux-hack on 2010-10-08
or this one : 

```
OUTF=rem-duplicates.sh;
echo "#! /bin/sh" > $OUTF;
find "$@" -type f -exec md5sum {} \; |
    sort --key=1,32 | uniq -w 32 -d --all-repeated=separate |
    sed -r 's/^[0-9a-f]*( )*//;s/([^a-zA-Z0-9./_-])/\\\1/g;s/(.+)/#rm \1/' >> $OUTF;
chmod a+x $OUTF; ls -l $OUTF
```
[http://elonen.iki.fi/code/misc-notes/remove-duplicate-files/](http://elonen.iki.fi/code/misc-notes/remove-duplicate-files/)

---

