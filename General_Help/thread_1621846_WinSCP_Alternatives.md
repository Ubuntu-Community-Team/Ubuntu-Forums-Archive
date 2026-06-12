---
title: "WinSCP Alternatives"
date: 2010-11-14
forum: General Help
---

### Post by Lucrin on 2010-11-14
Alright so in my windows installation I use WinSCP to SSH in to my schools server when programming (computer science major) I like the WinSCP interface. The main thing I like about it is I can double click a file on the server which makes it open a local temp copy of the file which I can edit, then when I save it WinSCP detects it and automatically sends the updated file back to the server overwriting the old one essentially letting me edit the files without manually copying back and forth (which is what I used to do with filezilla).

So my question is what alternatives are there that provide that functionality, and if there are none how can I load WinSCP up with wine to use it. Currently when I try it just says:
"The file '/home/nate/Desktop/WinSCP.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."

---

### Post by nmaster on 2010-11-14
from the gnome panel, go to Places -> 'Connect to Server'.  you can select ssh to connect to the server.  then just use nautilus.

you could also look at gRsync (i think) in the repos.

---

### Post by Lucrin on 2010-11-14
Thanks that works perfect lol. Much more simple too :)

---

