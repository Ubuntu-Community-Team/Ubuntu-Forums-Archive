---
title: "Search problem in File Browser"
date: 2009-07-26
forum: General Help
---

### Post by bob98122 on 2009-07-26
I have the following file on my hard disk:

/home/bob/.opera/cache4/temporary_download/firefox-3.5.1.tar.bz2

However, when I search the "File System" in Ubuntu 8.04 for "firefox-3.5.1.tar.bz2" it does not return any results, even though the file does exist. I copied the file to another drive and when I then searched the "File System" it found the copy on the other drive but not the one above.

Any ideas on why the search function in the file browser is not finding this file?

---

### Post by grayn0de on 2009-07-26
In the file browser (Nautilus) Go to Edit>Preferences ad select Show Hidden and Backup files. 

the./opera is a hidden folder. Find will not search inside them unless you are root.

Alternately, you can type the following into terminal:

```
sudo mv /home/bob/.opera/cache4/temporary_download/firefox-3.5.1.tar.bz2 /home/bob
```

That will pull the file out of that hidden folder to your home folder.

---

### Post by bob98122 on 2009-07-26
Thx. But the "Show Hidden and Backup files" option was already enabled. I also tried opening Nautilus through command line "sudo nautilus" assuming I would be opening it as admin, but it still won't find this file.

The other option only works if I know the location of the file, in which case I wouldn't be doing a search for it.

---

### Post by PGScooter on 2009-07-26
bob,

Can you please file a bug report? [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

In the meantime, you can search from the commandline. I prefer this to searching on nautilus:
```
find ~/ -iregex firefox.*
```
Does that find it?
Read ```
man find
```

---

