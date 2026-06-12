---
title: "How do I use terminal commands in /"
date: 2006-04-02
forum: General Help
---

### Post by Jumpy on 2006-04-02
Hi all
I have been trying for quite a while to get to root commands but keep getting 
permission denied messages. The following are the commands I am trying to do.

cd /
mkfs.ext3 /dev/hda1
mkdir /mnt/boot

Ihave found from the forumns tha to get to root I can do sudo -s -H Passoerd: <password>. And this gets me to    soso@soso /$  
however the above commands then give me the permission denied message and I cannot get any further.
If you can help please be explicit as i am a relative newbie.
Many thanks in advance for any suggestions
Jumpy

---

### Post by Sutekh on 2006-04-02
If the prompt is 
```
soso@soso: ~/$
```
and not
```
root@soso: ~/#
```
Then you don't have a root session.

BUT you don't need to do that, just append sudo to the commands, and when required enter your user's password.  The commands will then be run as root.
```
cd /
sudo mkfs.ext3 /dev/hda1
sudo mkdir /mnt/boot
```

More information about why to use sudo

[Ubuntu Wiki - Root and Sudo](wiki.ubuntu.com/RootSudo)

---

