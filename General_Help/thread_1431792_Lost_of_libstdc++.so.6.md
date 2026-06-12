---
title: "Lost of libstdc++.so.6"
date: 2010-03-17
forum: General Help
---

### Post by Sapfeer on 2010-03-17
Hi! I'm using Ubuntu Karmic on Lenovo S10-2 and unintentionally I've lost libstdc++.so.6. How can I recover it?..

Thanks in advance

---

### Post by sikander3786 on 2010-03-17
Hi.

I think libstdc++.so.6 has been removed from the repositories.

You can get it here.

[http://packages.debian.org/stable/base/libstdc++6](http://packages.debian.org/stable/base/libstdc++6)

Download additional dependencies if needed. And install them before installing libstdc++.so.6.

There should be many other ways but I think this is the easiest one.

Hope that helps.

Sikander.

---

### Post by Sapfeer on 2010-03-17
> **sikander3786 said:**
> Hi.

I think libstdc++.so.6 has been removed from the repositories.

You can get it here.

[http://packages.debian.org/stable/base/libstdc++6](http://packages.debian.org/stable/base/libstdc++6)

Download additional dependencies if needed. And install them before installing libstdc++.so.6.

There should be many other ways but I think this is the easiest one.

Hope that helps.

Sikander.

Thanks a lot for your such a quick answer. I tried this way, but there are a few dependencies of package libstdc++6. Then amount of dependencies of dependencies grows very fast - installing all of them is a very time consuming procedure. Hope there some other way to recover this library...

---

### Post by sikander3786 on 2010-03-17
There should not be a lot of dependencies I hope. You can check for dependencies in GDebi or what ever debian package manager you use.

It is worth giving it a try this way.

Or wiser heads than mine will have to jump in.

Regards.

---

### Post by Sapfeer on 2010-03-17
> **sikander3786 said:**
> There should not be a lot of dependencies I hope. You can check for dependencies in GDebi or what ever debian package manager you use.

It is worth giving it a try this way.

Or wiser heads than mine will have to jump in.

Regards.
Unfortunately there are... If it is the only way, I will have to install all of them.

Anyway, since I'm using Ubuntu Karmic, I may use some tools from apt package, but it doesn't work without libstdc++.so.6

---

