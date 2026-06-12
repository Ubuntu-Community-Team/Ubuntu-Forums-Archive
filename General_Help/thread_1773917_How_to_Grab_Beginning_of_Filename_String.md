---
title: "How to Grab Beginning of Filename String?"
date: 2011-06-02
forum: General Help
---

### Post by Kissell on 2011-06-02
I have a bunch of files that I want to move to different locations, however the key to their location is stored within the filename, it is delimited by a space,hyphen,space combo " - ", so I would like to automate this move, because there are thousands of files.  

Below I have listed some example filenames, all files are in a single directory, I would like to move them into folders named "Tax Record" and "Inventory" respectively.  Can I somehow search the filename for everything before " - " and then pass that into a command that will move the file to a different location based on what it found in the filename?

Example Filenames:
/home/me/Tax Record - 2011.xls
/home/me/Tax Record - 2010.xls
/home/me/Tax Record - 2009.xls
/home/me/Inventory - 2011.db
/home/me/Inventory - 2010.db

Desired Result:
/media/Data/Tax Record/Tax Record - 2011.xls
/media/Data/Tax Record/Tax Record - 2010.xls
/media/Data/Tax Record/Tax Record - 2009.xls
/media/Data/Inventory/Inventory - 2011.db
/media/Data/Inventory/Inventory - 2010.db

NOTE: I don't want a utility, I want to be able to script this, because I want cron to do this automatically for new/future files.

---

### Post by TeoBigusGeekus on 2011-06-02
```
#!/bin/bash
find ./ -type f ! -name "*script*"|while read f;
do
   fn=$(echo $f|sed 's/ -.*//g')
   mkdir "/media/data/$fn"
   mv "$f" "/media/data/$fn"
done

```
Name it as script and run it in the folder where the files are.

---

### Post by Kissell on 2011-06-03
Thanks a lot, that works great!

---

