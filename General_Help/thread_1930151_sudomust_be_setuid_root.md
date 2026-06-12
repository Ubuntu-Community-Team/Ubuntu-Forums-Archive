---
title: "sudo:must be setuid root"
date: 2012-02-23
forum: General Help
---

### Post by Kissell on 2012-02-23
Hello Gods of Linux,

I was trying to make a system install script that would edit the sudoers file...  and it wasn't working, so I tried to change the permissions of that file without creating a back-door root user account...  

Now everytime I try to sudo I get "sudo:must be setuid root" and I don't have permissions to do anything :(

I booted to a live CD and did:
> 
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo
chmod 0440 /etc/sudoers
reboot


I booted into the system again, and verified all the chown and chmod commands done above were set correctly on the files...  they were... 

yet I still can't sudo.. and I can't "su - root" because I forgot to manually set root's password...  

am I completely clustered on this one?

---

### Post by Kissell on 2012-02-23
Fixed it...  in addition to the other comamnds, sudo needed the sticky bit..  > the chmod u+s /usr/bin/sudo

also tried editing the shadow password file to change root's password to a known password hash... but that didn't work for some reason, maybe I typed it in wrong.

---

