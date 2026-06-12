---
title: "Deploy multiple workstation"
date: 2006-05-08
forum: General Help
---

### Post by Koybe on 2006-05-08
Hello,

My question is in the title. I want to install 10 identical workstations with ubuntu. How can i proceed to make it as quick as possible?

I know how to to it by copying the list of packages : 
```
# dpkg --get-selections > pkglist.dpkg
# dpkg --set-selections < pkglist.dpkg
# dselect install
```
but anyway it needs installation on all post before.

Any possibilities to make some image or something like that?
I heard about FAI... but it's seems quite long to install for only 10pc...

Any ideas?

---

### Post by mips on 2006-05-08
You should be able to image the drive. Could use the linux dd command and a livecd ?

How would one then go about changing the computer/host name as they will all be identical.
Would be nice if you could setup one machine with all updates and all software you need etc and then image it.

---

### Post by Koybe on 2006-05-08
Yeah it's ok.
I'm looking to this tool too : looks nice.
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

