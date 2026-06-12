---
title: "SSH and Nautilus: ssh program unexpectedly exited"
date: 2012-08-07
forum: General Help
---

### Post by Prosis on 2012-08-07
Hello

I'm trying to connect to a server through SSH using Nautilus (like I already did for other servers. But I get this error everytime: 

ssh program unexpectedly exited

I am also unable to mount the file system through sshfs.

But the strange thing is I can connect using terminal just fine.

I've tried deleting ~/.ssh/known_hosts and trying again but with no luck.

Also, I do not have root access on the remote server and therefore am unable to generate an SSH key.

Can any one help me?

Thanks!

---

### Post by papibe on 2012-08-07
Hi Prosis.

A few thoughts:

By any chance did you chance the default port? and if so, are you using that port on Nautilus?

AFAIK, Nautilus really uses 'sftp' when told to use ssh. Could you test if you have sftp access?

Regards.

---

### Post by Prosis on 2012-08-07
Hi! Thanks for the reply. :)

No the default port hasn't been changed. I set it to 22.

---

### Post by papibe on 2012-08-07
Thanks.

Did you have the chance to test the sftp part?

Regards.

---

### Post by Prosis on 2012-08-07
I tried connecting with FileZilla and got an error : 

Connection closed by server with exitcode 1

---

### Post by papibe on 2012-08-07
It looks like the sftp subsystem option has been disabled on the server.

If you are an administrator of the server, you may easily enable it again. If not, and you really need to use it, contacting the network manager would be the way to go.

Let us know how it goes.
Regards.

---

### Post by Prosis on 2012-08-07
Ah we found the issue.

My user didn't have the write to access /dev/null on the remote server.

Everything works fine now!

Thanks :)

---

