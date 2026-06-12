---
title: "Get ?"
date: 2006-06-20
forum: General Help
---

### Post by darkowl on 2006-06-20
Why doesn't GET command work ?
How can i get web page in terminal ?

---

### Post by mjm115 on 2006-06-20
Get is an FTP command if I understand you correctly.  What exactly are you trying to do?  Your information is very vague.

---

### Post by Delkster on 2006-06-20
GET is a HTTP request method, not a UNIX console command.

However, there's a command-line utility called 'wget' which will allow you to retrieve files over HTTP and FTP. It's in the 'wget' package, in case that one isn't installed for you already. It won't show you the web page in any form, it will just retrieve the file.

If you want to view the web page rendered on the terminal (i.e. a text-mode web browser), look into 'links' or 'elinks' (it resides in the package called 'elinks').

---

### Post by tronica on 2006-06-20
i think your wanting links. 

> sudo apt-get install lynx

---

### Post by QUASAR_FREAK on 2006-06-20
Or links2 that supports web pages with frames and framebuffer :D

---

### Post by steve.horsley on 2006-06-20
[QUOTE=darkowl]Why doesn't GET command work ?
How can i get web page in terminal ?[/QUOTE]
Try these two commands as an example:
```
telnet www.ubuntuforums.org 80
GET /

```

---

