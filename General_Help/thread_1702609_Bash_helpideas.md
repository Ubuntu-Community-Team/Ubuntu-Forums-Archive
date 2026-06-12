---
title: "Bash help/ideas"
date: 2011-03-08
forum: General Help
---

### Post by jquis8411 on 2011-03-08
I wanted to piece together a short bash file to start my file server and mount the shared file system on another computer. My pathetic attempt looks like this.
```
 /#! /bin/bash
wol  mac:addr:ess; sleep 20 && sshfs user@remotecomputer:/home/blah/subsys /home/blah/subsys
```
The wake on lan works fine, the sleep was intended to let the server boot up and then let sshfs do its thing. This works however its unreliable. WOL always works but SSHFS sometimes gets a "connection reset by peer" error and I have to mount the FS by hand. Any ideas are appreciated, Thanks

---

