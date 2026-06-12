---
title: "Broken Pango Packages, please help"
date: 2006-02-28
forum: General Help
---

### Post by Vadim on 2006-02-28
While trying to install a .deb of the newest version of gxine (gxine_0.5.4-0.1_i386) I had to install libpango and libpango-common which I could not do as the packages depended on each other (!?) as well as libglib2.0, libcairo2, and libxrender1. None of these could install as they depended on libpango. Now synaptic reports each of these as broken and wants to remove 200+ packages when I try to do anything at all; "apt-get -f install" acts similarly. Can anybody please help me?

---

### Post by Xian on 2006-02-28
[QUOTE=Vadim]I had to install libpango and libpango-common which I could not do as the packages depended on each other (!?) as well as libglib2.0, libcairo2, and libxrender1. None of these could install as they depended on libpango. [/QUOTE]

How could you have installed anything if apt would not let you because of dependency problems? Unless you used 'dpkg -i', in which case if all you did was install broken packages then they should be safely removed with '-f install', but you say this doesn't work. Can you be a little more specific on what (if anything) you did install and the method you used in your attempt?

---

### Post by RAOF on 2006-03-01
That gxine .deb came from a Debian source, didn't it :(

I'd suggest downloading the Ubuntu packages for the things you installed from [packages.ubuntu.com](packages.ubuntu.com) to a clean directory, and installing them with "sudo dpkg --install *.deb".  I **think** that should fix it.  Oh, and remove gxine.

---

### Post by Vadim on 2006-03-01
Thanks very much RAOF, that worked well, thanks for your help.

---

