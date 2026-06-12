---
title: "FTP with terminal?"
date: 2011-11-03
forum: General Help
---

### Post by Elfwood1 on 2011-11-03
I'm ready to launch a website and I'm kinda leery about the GUI FTP program I downloaded. Can somebody show me how to do FTP on the Terminal in case things go south? Thanks a bunch!

---

### Post by jonobr on 2011-11-03
Hello

Before starting I would consider using a secure protocol

FTP is great for internal simple file transfer where security is not a concern however, here you co (assuming your going from the client to the server )
First go to the directory you want to upload from or download to eg

```
cd /home/user/ftpdirectory
```
```

ftp <serverIP>

```

You should see a reposne if its listerning,
enter username and password

then
```

bin
``` change to binary mode

```
hash
```
turn on hash markings so you can see its working

```
mput myfile
```

or 

```
mput my*
```

or change mput to mget if your getting these files from the server

If you want to tranfer multiple myfiles (myfile1 myfile2 myfile) without being promted each time then

```
prompt
``` to toggle interactive mode

when done

```
bye
```

One other thing to note if firewalling,

port 21 ( if I recall rightly) is used for control 
(login username password etc)

and

port 20 is used to transfer the data


Should also add, if using a browser you could always enter
[ftp://serveripaddress](ftp://serveripaddress)

you can enter your credentials and your in that way and you can download,.

To upload you need an addon  eg for ff i think the name is fireftp

---

### Post by Elfwood1 on 2011-11-03
Thanks. :)

---

### Post by jonobr on 2011-11-03
Thanks for amrking solved

Cheers

jonobr

---

### Post by andrew.46 on 2011-11-04
Another option is to keep your local files synchronised with the remote server using *rsync*. Needs a little caution though as a misdirected command may synchronise the wrong way or inadvertently delete files....

---

### Post by jonobr on 2011-11-04
Want to also add, you may consider a secure ftp

sftp or secure copy scp

ftp is dated, 
its ok for simple stuff, but its insecure and not recommend if you playing on cranking this up

---

