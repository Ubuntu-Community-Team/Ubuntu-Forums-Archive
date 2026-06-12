---
title: "update manager not updating"
date: 2009-08-18
forum: General Help
---

### Post by mickyboy on 2009-08-18
Stumped again...

For some reason my update manager has decided not to cooperate. I haven't changed anything as far as I know but I am a fiddler so it's quiet possible I have inadvertently done just that. Not too hot with Linux being a recent convert so still fumbling my way around.
Any help (basic instructions pls) would be greatly appreciated. Can't seem to copy and paste here so have taken a pic of the result of my trying to update. Again, thanks for any help..

(ubuntu 9.04)

---

### Post by zvacet on 2009-08-18
Type in terminal

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by michy99 on 2009-08-18
Run this in a terminal:```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 437D05B5
```

---

### Post by upstatelabs on 2009-08-24
> **zvacet said:**
> Type in terminal

```
sudo apt-get update && sudo apt-get upgrade
```

I was also having trouble with a frozen update manager (Hardy 8.04).  It was working fine, then without warning one day recently it decided to stop as soon as I clicked "install updates".  This fix worked for me, and my updates went through.

edit: I have to do this every time there are updates, the update manager still freezes when I try to click "update"

---

