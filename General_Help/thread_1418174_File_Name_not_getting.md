---
title: "File Name not getting"
date: 2010-02-28
forum: General Help
---

### Post by CatchItBaby on 2010-02-28
How to find filename and file path from a string

---

### Post by chuina on 2010-02-28
> **CatchItBaby said:**
> Found.. it

Found what ? Share with us.;)

---

### Post by CatchItBaby on 2010-02-28
basename command i was missing ; at last :D

My first post updated

---

### Post by Barriehie on 2010-02-28
> **chuina said:**
> Found what ? Share with us.;)

+1, yeah, how did you do it???

---

### Post by Richard1979 on 2010-02-28
locate /path/file ?

---

### Post by Barriehie on 2010-02-28
I got it like this, but can't get it to exclude the directories!
```

ls -Ra1 | gawk '{ if($0 !~ /^\./ && $0 !~ /^$/) { print $0 }}'

```

---

### Post by CatchItBaby on 2010-02-28
echo $(basename pathofyourfoldername);

---

### Post by kaibob on 2010-02-28
> **CatchItBaby said:**
> echo $(basename pathofyourfoldername);

You can also use parameter expansion to get the file name and path:

> $ string="/home/kaibob/documents/file.txt" ; echo "${string##*/}"
file.txt
$
$ string="/home/kaibob/documents/file.txt" ; echo "${string%/*}"
/home/kaibob/documents

For more information on parameter expansion:

[http://bash-hackers.org/wiki/doku.php/syntax/pe](http://bash-hackers.org/wiki/doku.php/syntax/pe)

---

