---
title: "Downloading question"
date: 2010-12-07
forum: General Help
---

### Post by el_diablo on 2010-12-07
[SIZE=4]hi.
is it possible to pause th downloading from terminal.n how can i resume from same statu[/SIZE]s.

---

### Post by zvacet on 2010-12-07
I don´t think it is good idea to pause stop download,bevause after that you can run in many problems like getting errors and so...Why would you like to stop download in first place?

---

### Post by el_diablo on 2010-12-10
actually my net connection is quite poor.downloading need to stop other works

---

### Post by nothingspecial on 2010-12-10
Use wget with the -c flag

```
wget http://link_to_file
```

Ctrl-C to stop

then
```

wget -c http://link_to_file
```

---

