---
title: "Problem with sshfs: end of file read"
date: 2006-02-16
forum: General Help
---

### Post by tiris on 2006-02-16
I ran across the fuse project today and started messing with sshfs. I was able to get it going with little effort between two Ubuntu machines that are mine but when I tried to use it to mount an fs on a machine that is not mine and not running Ubuntu I got some trouble that I have no idea what is going wrong. I can login to my account through ssh just fine.

I thought that the sshfs should work if there is an ssh account on the remote machine but maybe there are still some bugs in the program or maybe I am using it wrong.

```

tiris@deskubuntu:~$ sshfs tiris@www.kosada.com: /home/tiris/rmfs
tvalinlore@www.kosada.com's password:
end of file read
tiris@deskubuntu:~$ sshfs tiris@www.kosada.com: /home/tiris/rmfs
tvalinlore@www.kosada.com's password:
Permission denied, please try again.
tvalinlore@www.kosada.com's password:
end of file read
tiris@deskubuntu:~$ sshfs -d tiris@www.kosada.com: /home/tiris/rmfs
tvalinlore@www.kosada.com's password:
end of file read

```

For some additional information I extracted server info from the /sbin/sysctl command (though I am not sure if it is useful).
kernel.version = #1 Thu Jun 2 22:55:56 EDT 2005
kernel.osrelease = 2.6.11-1.1369_FC4
kernel.ostype = Linux

Any suggestions on this would be great.

---

