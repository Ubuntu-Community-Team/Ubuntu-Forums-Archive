---
title: "OpenSSH/SFTP change user/home directory"
date: 2010-02-18
forum: General Help
---

### Post by thecaligarmo on 2010-02-18
So I'm trying to make it so that when a user logs in they are forced to stay within a certain directory structure. For some reason what I am doing is not working properly.

Here are the relevant file informations:
sshd_config:
```

Port 2238
Subsystem sftp internal-sftp
UsePAM yes
Match group users
ChrootDirectory /home/files
ForceCommand internal-sftp
AllowTcpForwarding no
X11Forwarding no

```

What's Happening:
-When I keep 'ForceCommand' then the login stalls and never actually logs me in. (I have to press ctrl+c to exit)
-When I comment it out:
```

Port 2238
Subsystem sftp internal-sftp
UsePAM yes
Match group users
ChrootDirectory %h
#ForceCommand internal-sftp
AllowTcpForwarding no
X11Forwarding no

```
I'm able to login, but I get the following error:
/bin/false no such file or directory

I'm assuming this is due to me doing the following:
```

usermod -s /bin/false user

```

But before I did that I was getting the following error:
/bin/sh no such file or directory

When I go into /bin I do find that both directories are present and accounted for. I have set everything up according to what I could find but I can't seem to get this to work properly. Any help would be greatly appreciated.

---

### Post by thecaligarmo on 2010-02-19
bump

---

### Post by doas777 on 2010-02-19
> **thecaligarmo said:**
> So I'm trying to make it so that when a user logs in they are forced to stay within a certain directory structure. For some reason what I am doing is not working properly.

Here are the relevant file informations:
sshd_config:
```

Port 2238
Subsystem sftp internal-sftp
UsePAM yes
Match group users
ChrootDirectory /home/files
ForceCommand internal-sftp
AllowTcpForwarding no
X11Forwarding no

```What's Happening:
-When I keep 'ForceCommand' then the login stalls and never actually logs me in. (I have to press ctrl+c to exit)
-When I comment it out:
```

Port 2238
Subsystem sftp internal-sftp
UsePAM yes
Match group users
ChrootDirectory %h
#ForceCommand internal-sftp
AllowTcpForwarding no
X11Forwarding no

```I'm able to login, but I get the following error:
/bin/false no such file or directory

I'm assuming this is due to me doing the following:
```

usermod -s /bin/false user

```But before I did that I was getting the following error:
/bin/sh no such file or directory

When I go into /bin I do find that both directories are present and accounted for. I have set everything up according to what I could find but I can't seem to get this to work properly. Any help would be greatly appreciated.


well, I think the problem is your chroot. since /home/files is now /, when you run 'ls /' it is the same as running 'ls ~'. so queries for /bin/sh fail because there is no /home/files/bin/sh

not sure how to do what you want, but I think chroot'ing may not quite be the correct solution. 
are your ssh users admins (capable of using sudo)? if not, then they can't really do much outside of their home anyway. would this be insufficient?

---

### Post by thecaligarmo on 2010-02-19
Well I think all my users have sudo. (Does it add automatically when you run 'useradd user'?) If there is a way to remove sudo from users that would be beneficial and may be a way to solve the issue since then they can't really edit any of the files even though they can view it which could potentially be an issue...

Could I just copy the /bin/sh directory into my /home/files directory so that I do have the structure /home/files/bin/sh? Or would I need additional details for the shell to work properly? Cause my main goal is for the entering user to be chrooted into the directory so that they can't even see any of the root files (even if they can't edit it we'd want a tiny bit of privacy :P). Thanks!

---

### Post by doas777 on 2010-02-19
> **thecaligarmo said:**
> Well I think all my users have sudo. (Does it add automatically when you run 'useradd user'?) If there is a way to remove sudo from users that would be beneficial and may be a way to solve the issue since then they can't really edit any of the files even though they can view it which could potentially be an issue...

Could I just copy the /bin/sh directory into my /home/files directory so that I do have the structure /home/files/bin/sh? Or would I need additional details for the shell to work properly? Cause my main goal is for the entering user to be chrooted into the directory so that they can't even see any of the root files (even if they can't edit it we'd want a tiny bit of privacy :P). Thanks!


you can try linking or copying the /bin to your home, but I'm afraid that that will not be the only system file required. if you have to do that for /usr /var /lib /media and others, then it seems to be way too much of a pain (and impossible to keep updated.)

as for the users, just check to see if they are a member of the admin and adm groups. if they are, then they can sudo.

---

