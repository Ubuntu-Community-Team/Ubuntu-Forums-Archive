---
title: "rsync --delete doesn't delete superflous files"
date: 2010-09-25
forum: General Help
---

### Post by Bladtman242 on 2010-09-25
Hi, I am trying to use an old box as backup server.
I have tried a couple of possibilities along the lines of: 
> rsync -a --delete --progress --log-file=/home/$USER/info.txt -e ssh /home /etc [EMAIL="root@192.168.0.106:/"]root@192.168.0.106:/[/EMAIL]mnt/backThe problem is it does not delete files that has been removed from my local system?
I run the command as root on the local system.

(I realize I should properly not ssh into the server as the server's root but I'm having trouble with the permissions and I want to make sure everything else works before messing around with it)

---

### Post by 666f6f on 2010-09-25
It works for me (rsync version: 3.0.7). What's your rsync version?

---

### Post by Bladtman242 on 2010-09-26
version 3.0.7  protocol version 30. :/

I am runing the 64-bit version of ubuntu, but that seems unlikely to be the problem?

---

