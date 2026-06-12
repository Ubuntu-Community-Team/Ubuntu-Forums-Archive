---
title: "Output files containing search term"
date: 2010-02-25
forum: General Help
---

### Post by JoeEndUser on 2010-02-25
I would like to search for a term within a batch of text files and copy the files containing that term to a folder. 

I've read the man pages for Grep, Ack-grep and looked through nautilus, dolphin, midnight commander as well as tried beagle, tracker and google desktop (and looked throught these forums). 

I can do this function easily with xp's wagging dog in the Windows search, but would like to find a way in Linux.

If anyone has any ideas, I would be grateful.

---

### Post by cjhabs on 2010-02-25
Try:
cd root_of_search_folders
find . -exec grep "text to find" {} -ls \;| xargs -I {} mv {} ../output_folder

You'll need to screw around with extra options if there are spaces in the filenames.

---

### Post by geirha on 2010-02-25
A safer one that will handle filenames containing spaces and oddities.
```
find . -name "*.txt" -exec grep -q 'searchterm' {} \; -exec cp {} "/path/to/dest" \;
```

See [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind) for more.

---

### Post by cjhabs on 2010-02-25
Sweet!

---

### Post by JoeEndUser on 2010-02-25
Thanks. I will try them out. By the way is there a more advanced guide for grep that you refer to? If so, please share.

---

### Post by JoeEndUser on 2010-02-25
Oops, missed the wiki link above the first time. Thanks again.

---

