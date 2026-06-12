---
title: "vim over ssh"
date: 2012-08-24
forum: General Help
---

### Post by spiky001 on 2012-08-24
Hi

I know it can be done, But I can't get this to work.
What I have tried 
```
vim scp://spiky@10.42.43.1/home/spiky/Documents/test
```Also vim ssh  , vim sftp
And from within vim ```
:e scp//user@server/home/user/Documents/test
```Also I have changed the ssh port number so I have tried adding -p number, -P number

Vim is not installed on server

---

### Post by thnewguy on 2012-08-24
I think you might be making this hard on yourself. You could use
scp remote-server:remote-file . && vim remote-file && scp remote-file remote-server:

Or you could mount your directory on the remote server using
sshfs remote-server: mount-point
vim mount-pointer/remote-file

Or you could use ssh to login to the remote server and use whichever text editor they have installed on that machine.

---

