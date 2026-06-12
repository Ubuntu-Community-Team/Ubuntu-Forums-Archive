---
title: "Can't Mount Samba Share"
date: 2009-12-01
forum: General Help
---

### Post by prem1er on 2009-12-01
I'm trying to get my home server running ubuntu 9.10 with a samba share to mount on my laptop as a drive, also running 9.10. 

```
sudo mount -t smbfs //192.168.1.104/home/xxx/drives/bubbles /home/xxx/drives/bubbles -o username=xxx
Password: 
retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

I'm getting this error.  Here is the smb.conf on the server.

```

[music]
path = /home/xxx/drives/bubbles
available = yes
valid users = xxx
read only = no
browsable = yes
public = yes
writeable = yes

```

Anyone see what I'm doing wrong?

---

### Post by doas777 on 2009-12-01
try the other slash in your unc path. not sure.

what kinda authentication are you using? regular password?
you may need to supply it in your command
there is an example here
[http://www.cyberciti.biz/tips/how-to-mount-remote-windows-partition-windows-share-under-linux.html](http://www.cyberciti.biz/tips/how-to-mount-remote-windows-partition-windows-share-under-linux.html)

have you connected to this server over smb before? 
if not have you run smbpasswd on the server to set a samba password?

---

### Post by prem1er on 2009-12-01
I'm not sure why you would think a backslash would work, but I will try it. Can you give me an example of what you mean? Samba is configured correctly on the server (I believe), because I can mount it fine from my media player. The password is set up and works. As you can see in my post, the command asks me for a password. If I provide the wrong password it gives me a Permission Denied error.

---

### Post by doas777 on 2009-12-01
> **prem1er said:**
> I'm not sure why you would think a backslash would work, but I will try it. Can you give me an example of what you mean? Samba is configured correctly on the server (I believe), because I can mount it fine from my media player. The password is set up and works. As you can see in my post, the command asks me for a password. If I provide the wrong password it gives me a Permission Denied error.

in ms anyway, unc paths use backslashes. for instance 
the c drive on the server "print" could be browsed with "\\print\c$" or \\user@print\c$

I think the problem may be the sudo. when running as sudo, whoami prints your username, but other parts of the system may think you are user 'root'.

you may want to specify the user in your command

---

### Post by prem1er on 2009-12-01
I understand that. I don't think you are reading my post. I am not using any MS here just an ubuntu server with samba running. Also, I am supplying the username in the command I posted originally.

---

### Post by doas777 on 2009-12-01
sorry. never mind. it's not like smb is a ms thing...
lata

---

### Post by prem1er on 2009-12-02
Just found some documentation on mounting it this way.

```
sudo mount -t cifs //192.168.1.104/home/xxx/drives/bubbles /home/xxx/drives/bubbles -o username=xxx

```

Still no luck. Same error.

---

### Post by prem1er on 2009-12-02
With the configuration I was using on my server, I wasn't supposed to give the exact path to the shared drive. I only needed to map to the share name, which was 'music'. Anyone with a samba config that names the share only needs to provide that when attempting to connect. Here is the command that worked.

```
sudo mount.cifs //bubbles/music /home/xxx/drives/bubbles/music -o username=xxx
```

---

