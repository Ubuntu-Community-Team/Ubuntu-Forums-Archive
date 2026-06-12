---
title: "Problem finding mcopidl"
date: 2009-11-08
forum: General Help
---

### Post by rozen on 2009-11-08
Hi,

I recently installed 9.10 and I am trying to build an old KDE application that I like very much but I am stuck at the configure step. The error message that I get is:

configure: error: The important program mcopidl was not found!

According to the ubuntu package search the file used to be in the package "libarts1-dev" but that package doesn't seem to be available for karmic.  I would appreciate any suggestions as to where I could find the missing file or how to proceed.

Thanks in Advance,
Don

---

### Post by NFblaze on 2009-11-08
You shouldnt have an issue installing an older version like the one from [Intrepid Ibex release.]("http://packages.ubuntu.com/intrepid/libarts1-dev")

---

### Post by rozen on 2009-11-08
Thanks,

I manually installed the "libarts1-dev" and its dependencies from the ibex release and was able to build the application.

Thanks for your help,
Don

---

### Post by fmmarzoa on 2010-01-29
Where you find that package? it seems that's not on default repositories...

Anyway I've seen this:

[https://bugs.launchpad.net/ubuntu/+source/scim-pinyin/+bug/445658](https://bugs.launchpad.net/ubuntu/+source/scim-pinyin/+bug/445658)

So I've done 

./configure --without-arts 

And it worked fine.

---

