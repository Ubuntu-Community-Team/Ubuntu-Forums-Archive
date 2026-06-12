---
title: "How to install or Convert .pkg files"
date: 2009-10-23
forum: General Help
---

### Post by christoforever on 2009-10-23
I've been given a .pkg file for a program I need for work ... but I only use Ubuntu. This file type I believe is for Solaris but I could be mistaken. I was wondering how to install this type under Ubuntu or to convert it to some other installable format?

---

### Post by gjoellee on 2009-10-23
> **christoforever said:**
> I've been given a .pkg file for a program I need for work ... but I only use Ubuntu. This file type I believe is for Solaris but I could be mistaken. I was wondering how to install this type under Ubuntu or to convert it to some other installable format?

As far as I know a .pkg is for Mac ([http://www.fileinfo.com/extension/pkg](http://www.fileinfo.com/extension/pkg)) and there is no Mac emulator for Linux available. What program is it, maybe the same program has support for Linux or maybe it is possible to use a similar program?

---

### Post by diesch on 2009-10-23
Solaris packages are called .pkg, too.

If it is a Solaris package the software most likely doesn't run on Linux. maybe you can run OpenSolaris in VirtualBox and install it there.

---

### Post by AlphaLexman on 2009-10-23
There is a package converter call alien. I used it once. I'm pretty sure it is in the repo's.

---

### Post by niteshifter on 2009-10-23
Hi,

AFIK, there is no conversion tool other than alien for that. It may work, it may not. Depends upon what the pkg item does and how it does it.

```
sudo apt-get install alien
```

But you might try searching - or tell us what the package is/does - there might be a Linux (.deb package) available. That's generally a no-hassle way to go.

If it's a Solaris / OpenSolaris package file, the source is may be available from the source tree at opensolaris.org - you could grab that and attempt building it. 

Another option is to virtualize OpenSolaris and install the package on that. I run OpenSolaris (2009.06) in VirtualBox, works fine but no sound. There's a fix for that but as I don't need sound in OpenSolaris it's not high on my to-fix list.

---

### Post by christoforever on 2009-10-23
Thanks for the help guys but the problem is now solved. I got the package from a guy at work when I asked him for a linux version of Cisco's vpn client ... I assumed he knew what he was talking about when he gave me a .pkg file. After I posted here I caught up with him and told him what was going on and he apologized and sent me a version specific to linux. So I'm good now. Thanks.

---

