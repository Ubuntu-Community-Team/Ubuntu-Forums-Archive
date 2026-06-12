---
title: "Where is the md5 for 10.04??"
date: 2010-04-29
forum: General Help
---

### Post by kakyoism on 2010-04-29
Can't find the checksum code on 
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Should I look elsewhere?

Thanks!

---

### Post by darolu on 2010-04-29
[http://releases.ubuntu.com/releases/10.04/MD5SUMS](http://releases.ubuntu.com/releases/10.04/MD5SUMS)

---

### Post by ddreamer on 2010-08-19
After you download .iso file, you can check MD5SUMS
Download from [http://releases.ubuntu.com/releases/10.04/MD5SUMS](http://releases.ubuntu.com/releases/10.04/MD5SUMS) and save it as MD5SUMS in the same directory of .iso file
In terminal at the same directory, type:

md5sum -c MD5SUMS

---

