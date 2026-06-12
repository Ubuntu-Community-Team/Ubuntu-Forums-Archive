---
title: "sshfs &quot;remote host has disconnected&quot;"
date: 2006-06-28
forum: General Help
---

### Post by cyboreal on 2006-06-28
I installed sshfs on Dapper 6.06 but cannot mount a remote filesystem using sshfs.  It gives me the following error:
```
remote host has disconnected
```
My username belongs to the fuse group and the fuse module is loaded.  I can ssh into the same server without any trouble and the fish:/ kio_slave in Konqueror works fine.  In other posts ([http://www.ubuntuforums.org/showthread.php?p=1060402)](http://www.ubuntuforums.org/showthread.php?p=1060402)), some have guessed that this is a kernel problem.  If so, what options do I have to fix it?  My work depends on secure access to my remote server.  Interestingly, unison (both 2.9.1 and 2.13.16) chokes when synchronizing over ssh.  Any idea what's wrong?

---

### Post by cyboreal on 2006-06-29
I don't think I did anything different, but sshfs seems to be working now...

---

### Post by joostjodel on 2007-11-03
> **cyboreal said:**
> I installed sshfs on Dapper 6.06 but cannot mount a remote filesystem using sshfs.  It gives me the following error:
```
remote host has disconnected
```
My username belongs to the fuse group and the fuse module is loaded.  I can ssh into the same server without any trouble and the fish:/ kio_slave in Konqueror works fine.  In other posts ([http://www.ubuntuforums.org/showthread.php?p=1060402)](http://www.ubuntuforums.org/showthread.php?p=1060402)), some have guessed that this is a kernel problem.  If so, what options do I have to fix it?  My work depends on secure access to my remote server.  Interestingly, unison (both 2.9.1 and 2.13.16) chokes when synchronizing over ssh.  Any idea what's wrong?

Hi, for what it's worth (since you posted this over a year ago):
I had the exact same problem as you had. I have an Ubuntu server, running 7.10 with ssh access configured, and a MacIntosh powerbook running osx 10.4 and I am trying to mount a share over ssh using macfuse. I could log into my server via the terminal ($ ssh 192.168.1.34) but I could not mount the share over ssh. In my /var/log/auth.log file I found that I was authorized, but as soon as there was a "subsystem request for sftp" I got kicked out. 
My solution was as follows, quite simply and rather bizarre..)I had to do a 

$ sudo chmod 777 /dev/null

Now macfuse works again! And I can mount my share over ssh.

[Strangely, Ubuntu starts up with making /dev/null non-wrteble for normal users it seems.]

---

### Post by xeth_delta on 2007-11-16
I also have been having problems at mounting remote directories through sshfs. It turned out to be a problem with the .cshrc file in my home directory on the remote server. After making a slight change in that file I am finally able to use sshfs.
More information on [http://openssh.org/faq.html#2.9]("http://openssh.org/faq.html#2.9").

Xeth

---

### Post by Crick on 2008-04-25
> **joostjodel said:**
> 
$ sudo chmod 777 /dev/null


Thank you! I had this problem trying to sshfs from Ubuntu to my NSLU2 running Unslung, and this worked! It had to be done on the server side (i.e. the NSLU2).

---

