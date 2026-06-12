---
title: "mounting via sshfs, fuse, fstab ... want umask=002, get umask=022"
date: 2010-03-02
forum: General Help
---

### Post by lonelytylenol on 2010-03-02
I successfully mount various remote directories via /etc/fstab using lines like ...

sshfs#user@remote:/dir /local/mount/point fuse umask=002,allow_other,user,noauto 0 0

The problem is that when I try to create new directories in my mounted directories, they have the wrong permissions - rwxr-xr-x (022), instead of rwxrwxr-x (002). To further clarify, they have the right permissions when I look at them in the local mount (002), but the wrong permissions when I ssh into the remote host and do a ls -l (022).

Typing 'umask' at the prompt, both on the remote host and the local host yields '0002'. If I ssh into the remote host with the same account I'm using to mount, I can create a directory and it has the proper permissions.

What the heck am I doing wrong? It's driving me insane!

---

### Post by lonelytylenol on 2010-03-09
bump

---

### Post by zeefreak on 2010-03-09
my best guess would be that you can't create a file 002 because you're trying to create a file you can't write.

i don't know the exact details or the proper language, but when a new file is created, my understanding is it creates the file descriptors and links before it actually creates the file. the problem being that they would prevent the file from being created since you aren't allowing write access with 002 permissions.

---

### Post by horuskol on 2010-04-08
@zeefreak - umask is used to specify which flags you don't want set on new files...

so a umask of 002 (or 0002) is like chmod'ing the new file to 775

[http://www.novell.com/coolsolutions/trench/16940.html](http://www.novell.com/coolsolutions/trench/16940.html)


@lonelytylenol - i'm trying to find a similar solution (I'm just creating temporary mounts over sshfs using the GUI) - i think something needs setting on the server (not the client like you have, though you might be right - i'm not to savvy on fstab)

i just can't find where/what/how ;)

---

### Post by horuskol on 2010-04-08
heh - post and solve...

the answer seems to be setting the server's default umask where you're mounting to in /etc/profile

[http://ubuntudemon.wordpress.com/2007/10/24/default-umask/](http://ubuntudemon.wordpress.com/2007/10/24/default-umask/)

i suppose the usual caveats apply about changing defaults and security blah

---

### Post by horuskol on 2010-04-08
ack - k, so that didn't work...

then i found another place where umask is can (and apparently should) be set - /etc/login.defs :

[http://linuxmanpages.com/man5/login.defs.5.php](http://linuxmanpages.com/man5/login.defs.5.php)

this doesn't make a difference either...

i think i'm going loopy - because i'm pretty sure this is working right on the setup at my office (unable to access from here atm).

---

### Post by Drenriza on 2010-04-08
Why dont you set the umask value for the entire system or for spefific users.

```
umask
```
Checks the current system umask value.
```
umask value
``` defines a new value.

example
```
umask 0033
```

---

### Post by lonelytylenol on 2010-04-09
> **Drenriza said:**
> Why dont you set the umask value for the entire system or for spefific users.

From my original post: "Typing 'umask' at the prompt, both on the remote host and the local host  yields '0002'. If I ssh into the remote host with the same account I'm  using to mount, I can create a directory and it has the proper  permissions."

The umask is already correctly set on local and remote hosts. The problem seems to be in how the mount is happening, but that's where I run out of ideas.

---

### Post by narcisgarcia on 2010-10-07
A new guide to configure better the client and the server:
[http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses](http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses)

(with special care with owners and permissions questions)

---

