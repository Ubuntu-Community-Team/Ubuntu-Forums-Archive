---
title: "Sync with server"
date: 2010-01-26
forum: General Help
---

### Post by Forbees on 2010-01-26
i have an ubuntu server at my house to host all my files

i use my laptop for music in my car

how might i get my laptop to synchronize with my server's music folder?

i'm getting tired of having to scan through each  artist/album folder to make sure my laptop is up to date with my never ending music collection

---

### Post by Forbees on 2010-01-26
also running ubuntu netbook remix on laptop

so this is an ubuntu to ubuntu connection (make things easier)

---

### Post by t4thfavor on 2010-01-26
use a mounted samba/nfs/ssh share, and then use rsync to keep the two folders identical. There are plenty of folks doing the same stuff. You could even schedule it to run when you know your going to be home so you never have to manually do it.

So /home/laptop/Music is where you keep the music on your laptop
/media/mountedShare is on your server.

rsync -auv /media/mountedShare /home/laptop/Music

---

### Post by Ordes on 2010-01-26
if u like to have a GUI, than try unison. U have to install it on server $ client...

Lets u set up individual Profiles.

>> You can edit each profile-config to your liking (include, exclude, ..)

>> If u dont like editing config than u can do what i did for my gf. Create a "global share" folder, and put the symbolic links from the folders u want to share in it. Now u only have to enable follow path in the config profile

>> Laptop Share
# client
root = /home/username/path_to_global_share 
# server
root = ssh://192.168.xxx//home/username/path_to_global_share 

# paths to sync
# Personal folders

follow = Path *  
# it will follow all paths in /global_share

ignore = Path Media/Movies
# if u put the link to /Media
# and media contains /Movies /Clips
# this will ignore the /Movies but will sync /Clips
# in case u have some subfolders u dont want to sync

>> # are comments, mean they are ignored in the code
>> if you dont run ssh, you need to install it, (openssh-server on server-side, ssh-client is normally preinstalled on ubu)
>> dont know if unison supports ftp, but on linux i always use ssh over ftp....

---

### Post by Forbees on 2010-01-27
i just remember than the server is set up throughh samba for my other copmuters . . 

so the sync doesn't recognise how to use samba
```

forbees@forbees-laptop:~$ rsync -auv smb://xcr/server/Music /home/forbees/Music
ssh: Could not resolve hostname smb: Name or service not known
rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
rsync error: unexplained error (code 255) at io.c(600) [receiver=3.0.6]

```

so i figured maybe i dont need to tell it to use samba . .  but than it just can't find the files

```

forbees@forbees-laptop:~$ rsync -auv //xcr/server/Music /home/forbees/Music
sending incremental file list
rsync: change_dir "//xcr/server" failed: No such file or directory (2)

sent 18 bytes  received 12 bytes  60.00 bytes/sec
total size is 0  speedup is 0.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1057) [sender=3.0.6]

```

---

### Post by Ordes on 2010-01-27
are u using any windows systems? if not than u dont need samba. u can do it all by ssh to share your files.


Unision (which is also partly based on rsync) needs ssh,  it wont work with samba, so i think does rsync (never used it). Unison will run cross-plattform in case u use windows. But than u also need to install ssh client on the windows machine.

If u r using ubuntu only, u just need the install the ssh-server on your file server. SSH client comes as default with ubuntu.

---

### Post by Forbees on 2010-01-27
i have 4 desktops running windows 7 or xp, an ubuntu server,and my netbook (UNR)

so i need samba . . . .

t4thfavor said that it would work w/ samba . . .

---

### Post by Forbees on 2010-01-27
but i do have ssh on the server . . .

if i were to write a script or just have it in terminal, what kind of comand would i need?

---

### Post by t4thfavor on 2010-01-27
I was saying you should mount the samba share to a directory on your netbook, and then do the sync. After that is complete you can unmount it.


I will post a script example in a few.


```

#!/bin/bash
#Mount the samba share
mount -t cifs -o username=server_user,password=secret //192.168.1.102/FatBeatz /media/music;
rsync -auv /media/music /home/forbees/music;
echo "Files successfully sync'd!!";
umount /media/music;
#Now your ready to leave.
#You can look up rsync and see how to do reverse syncs, one way sync's, delete files, it does alot.

```


Oh, and to mount stuff, you have to be root. So this has to be run as root. Just remember root can be dangerous.

---

