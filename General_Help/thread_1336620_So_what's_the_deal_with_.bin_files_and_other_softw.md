---
title: "So what's the deal with .bin files and other software packs?"
date: 2009-11-24
forum: General Help
---

### Post by Ubu4moi on 2009-11-24
I'm new with Ubuntu and sometimes I download software that doesn't come in a .deb file. What's the deal with .bin and other packs that come with a makefile file, etc.? Are there any easy instructions to install these?

---

### Post by The Cog on 2009-11-24
See [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

.bin might be an executable file, like the java installers from Sun. If so, make the file executable with the command:
**chmod +x *filename* **
then execute it with the command:
**./*filename***
but only do this if you trust the software source. Doing this kind of thing should really be a last resort.

---

