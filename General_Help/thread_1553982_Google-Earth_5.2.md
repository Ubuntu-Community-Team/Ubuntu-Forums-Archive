---
title: "Google-Earth 5.2"
date: 2010-08-15
forum: General Help
---

### Post by Yumi on 2010-08-15
Trying to install Google-Earth 5.2 on 10.04. Repositories contain 5.1

Downloaded GoogleEarthLinux.bin and die "Sudo CHMOD -x GoogleEarthLinux.bin". Then "./GoogleEarthLinux.bin".

**Get error**
$ ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.2.1.1547..............................................................
setup.data/setup.xml:1: parser error : Document is empty

^
setup.data/setup.xml:1: parser error : Start tag expected, '<' not found

^
Couldn't load 'setup.data/setup.xml'


Any advice?

Michael

---

### Post by wojox on 2010-08-15
Delete that version and try this [Howto – Linux – install Google Earth]("http://richs-lxh.linux-hardcore.com/2010/04/howto-linux-install-google-earth/")

---

### Post by jmfal on 2010-08-15
you have to add the medibuntu repository to install google earth

google medibuntu, follow directions to add repo, you can install G.E from there

but I would add repo then install using synaptic

---

### Post by Yumi on 2010-08-16
Thank you wojox. The instructions worked flawless. I can now use the new features of 5.2.

Jmfal, I had the version in the repositories which is 5.1. I wanted the Elevation Profile feature new in 5.2 and for this I have to download and install myself.

Michael

---

### Post by wojox on 2010-08-16
Your welcome. ;)

---

### Post by Yumi on 2010-09-03
Just to report that version 5.2 is working without problems in Maverick. Only once did not load the earth image due to "Graphic Card not found". It was due to a headers update and then did not recognise the "Noveau Driver". Installing Nvidia current driver solved this issue.

Michael

---

