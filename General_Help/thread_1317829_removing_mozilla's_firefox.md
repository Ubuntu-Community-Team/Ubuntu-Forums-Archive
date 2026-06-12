---
title: "removing mozilla's firefox"
date: 2009-11-07
forum: General Help
---

### Post by stvdel on 2009-11-07
Hello, I already had Ubuntu's 3.5.4 firefox installed on 9.10 then I installed 3.5.5 with this 
wget -P ~ [ftp://ftp.mozilla.org/pub/firefox/releases/3.5.5/linux-i686/en-US/firefox-3.5.5.tar.bz2](ftp://ftp.mozilla.org/pub/firefox/releases/3.5.5/linux-i686/en-US/firefox-3.5.5.tar.bz2) && tar xjf ~/firefox-3.5.5.tar.bz2 -C ~
My question is, what would be the correct command to use to remove this version and keep the Ubuntu version in place?

---

### Post by ibutho on 2009-11-07
The command you used to install Mozilla Firefox does not overwrite the Ubuntu Firefox, so you can just use "rm" (or nautilus) to delete the Mozillas firefox directory e.g. "rm -rf /path/to/firefox". Be careful of "rm -rf" because its effects are irreversible.

---

### Post by stvdel on 2009-11-08
Ok thanks, I knew that it did not overwrite Ubuntu's I just wanted to make sure that if I issued the remove command that it would not effect my profile or anything.
Thanks,

---

