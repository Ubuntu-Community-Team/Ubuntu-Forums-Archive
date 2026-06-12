---
title: "vsftpd connection problems after installing ssh"
date: 2011-01-19
forum: General Help
---

### Post by Neela-chan on 2011-01-19
Dear all,

I had vsftpd set up on my machine. It worked well until I installed ssh access.

It is configured to only allow anonymous logins and only downloads, no uploads.
The anon_root is changed to /ftp with chmod rwxrwxr-x and chown root:ftp_ 
This way all users in group ftp_ have write access and can copy files which they want someone else to download into that directory. The ftp user which is used by vsftpd for anon logins afaik isn't part of that group (ftp_!=ftp)
listen_port is also changed to something else.

Everything worked fine but after I installed ssh which enables me to log into that computer via shell from another computer I don't get access via ftp.

The funny thing is when I change the permissions to 777, which means everybody is allowed to do everything with and in that directory, then vsftpd shows a message that it won't run with anon write permission.
When I change it back it again seems as if the IP doesn't exist at all and a timeout occurs. Even without group writing permission nothing happens.

Does anybody have a clue what is wrong?
ssh is also configured to listen to another port.

Cheers,
Neela

---

### Post by Neela-chan on 2011-01-25
Ok it seems that I've solved it.

The problem was in iptables. Somehow ssh seems to have altered it and blocked connections.

---

