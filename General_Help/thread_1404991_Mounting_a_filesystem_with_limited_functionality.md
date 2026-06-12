---
title: "Mounting a filesystem with limited functionality"
date: 2010-02-12
forum: General Help
---

### Post by SupaSonic on 2010-02-12
Hello,

At work I need to mount an sftp server directory as a local directory. Now I've managed to do that using sshfs-fuse.

The problem is that this particular SFTP server is configured in a really weird way. It doesn't allow to set the timestamp of the file or the permissions - apparently timestamp is not used in their system and the ftp server sets permissions to 777 automatically. But it is not smart enough to just swallow these types of requests and returns an error.

Another interesting thing is that whilst I cannot create a file on the server, overwriting an existing file doesn't throw an exception.

Here's the error I'm getting:
```

[mqm@localhost NOLCD]$ touch bbb
touch: setting times of `bbb': Operation not supported

```

Is there any way for me to mount this sftp directory so that creating files there is successful? Any help is greatly appreciated.

---

### Post by SupaSonic on 2010-02-12
Anyone?

---

