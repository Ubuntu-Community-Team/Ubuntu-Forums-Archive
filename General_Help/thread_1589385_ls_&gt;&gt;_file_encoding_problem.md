---
title: "ls &gt;&gt; file: encoding problem"
date: 2010-10-06
forum: General Help
---

### Post by Ubentoo on 2010-10-06
Hello,doing ls gives me a list of files of the current directory, encoding fine. Doing ls >> file gives me the same list in the file 'file', but the encoding seems to be broken (eg german umlauts). Why is there a difference between screen output and output forwarded to a file and how do I solve the problem?Thanks a lot,Ubentoo

---

### Post by Ubentoo on 2010-10-18
Does anybody have an idea?

---

### Post by Vaphell on 2010-10-18
what do you use to open the file?
i tested it with polish chars and ls showed them fine but i had to set gedit to open the file with utf-8, otherwise i was getting garbage (2 random 1-byte chars instead of 1 2-byte utf one).

---

### Post by Ubentoo on 2010-10-19
I am sorry, I must have done something wrong. I was sure that the problem occurred even when I did a "cat", but now it seems to be only kate (which uses iso 8859-15 for compatibility reasons). Switching to UTF-8 in kate solved the problem. Thank you very much!

---

