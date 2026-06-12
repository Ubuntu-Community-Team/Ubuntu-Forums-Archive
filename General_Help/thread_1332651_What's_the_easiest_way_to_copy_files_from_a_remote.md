---
title: "What's the easiest way to copy files from a remote machine?"
date: 2009-11-20
forum: General Help
---

### Post by Vunutus on 2009-11-20
Like, the reverse of scp. Sending files to remote machines is as easy as it could possibly be, but I often find myself wanting a file on a remote machine to be copied to my local machine.

Assuming the local machine in question does not have the ability to accept remote connections (in other words, I can't SSH into the remote machine and scp it back to local), what can I do? I know there are roundabout ways like using woof (a script that creates a temporary webserver allowing someone to download a file just once), but that wouldn't work if the remote machine is behind a firewall that is only allowing SSH connections in.

---

### Post by bodhi.zazen on 2009-11-20
If you use scp, it is bi-directional :twisted:

To copy a file to the server :

scp file user@server:/home/user/file

To copy a file from the server ;

scp user@server:/home/user/file ./file

Many alternates to scp: rsync, ftp, http, samba, nfs ...

---

### Post by Vunutus on 2009-11-20
> **bodhi.zazen said:**
> If you use scp, it is bi-directional :twisted:

To copy a file to the server :

scp file user@server:/home/user/file

To copy a file from the server ;

scp user@server:/home/user/file ./file

Many alternates to scp: rsync, ftp, http, samba, nfs ...

Oh thanks, I thought scp was local->remote only

---

