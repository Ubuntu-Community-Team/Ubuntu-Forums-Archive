---
title: "remind me ... how to install not via Synaptic"
date: 2012-03-04
forum: General Help
---

### Post by engine on 2012-03-04
It's been a while, and I really don't want to damage anything …

So, I'm running Ubuntu 10.04 and I've just downloaded the .tar.gz for Ghostscript 9.04 in the hope this will solve some irritating PostScript problems. If someone could kindly and patiently remind me what I need to do with the unzipped contents of the archive?

Thanks in advance!

---

### Post by lechien73 on 2012-03-04
Have you extracted the .tar.gz file, and so have a ghostscript-9.04 folder?

If so, running the following commands in a terminal window should get it installed for you:

```
cd ghostscript-9.04
./configure
make
make install
```

---

### Post by mcduck on 2012-03-04
> **engine said:**
> It's been a while, and I really don't want to damage anything …

So, I'm running Ubuntu 10.04 and I've just downloaded the .tar.gz for Ghostscript 9.04 in the hope this will solve some irritating PostScript problems. If someone could kindly and patiently remind me what I need to do with the unzipped contents of the archive?

Thanks in advance!

There's no general instructions, as a .tar.gz is just an archive that can contain anything. Maybe it's source code that needs to be compiled, or perhaps a precompiled binary that you just need to extract somewhere. Maybe you need to install additional stuff or make some configurations by hand and maybe you don't....

The first thing to do is take a look in the archive itself, it should contain a text file with instructions. If it doesn't, check the web site where you downloaded it.

(In case of Ghostscript, it most likely is source code, and the process described by echien73 should be more or less correct)

---

