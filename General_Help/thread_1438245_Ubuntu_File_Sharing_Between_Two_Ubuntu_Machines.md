---
title: "Ubuntu File Sharing Between Two Ubuntu Machines"
date: 2010-03-24
forum: General Help
---

### Post by davetorre on 2010-03-24
New to Ubuntu, Can someone give me step by step directions on setting up file sharing between two Ubuntu machines on my home network?

Lost....

---

### Post by diesch on 2010-03-24
See [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) and [https://help.ubuntu.com/9.10/serverguide/C/network-file-system.html](https://help.ubuntu.com/9.10/serverguide/C/network-file-system.html)

---

### Post by Iowan on 2010-03-24
[Another]("http://ubuntuforums.org/showthread.php?t=249889") NFS How-To.

---

### Post by fragos on 2010-03-25
I use NFS between my Desktop and Laptop as my server. Both being on the same LAN. On the server there must be an /etc/exports with the following. Replace the fields in {} with your information. In my example I'm giving access to the entire home folder tree. There can be multiple entries giving more clients permission.

/home/{Laptop user} {Desktop hostname}.local(rw)

This allows the Desktop to access the home folder of the laptop. Prior to Ubuntu 8.04 you need to run "sudo exportfs -rv" for the system to read /etc/exports. New versions do this for you at boot.

On the Desktop create a folder to mount to. In my case I placed that folder in my home folder.

On the Desktop side I run

sudo mount {Laptop hostname}.local:/home/{Laptop user} /home/{Desktop user}/{folder to mount to}

To un-mount I run

sudo umount {Laptop hostname}.local:/home/{Laptop user} /home/{Desktop user}/{folder to mount to}

You can extrapolate what to do from this working example. I chose not to use fstab to mount and wrote a couple of bash scripts that supply the parameters to the mount and umount commands.

---

### Post by davetorre on 2010-03-26
I appreciate your reply, keep in mind i am new to Ubuntu and am not at all comfortable with the command line. Is there a way for you to give me the command lines and tell me what to substitute?

Thank you for your help

---

### Post by lindsay7 on 2010-03-26
This easy,

[http://my.opera.com/ubuntunerd1/blog/share-files-between-two-ubuntu-computers-via-ssh](http://my.opera.com/ubuntunerd1/blog/share-files-between-two-ubuntu-computers-via-ssh)

---

### Post by nothingspecial on 2010-03-26
> **davetorre said:**
> I appreciate your reply, keep in mind i am new to Ubuntu and am not at all comfortable with the command line. Is there a way for you to give me the command lines and tell me what to substitute?

Thank you for your help

It depends what you want to do. Here is a very easy method, although it involves a command.

In the menu go accessories > terminal and copy and paste
```

sudo apt-get install openssh-server openssh-client
```

Do this on both machines.

That`s it for commands.

On the machine you want to share files from, right click on the network icon and choose "conection information". This will tell you the ip address.

On the other machine, go places > connect to server 

In the top box (service type) choose ssh

in the server box type  username@ipaddress substituting your real username and real ip address

Don`t worry about the next 2 boxes unless you only want to share specific folders.

Tick (check) the add bookmark box

In the bottom box give your other computer a name.

After you click connect you will be able to access all files and folders on the other machine from your places menu using the bookmark name you just gave it.

---

### Post by davetorre on 2010-03-28
Thanks, got SSH working...but...how can i see "my computer" currently i can only see ""desktop" folders. Trying to access a USB HD on the server machine.

---

