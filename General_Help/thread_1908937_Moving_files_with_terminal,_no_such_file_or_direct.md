---
title: "Moving files with terminal, no such file or directory"
date: 2012-01-14
forum: General Help
---

### Post by speud on 2012-01-14
Hi, I'm trying to move some files over to the linux kernel and it always says cannot stat no such file or directory. The files are in my home folder. I did: 
[COLOR=#ff0000]*[I]sudo mv iwl-sta.c iwl-tx.c iwl-agn.c /usr/src/linux-source-3.0.0/drivers/net/wireless/iwlwifi*[/I][/COLOR] 
and then it says cannot stat iwl-sta.c no such file or directory


Can someone help me out?

---

### Post by Lars Noodén on 2012-01-14
[mv](http://manpages.ubuntu.com/manpages/oneiric/en/man1/mv.1.html) takes only two arguments, a source and a destination.  Are you really trying to do something like this instead?

```

sudo mv iwl-sta.c /usr/src/linux-source-3.0.0/drivers/net/wireless/iwlwifi 
sudo mv iwl-tx.c /usr/src/linux-source-3.0.0/drivers/net/wireless/iwlwifi 
sudo mv iwl-agn.c /usr/src/linux-source-3.0.0/drivers/net/wireless/iwlwifi 

```

---

### Post by speud on 2012-01-14
It still says no such file or directory. Is there somewhere these files need to be for it to find them?

---

### Post by Lars Noodén on 2012-01-14
They have to be in the current working directory or else you have to specify the full path.  You can see which directory you are in (the working directory) with [pwd](http://manpages.ubuntu.com/manpages/oneiric/en/man1/pwd.1.html).  You can see which files are in the working directory with [ls](http://manpages.ubuntu.com/manpages/oneiric/en/man1/ls.1.html).  If the files you are trying to move are not there, then you'll have to either write the full path or else move to that directory before trying to move them.

---

### Post by speud on 2012-01-14
Ok, I put the files in the working directory and now it works. Thanks.:D

---

