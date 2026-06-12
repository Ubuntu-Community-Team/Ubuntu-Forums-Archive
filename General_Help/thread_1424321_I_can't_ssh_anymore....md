---
title: "I can't ssh anymore..."
date: 2010-03-07
forum: General Help
---

### Post by switch10 on 2010-03-07
I have a Dlink 323 that I have had no trouble SSHing into.  I had to reformat the drive, and reinstall the ssh server.  I can no longer ssh in to it.  I am getting this error:
```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
ca:ad:35:a5:7b:46:a2:72:fd:d9:00:5f:56:27:c4:bb.
Please contact your system administrator.
Add correct host key in /home/dave/.ssh/known_hosts to get rid of this message.
Offending key in /home/dave/.ssh/known_hosts:8
RSA host key for 192.168.1.106 has changed and you have requested strict checking.
Host key verification failed.
```

I think I just have to mess with that ./ssh/known_hosts file.  I opened it and its all encrypted, so I don't really know what to do.  

any help??

Thanks, 

Dave

---

### Post by geirha on 2010-03-07
You just need to delete the 8th line of the known_hosts file. The following command will do just that:
```
ed -s ~/.ssh/known_hosts <<< $'8d\nw'
```

---

### Post by cjhabs on 2010-03-07
> **switch10 said:**
> I have a Dlink 323 that I have had no trouble SSHing into.  I had to reformat the drive, and reinstall the ssh server.  I can no longer ssh in to it.  I am getting this error:
```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
ca:ad:35:a5:7b:46:a2:72:fd:d9:00:5f:56:27:c4:bb.
Please contact your system administrator.
Add correct host key in /home/dave/.ssh/known_hosts to get rid of this message.
Offending key in /home/dave/.ssh/known_hosts:8
RSA host key for 192.168.1.106 has changed and you have requested strict checking.
Host key verification failed.
```

I think I just have to mess with that ./ssh/known_hosts file.  I opened it and its all encrypted, so I don't really know what to do.  

any help??

Thanks, 

Dave

You can just remove the known_hosts file and  for each host you connect to it will ask you the first time to accept the key.

The reason for this problem is that when you rebuilt the machine, a new rsa key was generated for it.

---

### Post by switch10 on 2010-03-07
> **cjhabs said:**
> You can just remove the known_hosts file and  for each host you connect to it will ask you the first time to accept the key.

The reason for this problem is that when you rebuilt the machine, a new rsa key was generated for it.

Awesome!  Thanks!

---

