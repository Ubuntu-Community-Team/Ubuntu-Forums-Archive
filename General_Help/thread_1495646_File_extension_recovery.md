---
title: "File extension recovery"
date: 2010-05-28
forum: General Help
---

### Post by verdomde on 2010-05-28
Hi. I've been moving all my music to windows via an external hard disk- I'm trying to convert 20,000 pus files, all in different formats, re-organising as it's done and deleting the originals- overwriting duplicates- there is no way i can do this in ubuntu- so i'm using media monkey
My problem is the file extension- somehow all the file extensions are missing. I dont know how. BUt I need them back- ubuntu recognises the files and plays them, so it must be possible to recover the file extensions, as a batch?
Thanks
Paul

---

### Post by mike555 on 2010-05-28
if the extensions don't show on Windows , do other extensions show ? if not you need to uncheck "hide file extensions" in Windows ..

---

### Post by verdomde on 2010-06-01
Hey, the files definatley have no extensions. Windows would recognise them otherwise. Thanks

---

### Post by StuartN on 2010-06-01
> **verdomde said:**
> it must be possible to recover the file extensions, as a batch?

This is a bit kludgey, but try (on a backup first):

```
for file in *([^\.]) ; do
  if file "$file" | grep -q "MPEG ADTS, layer III" ; then
    mv "$file" "$file.mp3"
  fi
done
```

This should locate using ***([^\.])** all files that have no file extension, so that it does not do it twice, then identifies MP3 files by the output from the **file** command, and renames them with the .mp3 extension.

Use **file *** to find the other strings and file extensions you need for your files.

---

### Post by verdomde on 2010-06-01
thats superb thanks a lot, that works a treat.Is there some way to scan recursively?
thanks

---

### Post by mike555 on 2010-06-01
> **verdomde said:**
> Hey, the files definatley have no extensions. Windows would recognise them otherwise. Thanks

  Windows doesn't know a file if it doesn't have an extension ...

---

### Post by StuartN on 2010-06-02
> **verdomde said:**
> thats superb thanks a lot, that works a treat.Is there some way to scan recursively?
thanks

Yes, you can use find to serve up all filenames without a "." (one per line) to the for loop, and set the input field separator IFS to newlines - the only change in code is the "file in ..." bit:

```
IFS=$'\n'
for file in $(find . ! -iname "*.*") ; do
  if file "$file" | grep -q "MPEG ADTS, layer III" ; then
    mv "$file" "$file.mp3"
  fi
done
```

---

