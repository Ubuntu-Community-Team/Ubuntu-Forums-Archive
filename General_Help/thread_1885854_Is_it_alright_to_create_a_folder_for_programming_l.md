---
title: "Is it alright to create a folder for programming libraries under usr?"
date: 2011-11-24
forum: General Help
---

### Post by skytreader on 2011-11-24
A friend noticed that I put my Java libraries under /usr/import where import is a folder I created myself (to mirror the include folder for C libs). I did this since, well, looks logical as most libraries/headers reside there anyway. However, she told me that this isn't a very wise decision, pointing to [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html) where it says that

> Large software packages must not use a direct subdirectory under the /usr
hierarchy.

Will Java libs fall under this clause? My set-up has been like this for around half-a-year or so and I haven't any problems with it. My import folder isn't really big (just around 11.7MB) but I'd just like to be ready in case it gets bloated up in the future. It wouldn't really bother me to change my Java library folder, I'd just change a few lines in my ~/.bashrc but, well, I like my organization that way.

Any thoughts?

---

