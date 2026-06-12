---
title: "problem installing bashish"
date: 2010-07-25
forum: General Help
---

### Post by mamboze on 2010-07-25
I've downloaded bashish-2.2.4.tar.gz and extracted it. But where to go from here?

There is a shell script install-sh which I've attempted to run. 

sudo chmod +x install-sh

and then   install-sh

nothing happens.

Where am I going wrong here?

---

### Post by demosthenese on 2010-07-25
Looking at the freshmeat website at [http://freshmeat.net/projects/bashish]("http://freshmeat.net/projects/bashish") there is a debian package in the links box on the right. You could try downloading this and installing.

```
sudo dpkg -i /path/to/download/bashish_whatever.deb
```

I'm not familiar with bashish, so I cannot help with configuring it.

---

### Post by mamboze on 2010-07-25
Thanx demosthenese, your advice was spot on. Actually, I downloaded the tar file from that site but missed the deb. 

Roy

---

