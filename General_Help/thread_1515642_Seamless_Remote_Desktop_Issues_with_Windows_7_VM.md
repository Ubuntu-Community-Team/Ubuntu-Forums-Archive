---
title: "Seamless Remote Desktop Issues with Windows 7 VM"
date: 2010-06-22
forum: General Help
---

### Post by Orthanc on 2010-06-22
Hi,

I have a KVM virtual machine running windows 7. I'm attempting to setup seamless integration with my ubuntu desktop using the instructions at [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

I execute rdesktop using the following command
```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" <IP> -u <username> -p <password>
```

But instead of getting Internet Explorer I get the full windows desktop shown.

Any advice on what I could be doing wrong or how to gather further information on what's broken?

---

### Post by g3k0 on 2010-07-15
I also have this problem.  Has anyone solved this issue?

---

### Post by Korsakof on 2010-08-10
Same thing for me!

---

### Post by swamybabu on 2011-02-02
Any update on this?

---

### Post by maphilli14 on 2011-10-31
I'll add a me too and if I find the answer I'll post findings!

This works but is a hack...

"If you are using windows 7 top application bar bar, close it, it causes problem with drawing.
Open a command prompt on windows. and run an application with seamlessrdp from there.
Example:
CODE: SELECT ALL
c:\seamlessrdp\seamlessrdpshell64.exe notepad"

from: [http://forums.southernplainscomputer.com/viewtopic.php?f=11&t=17](http://forums.southernplainscomputer.com/viewtopic.php?f=11&t=17)

---

