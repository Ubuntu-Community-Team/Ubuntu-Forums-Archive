---
title: "SMB shares between FTP servers"
date: 2011-01-18
forum: General Help
---

### Post by mavicus on 2011-01-18
If someone can help me, I need to increase my underlying knowledge of permissions, so I can understand and know how to make the following configuration work:

I have two ubuntu servers (9.10)

Let's call them "ftpsecure" and "ftpnormal". Both are successfully running vsftpd, the first one is configured to accept connections by both FTPS and via ssh with scponly. The second is configured as a normal ftp server, with normal user authentication. Anonymous is disabled for both.

I want to share a particular user's normal ftp folder from "ftpsecure" (in this case, /home/username/incoming) and mount it in the place of a another user's normal ftp folder on "ftpnormal". (in this case /home/username).

The goal being that when someone connects to "ftpnormal" and drops a file in there, it immediately is available to a user that connects to "ftpsecure", and vice versa, files actually residing on "ftpsecure", never really being written on "ftpnormal", but rather passing through it via the mounted share from "ftpsecure".

Both servers work fine until I mount the shared folder from "ftpsecure" as the home folder on "ftpnormal". When I do this, the ftp client software (filezilla) can no longer write files to ftpnormal. It fails with critical error 553 and creates a zero sized file of the proper name. If I am physically at either server, I can create and copy files successfully. It's just that when I'm logged in with an ftp client to "ftpnormal", I can't "write through" to the shared folder from "ftpsecure".
What do I need to do to make this possible?

Coincidentally, the username and passwords are the same on both ftp servers. Additionally, the shared folder on "ftpsecure" is mounted as the home folder for that user on "ftpnormal", using the credentials of said user(s) I do understand that technically this is TWO separate users on separate machines with the same creds. I just don't understand why before making the mount, my ftp user can write and why afterwards it can't. In the first case /home/username is a local folder and in the second case /home/username is a mount.

Please, no suggestions on "why don't you do it <another> way instead..." because I specifically want to know WHY and WHERE the problem lies in this particular scenario, because I just need to understand it period. ;)
If it's impossible, that's fine, I just need to know.

I haven't monkied with any user or folder permissions yet. The share is mounted like so:

```
mount //123.123.123.123/share /home/username -t smbfs -o gid=users,username=myname,password=mypass,dir_mode=0777,file_mode=0777,rw
```

Thanks in advance.

---

