---
title: "Update Manager and Computer Janitor are not working"
date: 2010-02-15
forum: General Help
---

### Post by Sihle on 2010-02-15
Hello I'm very new to Ubuntu and installed 9.10 a couple of months ago.  Since I've been using ubuntu I've been accustomed to updating manually from time to time.  When I attempt to update now using the Update Manager it fails and produces the following error message details:

"W: Unable to read /etc/apt/apt.conf.d/ - FileExists (2: No such file or directory)
W: Unable to read /etc/apt/sources.list - FileExists (2: No such file or directory)
W: Unable to read /etc/apt/sources.list.d/ - FileExists (2: No such file or directory)
W: Unable to read /etc/apt/sources.list - FileExists (2: No such file or directory)
W: Unable to read /etc/apt/sources.list.d/ - FileExists (2: No such file or directory)"

I also would like to note that Computer Janitor is also not functioning and produces the following error message: 

"Essential package dash is missing. There may be problems with apt sources.list or Packages files may be missing?"

Does anyone know any fixes for this?  I suspect these problems are related but have no idea, any help anyone could provide would be greatly appreciated.  Thanks

---

### Post by mk1w86 on 2010-02-15
Could you please post what happens when you run:

```
sudo apt-get update
```

---

