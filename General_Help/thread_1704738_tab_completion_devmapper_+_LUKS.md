---
title: "tab completion /dev/mapper + LUKS"
date: 2011-03-11
forum: General Help
---

### Post by give.away on 2011-03-11
Hello,

in the past I was able to tab complete the following statement
```
sudo mount /dev/mapper/s
```
after I opened an encrypted partition via
```
sudo cryptsetup luksOpen /dev/sda secret
```.

Since a few weeks, without consciously changing anything, this doesn't work anymore. Where is the tab completion behavior defined? How can I get the previous behavior back?

(It is all about tab completion, mounting and other related stuff still works.)

Thanks!

---

