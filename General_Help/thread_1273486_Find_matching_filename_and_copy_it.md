---
title: "Find matching filename and copy it"
date: 2009-09-23
forum: General Help
---

### Post by 3L33T on 2009-09-23
Hello ubuntu colleagues,

I'm not sure if this is the right place to post this question, so moderator please feel free to move to appropriate thread section.

I need ideas on how to:

  1) find a file or bunch of files in a folder that contains thousands of PDF files.
  2) once found, copy it onto another folder.

The list of file I want to copy is contained in a text flatfile that has one column and one line per column.  

My script is as follows:

```


for i in `/bin/cat $flatfile`
   do
      echo "Searching for $i"
      if [ `find /pdfdir -name "*$i*" -print -exec \
        /bin/cp -fp "{}" /copydir \;` ] ; then
          echo "Found matching "$i"
      else
         echo " `basename $i` Not Found"
         sleep 2
      fi
   done

```

Any suggestions on how to improve it for speed and accuracy?

---

### Post by scragar on 2009-09-23
I think building a list of files, then grepping it down as needed might be more efficient than searching all the directories every time the script loops.

---

### Post by 3L33T on 2009-09-23
> **scragar said:**
> I think building a list of files, then grepping it down as needed might be more efficient than searching all the directories every time the script loops.

:confused:](*,)

---

### Post by DaithiF on 2009-09-23
Hi, something like this:
```
while read file; do [[ -e "/pdfdir/$file" ]] && cp "/pdfdir/$file" /copydir || echo "Not found: $file"; done < list
```

where list is the name of the file containing the filenames

---

### Post by 3L33T on 2009-09-23
> **DaithiF said:**
> Hi, something like this:
```
while read file; do [[ -e "/pdfdir/$file" ]] && cp "/pdfdir/$file" /copydir || echo "Not found: $file"; done < list
```

where list is the name of the file containing the filenames

THIS is clean and simple.  I ran it and it actually works fast.

Now the following issues came up:

1) My list of filenames in the flatfile does not have the file extensions, only the filename.   :(

2) The actual files in the folder have either a ".pdf" or ".PDF" extension.   

How do I make sure the script finds and copies the right file?

---

### Post by DaithiF on 2009-09-23
hmm, i'm sure theres probably neater ways, but in the absence of one occurring to me, heres a brute-force-ish approach 
```
sed 'h;s/$/.pdf/;p;g;s/$/.PDF/' list | while read file; do [[ -e "/pdfdir/$file" ]] && cp "/pdfdir/$file" /copydir || echo "Not found: $file"; done
```

---

### Post by DaithiF on 2009-09-23
if you don't care about reporting files which aren't found, then this is may be simplest:
```
while read file; do cp -t /copydir /pdfdir/$file.[pP][dD][fF]; done < list
```

---

