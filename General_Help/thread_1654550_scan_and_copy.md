---
title: "scan and copy"
date: 2010-12-28
forum: General Help
---

### Post by jmggs on 2010-12-28
i have a Linux server that i have instaled and i have a samba share. the Linux is connected to internet LAN from one card and the other card is connect to LAN (no internet access
)

I want to scan a folder (watch folder) (that internet LAN have acess) and them if don't have virus copy to other folder (LAN acess) if have virus just remove. the anti-virus that i am using is clam av and the Linux

help! i have no idea how to do it!

Thanks

---

### Post by kidders on 2010-12-29
Hi there,

What options are realistic depends on a few things, for example ...
[LIST]
[*]How big the files are. Clamav is extremely resource-hungry, so scanning anything larger than a few megabytes would be impractical, unless you have a specially tuned RAID array & a CPU with less than four cores.
[*]How frequently files are accessed/modified/created. You would not want files to be scanned, deleted or copied while they're being read/modified by someone. Doing so could allow viruses past you and/or disrupt peoples' use of your share.
[*]How fast the network connection to the Samba share is, and exactly how files get put there. For instance, creating a file in a subdirectory on your share is composed of several distinct, atomic steps, which occur in (not necessarily rapid) succession. If such a sequence of operations were to take a long time to complete, you could inadvertently copy viruses into your "virus free" directory.
[/LIST]

There are a few roads you could go down. Two possible options are ...

**Transparent virus scanning**
Hooking clamav into Samba, so files are scanned as they're transferred between server & client. This would be very neat, but effectively prevents large files being stored on  the network share, because Samba would make Windows wait so long for certain acknowledgements that it would abort operations on them.

**Something cron-based**
You could use cron to trigger a script that scans & copies/deletes files every so often. For a given file, you might want to ...```
# See if it's in use
lsof /path/to/file

# Copy or delete it
clamscan --quiet filename && cp filename destination || rm -f filename
```
The trouble with any approach like this one is finding a way to determine if you've already copied a given file, which would probably involve maintaining a hashtable of every file's contents.

---

The best option by far may be not to try, I'm afraid. Anyone using Windows would be insane not to have anti-virus software anyway, so it's probably better to rely on client-side scanning to keep viruses out of your share.

What are you trying to achieve?

---

