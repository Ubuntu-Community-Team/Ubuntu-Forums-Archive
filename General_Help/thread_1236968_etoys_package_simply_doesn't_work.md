---
title: "etoys package simply doesn't work?"
date: 2009-08-10
forum: General Help
---

### Post by akos.maroy on 2009-08-10
I just installed the etoys package, and it simply doesn't work:

```

$ etoys 
/usr/bin/squeakvm -encoding UTF-8 -vm-display-x11 -xshm /usr/share/etoys/etoys.image 
unknown option: -xshm
Usage: /usr/bin/squeakvm [<option>...] [<imageName> [<argument>...]]
       /usr/bin/squeakvm [<option>...] -- [<argument>...]

...

```

is this package simply bad?

---

### Post by Bert Freudenberg on 2009-08-11
That's a known packaging bug in squeak-vm:

[https://bugs.launchpad.net/ubuntu/+source/squeak-vm/+bug/329038](https://bugs.launchpad.net/ubuntu/+source/squeak-vm/+bug/329038)
[https://bugs.launchpad.net/ubuntu/+source/etoys/+bug/301190](https://bugs.launchpad.net/ubuntu/+source/etoys/+bug/301190)

A workaround is to remove the -xshm option from the etoys script as described in the report above (although then it will be slightly slower).

Or uninstall the Ubuntu etoys package, and install the DEB from Squeakland: 
[http://squeakland.org/download/](http://squeakland.org/download/)

- Bert -

---

### Post by alsroot on 2009-08-11
just a temporary decision,
use etoys from sugar-0.84 ppa
[https://launchpad.net/~alsroot/+archive/ppa](https://launchpad.net/~alsroot/+archive/ppa)

---

