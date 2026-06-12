---
title: "Using Mono"
date: 2011-02-12
forum: General Help
---

### Post by layers on 2011-02-12
Well, I used Mono like shown bellow, and it ran the application once. I closed it, and tried to run this again, but nothing happens. Even if I add 2> error.log, the log is completely empty. Does anyone know what's happening here?
```
ibo@ibo-laptop:/media/IBO USB(K1/untitled folder 2/gMapMaker$ mono gMapMaker.exe
ibo@ibo-laptop:/media/IBO USB(K1/untitled folder 2/gMapMaker$ 

```

---

### Post by davidmohammed on 2011-02-12
maybe the proces itself hasnt stopped?

try

ps -ef | grep -i mono

or

ps -ef | grep -i gmapmaker

if the process is still visible - try forcing the process to stop

sudo kill -9 <process id>

---

### Post by layers on 2011-02-12
Sorry, again, I fixed it - it required sudo.

---

