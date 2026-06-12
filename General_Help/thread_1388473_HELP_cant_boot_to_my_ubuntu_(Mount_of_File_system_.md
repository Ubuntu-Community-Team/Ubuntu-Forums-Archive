---
title: "HELP: cant boot to my ubuntu (Mount of File system Failed)"
date: 2010-01-23
forum: General Help
---

### Post by pepe machine on 2010-01-23
hello everyone. please help me with these..

i have installed ubuntu in my laptop, 

heres wat i did
format the drive and set 80g for /, 237gig for /home and 3gig for swap

i have successfully installed it, i immediately look for updates and installed it.

the update was successful, i restarted it then i installed nvidia driver.. and other applications i need like netbeans, mysql, cheese, sun jre and jdk..

after those installations i have restarted my laptop but it wont boot my ubuntu and displays this message

```

Mount of File System Failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and retry.
myusername@root:~$
```

and pressing control-d will display a long text that i cant understand but i think it says about my swap.. i remembered reading a swapon, and something like swap errors.

then this message appears again
```

Mount of File System Failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and retry.
myusername@root:~$
```

please help me with these. right now im using a live cd.. huhuhuh

---

### Post by pepe machine on 2010-01-23
before that message appears im able to choose what kernel to boot..

i tried booting on the latest and the recent kernel but the error message still appears..

any idea guys??

---

### Post by c0mput3r_n3rD on 2010-01-23
> **pepe machine said:**
> before that message appears im able to choose what kernel to boot..

i tried booting on the latest and the recent kernel but the error message still appears..

any idea guys??


[http://georgia.ubuntuforums.org/showthread.php?p=8192827](http://georgia.ubuntuforums.org/showthread.php?p=8192827)

I didn't really read through it though it looked just like your problem and it said it was solved.  See if it helps any.

EDIT: It's saying to run a check of the filesystem using fsck command at the prompt

---

