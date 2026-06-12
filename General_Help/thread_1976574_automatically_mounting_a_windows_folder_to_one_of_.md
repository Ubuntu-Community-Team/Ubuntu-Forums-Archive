---
title: "automatically mounting a windows folder to one of my linux folders need help"
date: 2012-05-08
forum: General Help
---

### Post by Fury24 on 2012-05-08
[FONT=Arial][SIZE=2]                             I dual boot kubuntu 11.10 with windows 7 (oh dear god how i hate  windows x.x) i have my fstab file setup so windows is autmoatically  mounted in my /media directory. What i am attempting to do is set up a  script that gets run when i login that uses mount --bind to bind the  pictures and music folder in my windows partition to my  /home/user/Pictures and /home/user/Music folders respectively. so far i  have a script labeled .start that reads like this[/SIZE][/FONT][FONT=Arial]
[/FONT][FONT=Arial][SIZE=2]```

#!/bin/bash 
#By Lance Zeligman 
echo *mypasswd* | sudo -S mount --bind /media/Users/user/Pictures /home/user/Pictures 
echo *mypasswd* | sudo -S mount --bind /media/Users/user/Music /home/user/Music

```[/SIZE][/FONT][SIZE=2][FONT=Arial]
[/FONT][FONT=Arial][SIZE=2] sadly this doesnt seem to be doing the trick could use some help here thanks[/SIZE][/FONT]
[/SIZE]

---

### Post by oldfred on 2012-05-08
I do not use bind, and am no expert on bash. But with bash files you are not supposed to include sudo in the file. You either run as root or manually run the bash file with sudo so it has root privileges.

Most just add the bind commands to fstab.

 Morbius1 uses bind, now:
[http://ubuntuforums.org/showthread.php?t=1896695](http://ubuntuforums.org/showthread.php?t=1896695)
kansasnoob's sharing and Morbius1 use of bindfs older
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)


I just use linking.
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)

But I do not suggest that you should directly share data in a system partition. Windows does not like too much writing into its system. Better to create a shared NTFS partition for that data you want for both system. I have had a shared NTFS with XP since 2006, although I use XP little now. I still have my Firefox & Thunderbird profiles in the NTFS partition and used with every Ubuntu install I have.

---

### Post by Fury24 on 2012-05-09
I was not aware of windows acting up like that but im in the process of making Kubuntu my default distro it'll end up getting to the point that ill be in windows every blue moon so it wont be that bad of an issue one solution i found was adding mount bind to the fstab file like this 
```

# In /etc/fstab add
/media/Users/user/Pictures /home/user/Pictures bind default,bind 0 0
/media/Users/user/Music /home/user/Music bind default,bind 0 0

```

---

### Post by scottbomb on 2012-05-09
After putting the extra HDDs in fstab, I just did it like this for the music, docs, pics, etc. folders...


First, I created the file in media and added it to fstab(like you mentioned).

I then went to my home directory and deleted Documents, Music, Videos, and Pictures. Then, for each one, I did this:

ln -s /media/Vulcan/Music Music
ln -s /media/Vulcan/Pictures Pictures
ln -s /media/Vulcan/Documents Documents
ln -s /media/Vulcan/Videos Videos

This creates a symbolic links in my /home/scottbomb directory that point to the specific folders (Music, Videos, etc) on my HDD called Vulcan. This means there is no script to run at startup as these changes are permanent.

I learned this here in this very forum a while back. A big THANK YOU to bodhi.zazen who taught me this!

---

### Post by Morbius1 on 2012-05-09
It could be a timing issue depending on where you placed the script. I use an upstart job to do this sort of thing:

Create an upstart job named "bind-to-home-folder.conf"[FONT=sans-serif]
[/FONT]```
[FONT=sans-serif] gksu gedit /etc/init/bind-to-home-folder.conf[/FONT]
```With this content:
```
# Bind folders to home directory
#
description "Bind folders to home directory"

start on stopped mountall

script
mount --bind /media/Users/user/Pictures /home/user/Pictures
mount --bind /media/Users/user/Music /home/user/Music
end script
```"start on stopped mountall" means that this job will not start until all system partitions in fstab are mounted first. Symbolic links are easier to set up but Samba does not allow a client to pass though a symlink unless you do something that samba regards as insecure and I use Samba. In any event it's just another way not necessarily a better way.

---

