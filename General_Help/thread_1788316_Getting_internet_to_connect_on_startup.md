---
title: "Getting internet to connect on startup"
date: 2011-06-22
forum: General Help
---

### Post by whatthefunk on 2011-06-22
I want to run this at startup to start my internet connection.
```
poff -a
pon dsl-provider
```

I dont know why, but I have to run *poff -a* first or it wont connect.  pppoeconf does not start my connection at startup so I currently have to connect it manually every time I boot.  Any ideas?

---

### Post by dino99 on 2011-06-22
you might either:
- ask on launchpad to get a dev answer
- report a bug against pppoeconf

what give: sudo dpkg-reconfigure pppoeconf

---

### Post by iclestu on 2011-06-22
> **whatthefunk said:**
> I want to run this at startup to start my internet connection.
```
poff -a
pon dsl-provider
```I dont know why, but I have to run *poff -a* first or it wont connect.  pppoeconf does not start my connection at startup so I currently have to connect it manually every time I boot.  Any ideas?


you could certainally make it into a script to run at start up:

save a text file called "netStart.sh" or something with:

```

#!/bin/sh

poff -a
pon dsl-provider

```then save it in /etc/init.d/ directory and make it executable with

```
sudo chmod +x /etc/init.d/netStart.sh
```and finally run

```
sudo update-rc.d /etc/init.d/netStart.sh defaults
```but this seems like a helluva kludgy fix.

maybe someone else can help u set up your connection automatically?

---

### Post by iclestu on 2011-06-22
crosspost with dino99's reply.

suggest you follow his advice to try to get it working properly first before trying to kludge it :)

---

### Post by whatthefunk on 2011-06-22
> **iclestu said:**
> you could certainally make it into a script to run at start up:

save a text file called "netStart.sh" or something with:

```

#!/bin/sh

poff -a
pon dsl-provider

```

then save it in /etc/init.d/ directory and make it executable with

```
sudo chmod +x /etc/init.d/netStart.sh
```

and finally run

```
sudo update-rc.d
```

but this seems like a helluva kludgy fix.

maybe someone else can help u set up your connection automatically?

Ive been trying to do something like this, but I didnt know about the init.d directory and was saving my file in bin.  Learn something new everyday:)  That may have been why it didnt work.  Trying now...

---

### Post by iclestu on 2011-06-22
> **whatthefunk said:**
> Ive been trying to do something like this, but I didnt know about the init.d directory and was saving my file in bin.  Learn something new everyday:)  That may have been why it didnt work.  Trying now...

GL - i re-iterate the advice to try and fix properly tho! :)

---

### Post by iclestu on 2011-06-22
> **whatthefunk said:**
> Ive been trying to do something like this, but I didnt know about the init.d directory and was saving my file in bin.  Learn something new everyday:)  That may have been why it didnt work.  Trying now...

ooooo - and note my edited last command! Boy you got to that quick! Noticed and corrected my error as soon as I posted!

---

### Post by whatthefunk on 2011-06-22
Worked.  Thanks iclestu!  Ill look into the proper fix when I have the time.

---

### Post by iclestu on 2011-06-22
> **whatthefunk said:**
> Worked.  Thanks iclestu!  Ill look into the proper fix when I have the time.

:) my pleasure.

---

