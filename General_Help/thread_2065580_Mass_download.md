---
title: "Mass download"
date: 2012-10-02
forum: General Help
---

### Post by alfirdaous on 2012-10-02
Hello there!!!

I would like to download media files with AVI axtension on the same file at once, how can I do it in a command line, contents are like below:
```

[www.site.com/folder/content.avi]("http://www.site.com/repertoire/contenu1.avi")
[www.site.com/folder/something.avi]("http://www.site.com/repertoire/autrechose.avi")
[www.site.com/folder/file.avi]("http://www.site.com/repertoire/fichier.avi")[www.site.com/folder/blabla.avi]("http://www.site.com/repertoire/blabla.avi")


```

I know this one:
```

wget www.site.com/folder/{1..100}.avi

```

but I don't have series, even with *.avi doesn't work

Thanks in advance

---

### Post by alfirdaous on 2012-10-02
[http://www.addictivetips.com/ubuntu-linux-tips/download-multiple-files-from-command-line-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/download-multiple-files-from-command-line-in-ubuntu-linux/)

---

### Post by alfirdaous on 2012-10-24
Re,

I created a backup folder in my server for MySQL database and some other fodlers, the format is like this:

> 
site.com/backup/site.com-var-lib-mysql.20121024.master.tar
site.com/backup/site.com-var-mail.20121024.master.tar
site.com/backup/site.com-var-www.20121024.master.tar
site.com/backup/site.com-home-site.20121024.master.tar


How can I download the folder content at once?

Thnx

---

### Post by dsv47 on 2012-10-24
_

---

### Post by BaardKopperud on 2012-10-24
Can't you just use something like "wget -r -l inf -np -A avi http://host/dir/index.html" ?

-r = recursive
-l inf = infinite level of recursive
-np = no parent; go down the directory-tree, not up
-A avi = Accept only files with the avi-extension

I think that it will still "look" at the html-files (with links to othe files) although it only *keeps* the AVI-files...

Apart from that, I very much like the lynx -dump/wget -i solution, and often use it myself.  

An alternative is to use wget to first get all the html-files (and PHP-files and other files of interest), and the use "find where-wget-downloaded -name "*.html" -exec lynx -dump {} \; | sed 's/^ *[0-9]*\. //p' | sort | uniq | fgrep ".avi" > avi-list" to get a list of all links to AVIs.

The sed-script finds all the links at the bottom of a lynx -dump output...

---

