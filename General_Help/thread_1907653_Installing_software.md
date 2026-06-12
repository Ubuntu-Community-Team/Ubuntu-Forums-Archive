---
title: "Installing software"
date: 2012-01-11
forum: General Help
---

### Post by Geostr on 2012-01-11
I'm a total newb and I really want to get the hang of at least the basics. Is there a basic primer somewhere? I want to use Ubuntu on an HTPC. I can't figure out how to install XBMC. I get a "fix broken packages first" error msg.

---

### Post by mikewhatever on 2012-01-11
To fix a broken package, you should open a terminal window and run the following:

```
sudo apt-get install -f
```

---

### Post by pr3zident on 2012-01-11
> **Geostr said:**
> I'm a total newb and I really want to get the hang of at least the basics. Is there a basic primer somewhere? I want to use Ubuntu on an HTPC. I can't figure out how to install XBMC. I get a "fix broken packages first" error msg.

try this to install XBMC

```

sudo add-apt-repository ppa:team-xbmc/unstable
sudo apt-get update
sudo apt-get install xbmc

```

---

### Post by Geostr on 2012-01-12
> **pr3zident said:**
> try this to install XBMC

```

sudo add-apt-repository ppa:team-xbmc/unstable
sudo apt-get update
sudo apt-get install xbmc

```

YES! Thank you!

---

### Post by pr3zident on 2012-01-12
> **Geostr said:**
> YES! Thank you!

No problem ....

---

