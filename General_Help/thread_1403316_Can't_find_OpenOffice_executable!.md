---
title: "Can't find OpenOffice executable!"
date: 2010-02-10
forum: General Help
---

### Post by buckteeth7 on 2010-02-10
Hi,

Because my internet doesn't work on my laptop, I installed OpenOffice through the debian package manager. Everything worked to perfection, except that I couldn't find the executable file!

I did a search of the computer for files with "openoffice" in their name, but none would open as an executable. It's not in any menu either.

Could someone please tell me where it is?

Thanks,

BuckTeeth7

---

### Post by mechro on 2010-02-10
Try **ooffice -writer** from a Terminal. That'll at least tell you if it's installed.

Do you have to make your own launchers for openoffice in xubuntu??

---

### Post by buckteeth7 on 2010-02-10
It wouldn't accept the **oofice **command as a command, but I read that **soffice -writer** would work. So, I tried that. Terminal told me the thing wasn't installed. I reinstalled it with the debian package manager (which had a reinstall button instead of an install button) and tried again with synonymous results.

---

### Post by mcduck on 2010-02-10
The correct command is "ooffice -writer", or "oowriter", just like mechro suggested. (soffice would be related to StartOffice, the commercial verison of OpenOffice)

Could you tell exactly how you installed OpenOffice? It really sound like it's not correctly installed on your system..

---

### Post by buckteeth7 on 2010-02-10
I copied the file "OOo_3.1.1_LinuxIntel_install_en-US_deb.tar.gz". I extracted the folder inside to the desktop.  Next, I opened that folder, then opened the DEBS folder inside, then opened the desktop-integration folder inside that and then opened the file "openoffice.org3.1-9420_all.deb". This brought up the Debian Package manager and the file, and I clicked the install button. I waited a short while, and the process was complete.

---

### Post by llamabr on 2010-02-10
The point is, in your post, you said that you typed 

```
oofice
```

but the correct command is

```
ooffice
```

just open a terminal, type

```
ooffice
```

and press enter.  it should start.

---

### Post by Vaphell on 2010-02-10
using tab to suggest/autocomplete helps with typos
**o[tab][tab]** = you get all valid commands starting with o.

---

### Post by buckteeth7 on 2010-02-12
Thankyou all, the command that terminal was asking for was: ```
openoffice.org3
```

Terminal said it should be in the directory ```
opt/openoffice.org3/program/soffice
```

When I searched for files with "openoffice" in their name, they all turned up in "usr" and its subdirectories. "opt" was empty and I couldn't move any file to there. Debian doesn't let me change where files go either.

---

### Post by Hagar Delest on 2010-02-13
> **buckteeth7 said:**
> I copied the file "OOo_3.1.1_LinuxIntel_install_en-US_deb.tar.gz". I extracted the folder inside to the desktop.  Next, I opened that folder, then opened the DEBS folder inside, then opened the desktop-integration folder inside that and then opened the file "openoffice.org3.1-9420_all.deb". This brought up the Debian Package manager and the file, and I clicked the install button. I waited a short while, and the process was complete.

You've only installed the menus! This is the last step. See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Note that the package manager also use the internet connection (except if you've the install CD or DVD). So I don't really understand your first post.

---

### Post by buckteeth7 on 2010-02-16
I downloaded it from the OpenOffice site and installed in manually using the Debian Package manager. It's not the regular package manager, but a different one.

---

