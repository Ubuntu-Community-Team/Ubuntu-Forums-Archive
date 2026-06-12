---
title: "Compiling Error"
date: 2006-06-11
forum: General Help
---

### Post by snakeyes37 on 2006-06-11
Hello,


I'm currently trying to install Network Manager 0.6.0 on my Ubuntu 6.06 but I keep receiving an error in my terminal when trying to configure.

```

checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

```


Any help would greatly be appreciated.


Thanks.

---

### Post by droazen on 2006-06-11
sudo apt-get install libxml-parser-perl

---

### Post by glotz on 2006-06-11
Try **sudo aptitude install libxml-parser-perl**

---

### Post by snakeyes37 on 2006-06-11
Thanks guys, I just downloaded NetworkManager from the download manager. But when I double click on NetworkManager nothing happens.

---

### Post by glotz on 2006-06-11
Try starting from terminal, so you'll see any errors it'll produce.

---

