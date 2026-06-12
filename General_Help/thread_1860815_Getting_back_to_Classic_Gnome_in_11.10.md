---
title: "Getting back to Classic Gnome in 11.10"
date: 2011-10-15
forum: General Help
---

### Post by JesusM on 2011-10-15
There is an 'sticky' with a solution, but it doesn't work for me:

```

jesusm@stilgar:~$ sudo apt-get install gnome-session-fallback
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-session-fallback is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gnome-session-fallback' has no installation candidate
jesusm@stilgar:~$ 
```

---

### Post by coffeecat on 2011-10-15
Make sure you have the Universe repository enabled - Software Centre -> Edit -> Software Sources. Then close Software Centre, and:

```
sudo apt-get update
```

Then you should be able to install gnome-session-fallback

---

### Post by JesusM on 2011-10-15
Is it ok?

[IMG]http://img263.imageshack.us/img263/7238/sourcecj.png[/IMG]

But now I think the problem is with the Server in Spain. I've tried with 'Main server' and it seems to work fine.

Thanks

---

### Post by coffeecat on 2011-10-15
I'm glad changing the server worked. Sometimes the regional servers get out of sync or are being maintained. It's been a busy time lately for all the servers!

---

