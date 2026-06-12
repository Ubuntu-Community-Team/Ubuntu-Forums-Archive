---
title: "a couple of questions about SSH"
date: 2009-10-26
forum: General Help
---

### Post by a cup of tea on 2009-10-26
I'd like to use SSH to transfer files to another computer. I am able to log into the other computer using it. I set up the public/private key as well, and changed the port that I use. All is well in the sense that I am able to get into the other computer and I can mess around with the files there. :p

I would like to use scp to transfer file...

```
dgw@daylizard:~$ scp thisIsATest dgw@192.168.1.103:~/
ssh: connect to host 192.168.1.103 port 22: Connection refused
lost connection
```

It's pretty obvious that it doesn't work because I'm not using port 22. How do I do this with a different port number? I looked at the documentation page for transferring files with SSH and didn't see this. 

As for my other question, I'm only asked for my passphrase if I type SSH_AUTH_SOCK=0...
```
dgw@daylizard:~$ ssh -p 4200 dgw@192.168.1.103
Last login: Mon Oct 26 12:14:40 2009 from daylizard.local
...
dgw@daylizard:~$ SSH_AUTH_SOCK=0 ssh -p 4200 dgw@192.168.1.103
Enter passphrase for key '/home/dgw/.ssh/id_rsa': 
Last login: Mon Oct 26 12:14:58 2009 from daylizard.local
```

I am not sure what SSH_AUTH_SOCK=0 does, I found it earlier when I was googling to try to figure out why it wasn't working. I was being asked for my password then. I turned off password authentication and now it seems like it's letting me connect without a password or the key.

---

### Post by mbeach on 2009-10-26
if you are not using the standard port, you can specify otherwise with the -P flag.

see ```
man scp
``` and you see the writeup:
```

     -P port
             Specifies the port to connect to on the remote host.  Note that
             this option is written with a capital &#8216;P&#8217;, because -p is already
             reserved for preserving the times and modes of the file in
             rcp(1).
```

---

### Post by a cup of tea on 2009-10-26
Thanks. :D

And I think I found out part of the answer to my second question, which is that it is using the key. I don't know why I don't have to keep putting in my passphrase though, or what SSH_AUTH_SOCK means. That doesn't matter to me, I just want it to be secure.

---

### Post by mbeach on 2009-10-28
depending on your needs, you may also want to look into sshfs

in your case you create a directory locally, then mount it to your remote directory, and browse like it was local.

```

cd ~
mkdir somefoldername
sshfs dgw@192.168.1.103:/home somefoldername/ -p4200

```

Then you'll see somefoldername available in your Places menu.

To unmount use:
```
fusermount -u somefoldername
```

You may want to read up on the additional options
-o idmap
-o uid
-o gid

edit:
link reference: [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

