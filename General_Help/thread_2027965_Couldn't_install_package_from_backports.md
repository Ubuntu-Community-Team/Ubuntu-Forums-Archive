---
title: "Couldn't install package from backports"
date: 2012-07-17
forum: General Help
---

### Post by avli on 2012-07-17
I've turn on backports repositories, because I want the latest QtCreator, that is *in* Precise backports. I'm doing:

```
$ sudo apt-get update
$ sudo apt-get upgrade

```

but QtCreator version is still 2.4.1 When I do:

```
$ apt-cache show qtcreator
```

I see, that the version is 2.4.1. What am I doing wrong?

---

### Post by avli on 2012-07-19
I solve the problem. Looks like backports reposity has lower priority, then other ones, so -t option should be used. In my case:

```
sudo apt-get install -t precise-backports qtcreator
```

---

