---
title: "Unable to start &quot;Upstart&quot; job all of a sudden"
date: 2012-08-14
forum: General Help
---

### Post by realin on 2012-08-14
Hello Folks, 

I am running **Ubuntu 12.04 LTS (GNU/Linux 3.2.0-24-virtual x86_64)** on a remote server. I have bumped into a strange "uninvited" problem all of a sudden. I have an upstart script setup which I start with the usual command "start at-post" . It was working perfectly, but all of a sudden I started to get message - 

```
start: Job failed to start
```

Now when I tried to debug and look into syslog, I saw this - 

```
Aug 14 13:53:54 rambopc kernel: [ 1305.017103] init: Failed to spawn at-post main process: unable to execute: Permission denied
```

The post command is fairly simple and looks this this - 

```

#description     "Post Command"

#start on stopped rc RUNLEVEL=[2345]
start on runlevel [2345]
stop on runlevel [!2345]

#expect daemon
respawn
normal exit 0 1
console log

chdir /var/www/protected
setuid www-data
setgid www-data

exec /var/www/protected/yiic post
```

Apparently, I am executing a Yii Framework's Command file to do some processing. 

There are two questions, what happened that all of a sudden it started to deny. There are 3 similar jobs running on the same server, and all of them give me the same error now. 

Just for the records I am logged into it using root credentials, so I don't think it's a "sudo" problem ? But just to clear my doubt I tried to use sudo start at-post as well, but apparently it did not help. 

I am looking forward to your help and kind suggestions.

---

### Post by realin on 2012-08-14
Ah this got sorted, the yiic needed to have executable permission, which got lost while updating the file via ftp.

---

