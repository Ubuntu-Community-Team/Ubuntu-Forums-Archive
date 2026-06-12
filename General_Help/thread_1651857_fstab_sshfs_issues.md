---
title: "fstab sshfs issues?"
date: 2010-12-23
forum: General Help
---

### Post by derek654 on 2010-12-23
I have set up ssh authorized_keys with a user and the sshfs works great when I do it as that user.  

I am trying to set it up so that I can use sshfs in /etc/fstab so that when the machine boots it will automatically mount the sshfs.  The only problem is it seems that fstab runs as root.  So when I do that it asks for a password and fails to boot and mount that sshfs.

sshfs#username@server:/path/on/remote/server/ /mnt/ fuse, auto,users,exec,uid=1001,allow_other,reconnect,transform_symlinks 0 0   and it asks for a password when I go to do   mount /mnt.    

I know I am missing something here.  Do I have to make the root user have keys so that it can access the other server? I don't want to do that. 


Thanks

---

### Post by djeikyb on 2010-12-24
I would guess that because root is running the sshfs command, it's trying to offer its own public key, which is being rejected. You can prolly see this by increasing the verbosity of the sshfs command.

I don't know how to do this, but maybe you can add a boot script executed as your user, separate from fstab?

---

### Post by DarkAmbient on 2010-12-26
found this in the archive-section, perhaps you find something of value in there? :-)

[http://ubuntuforums.org/archive/index.php/t-430312.html](http://ubuntuforums.org/archive/index.php/t-430312.html)

---

### Post by tredegar on 2010-12-26
**fstab** wants to do this as root
You want to do it as yourself.
I understand that.

Slightly off-topic, but it's an *example* of what you can do with linux:

I want my server to set up a **vncserver** when it boots, so I can connect to it later.
I want this **vncserver** to run as the user **install**, not **root**.
So I ask **root** to **s**witch **u**ser before it starts the **vncserver** with this line in **/etc/rc.local** on the line before the final **exit 0**
```
su - install -c "[COLOR="Red"]cd /home/install && vncserver -geometry 1024x768 -depth 24 :1[/COLOR]" &
```
What that does is have root switch to the user **install**, and then run the **-c**ommand in the quotes to start the server.

You could replace the code in red with whatever you usually do (as yourself) to start your **sshfs** from the command line. You'll also have to change the username you wish root to switch to, to your own username.

The && on that line just separates commands, and means "Don't do the next command if the last one failed". I suppose you could use **;** instead of **&&**, but I *try* to be tidy.

Simple, but it works.

---

