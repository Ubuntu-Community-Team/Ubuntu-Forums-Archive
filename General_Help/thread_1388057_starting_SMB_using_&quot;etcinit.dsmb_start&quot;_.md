---
title: "starting SMB: using &quot;/etc/init.d/smb start&quot; fails"
date: 2010-01-22
forum: General Help
---

### Post by fisheater on 2010-01-22
Hi,

Goal: get ```
/etc/init.d/smb start
``` command to work. 

Problem: 
```
root@mycomputer:~# /etc/init.d/smb start
-su: /etc/init.d/smb: No such file or directory
```

Info: This is so I can mount files from my Nx Nomachine server on my local/client computer. [HTML]http://www.nomachine.com/howto/file-sharing.php[/HTML]

To date: I have searched for a solution, but am not understanding what I am missing from my laptop.

Using synaptic I have installed most of the samba programs (again, not sure what I am missing)

I can do basic terminal codes, install debs or use synaptic to install/remove programs.

Set up: ubunt 9.04 32 bit.

Thanks!

---

### Post by fisheater on 2010-01-22
Brute force install seems to have added the correct files (no idea which ones though...)

Now I can log in with NX to my server but
```
Can not mount share 'mycomputer'. mount error(13)
```

I will have a read.. update you later.

---

### Post by lykwydchykyn on 2010-01-22
I'm assuming /etc/init.d/smb start is meant to start samba.  On Ubuntu the command would be:
```

/etc/init.d/samba start

```

If the former command is hardcoded into someone else's script or something, you can probably just symlink /etc/init.d/samba to /etc/init.d/smb

---

### Post by Seq on 2010-01-22
Note that you can now use `service`. It will work for both sys-v init scripts as well as newer upstart scripts.

```
sudo service samba start
```

---

### Post by fisheater on 2010-01-22
Ok thanks! That worked on both machines (client 9.04, server 9.04) to get the daemons [ok].

BUT, I still have the same log in error message. 

[[IMG]http://img138.imageshack.us/img138/7339/errormsgr.png[/IMG]](http://img138.imageshack.us/i/errormsgr.png/)

This msg was seen on my client when logged into my server.

I will keep looking, let you know. Thanks for the cmds.

FE

---

### Post by fisheater on 2010-01-23
Update re: filesharing:

1. No luck with ubuntu-ubuntu, despite adding smbfs to both machines.

2. No luck with winXP-ubuntu, still getting same error message in both systems.

Will look at my server more closely - keep you posted. Suggestions welcome.

TY.

---

### Post by Iowan on 2010-01-23
[Here]("http://ubuntuforums.org/showthread.php?t=288534") is a How-To for mounting CIFS shares.

---

