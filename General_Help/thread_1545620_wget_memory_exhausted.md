---
title: "wget: memory exhausted"
date: 2010-08-04
forum: General Help
---

### Post by Freiburg05 on 2010-08-04
Hi there,

         I'm trying to use wget on an ubuntu 10.04 server 64bit, with 16GB RAM and 1.1 TB free disk space. It exits with the message "wget: memory exhausted". I'm trying to download 1MB of some sites. After different tries this is the command I'm using:

```
 wget -r -x -Q1m -R "jpg,gif,jpeg,png" -U Mozilla http://www.onesite.com
```

       (I only need the html documents, but when if I run the -A options only the first page is donwloaded, so I change to -R).


         This happens with wget 1.12 version. I've tried the same command in other computers with less RAM and disk space (ubuntu 8.04 - wget 1.10.2) and it works just fine.


       I'd be grateful if someone could give me a hint.


         Thanks in advance.

---

### Post by Freiburg05 on 2010-08-06
Hi again,

       For those who may have interest in this issue, as I understand from this [thread]("http://comments.gmane.org/gmane.comp.web.wget.general/9621"), it seems to be a bug in wget when processing css files. 
       If you specify not to download the css files, wget will work fine. This may not be a solution for everybody, but at least can be a workaround for some people.

     The command I posted in the previous message would then work as follows:
```
wget -r -x -Q1m -R "jpg,gif,jpeg,png,css,scss" -U Mozilla http://www.onesite.com
```

     Bye!

---