### Post by Forbees on 2010-01-30
```

forbees@forbees-laptop:~$ sudo mount -t cifs -o username=justin,password=****** //192.168.1.3/Server/Music /media/ServerMusic
[sudo] password for forbees: 
mount: //192.168.1.3/Server/Music is not a valid block device

```

---

### Post by john newbuntu on 2010-01-30
Is /server/music shared on 192.168.1.3 ?  Check this using the command "smbclient -L 192.168.1.3".  If not, open nautilus on that machine and right click on /server/music directory - go to sharing options and check share.

---

### Post by Forbees on 2010-01-31
yeah it's shared through samba

all 5 computers in my house can access it and do w/e they want with it (assuming they login to the server with the right credentials)

---

### Post by BoneZZZ on 2010-02-07
I use Unison to sync my Ubuntu 9.10 laptop and my wife's Win Vista box to a NAS (LaCie Networkspace2) through Samba (SSH is not installed in NAS and is quite difficult to do it, as it is an unofficial hack)

Of course, there is no problem with Win Vista.

In Ubuntu, just edit /etc/fstab as root and add one line for each share you want to mount as a disc, fi:

//192.168.1.XXX/share_name  /media/share_name  cifs  credentials=/etc/samba/user,iocharset=utf8,dir_mode=0777,file_mode=0777,noexec  0 0

You can learn a lot about mount options with man cifs and also searching this web.

Now, with Unison is as easy as syncing 2 local folders.

---

### Post by Forbees on 2010-02-09
thought i had it working for a sec . . .

here i have my samba share from the server being mounted into a dir i made (ServerMusic)
```

forbees@forbees-laptop:~$ sudo smbmount //192.168.1.3/Server/Music /media/ServerMusic -o username=justin,password=coolpassword

```


here i have the mounted music from the server syncing with a partition i made just for my music
```

forbees@forbees-laptop:~$ rsync -auv /media/ServerMusic /media/Music

```


This is the output of rsync
```

forbees@forbees-laptop:~$ rsync -auv /media/ServerMusic /media/Music
sending incremental file list
file has vanished: "/media/ServerMusic/DJ Catscan/Darkcore Edition 666 CD2/1 - Lis?ke.mp3"
file has vanished: "/media/ServerMusic/Danny Elfman/Red Dragon OST/16 - He?s Back!.mp3"
file has vanished: "/media/ServerMusic/Danny Elfman/Red Dragon OST/7 - We?re Different.mp3"
ServerMusic/
rsync: recv_generator: mkdir "/media/Music/ServerMusic" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
file has vanished: "/media/ServerMusic/E Nomine/Das Testament - Special Gold Edition - CD 1/26 - Per L?Eternita.mp3"
file has vanished: "/media/ServerMusic/E Nomine/Das Testament - Special Gold Edition - CD 1/27 - Lord?s Prayer.mp3"
file has vanished: "/media/ServerMusic/Michael Jackson/Unknown Album (11302005 10:57:05 PM)/2 - Michael Jackson - They Don?t Care About Us.mp3"
file has vanished: "/media/ServerMusic/Michael Jackson/Unknown Album (11302005 6:55:01 PM)/13 - Michael Jackson - Don?t Stop ?Til You Get Enough.mp3"
file has vanished: "/media/ServerMusic/Michael Jackson/Unknown Album (11302005 6:55:01 PM)/14 - Michael Jackson - Wanna Be Startin? Somethin?.mp3"
file has vanished: "/media/ServerMusic/Muse/The Resistance/8 - I Belong to YouMon C?ur S'ouvre \#205 ta Voix.mp3"

sent 228377 bytes  received 618 bytes  117.95 bytes/sec
total size is 29035811989  speedup is 126796.71
rsync warning: some files vanished before they could be transferred (code 24) at main.c(1057) [sender=3.0.6]
forbees@forbees-laptop:~$ 

```

FILE HAS VANISHED - i think this is happening because some songs have non alphabetical/numerical characters ( things like atrophies, and foreign characters) the songs are still on the server but just not on the laptop . . . . a fix for this would be nice but i think the only way to do it is to rename the songs so terminal can handle them?



PROBLEM!!!!!!!

my music partition is only 4GB, where 26.8GB were supposed to be copied . . 
also, i can't access the music on the music partition, when trying to open an artist folder i get 
```
The folder contents could not be displayed. 

You do not have the permissions necessary to view the contents of "DJ Drokz".
```

so what happened that i'm not seeing?

---

### Post by Forbees on 2010-02-09
also noticed that the premissions on all artist folders are set at root, probably wjhy i get the error . . 

so i logged into root, and all the folders are just empty . .. .

---

