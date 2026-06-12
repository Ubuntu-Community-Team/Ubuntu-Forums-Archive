---
title: "Find programs installed on a specific date"
date: 2010-09-04
forum: General Help
---

### Post by Steve00 on 2010-09-04
Is it possible to find programs that were installed on a specific date or within a specific date range? If so, how?

Thanks.

--Steve

---

### Post by Revolutionary101 on 2010-09-04
As of right now there is no way to see when software was installed. Although, in Ubuntu 10.10, there will be a history page in the Ubuntu Software Center.

---

### Post by kmsalex on 2010-09-04
you could go into your home folder enable show hidden files (view>show hidden files) find the program folder right click on it select propertys and there should be the date it was installed and the last modifications to it. aside from that i don't know of anyway to do this.

---

### Post by d3v1150m471c on 2010-09-04
you can't.

---

### Post by dcstar on 2010-09-04
> **Steve00 said:**
> Is it possible to find programs that were installed on a specific date or within a specific date range? If so, how?

Thanks.

--Steve
This should give you the whole lot, pipe it through other programs to trim it:
```
ls /var/lib/dpkg/info/*.list -lh
```

Also:
[http://mavior.eu/apt-log/](http://mavior.eu/apt-log/)

---

### Post by oldos2er on 2010-09-04
In Synaptic Package Manager, click File, History.

---

### Post by Steve00 on 2010-09-06
> **oldos2er said:**
> In Synaptic Package Manager, click File, History.

Thanks. I am running Ubuntu 8.10; are there circumstances under which a program could be installed and not show up in the Synaptic Package Manger's history logs?

---

