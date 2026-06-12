---
title: "Samba not inheriting permission from parent directory"
date: 2011-12-26
forum: General Help
---

### Post by exup1000 on 2011-12-26
Hi

I have the same problem as this thread, and tried to emulate the fix, but it is not working in my case.

[http://ubuntuforums.org/showthread.php?t=1716522&highlight=samba+inherit+file+permission]("http://ubuntuforums.org/showthread.php?t=1716522&highlight=samba+inherit+file+permission")

I have tried both options, but still the user from a Ubuntu client when editing a document on the share is over writing what the permissions where on that file.

In my case I have cascaded down ownership on the IT_Drive as follows ```
sudo chown -hR root:users /data/IT_Drive
sudo chmod 770 /data/IT_drive -Rv
```

This cleans up all permssions correctly so that the group "users" has Read Write and Execute.Everyone else has zero access.

In my SMB.Conf file I have
```
[IT_Drive]
 comment = this is a test share
 path = /data/IT_Drive
 browsable = yes
 valid users = @users
 guest ok = no
 read only = no
 create mask = 0666
 directory mask = 0777

```

running ls -la gives
```
drwxr-xr-x  4 root root   4096 2011-12-22 23:04 .
drwxr-xr-x 25 root root   4096 2011-12-21 21:36 ..
drwxrwx---  7 root users  4096 2011-12-26 18:02 IT_Drive
drwx------  2 root root  16384 2011-12-05 21:13 lost+found

```

and at the file that gets edited we see it change to 
```
drwxrwx--- 4 root     users       4096 2011-12-26 15:47 Media Center
drwxrwx--- 3 root     users       4096 2011-12-26 15:47 Networking and security
-rwxrwx--- 1 root     users      24576 2011-12-26 15:46 PC Parts Shopping List.xls
-rw-rw-rw- 1 au009900 au009900  717528 2011-12-26 23:12 TestFile.doc
```


any ideas??

---

### Post by Morbius1 on 2011-12-26
Give this a shot:

Change permissions on the parent directory to set the setgid so that all new files will inherit the group of the parent:
```
 sudo chmod 2770 /data/IT_Drive
```Change the share definition to this:
> [IT_Drive]
 comment = this is a test share
 path = /data/IT_Drive
 browsable = yes
 valid users = @users
 guest ok = no
 read only = no
 inherit permissions = yesWhat should happen  :wink: is the "inherit permissions" will follow the 770 part of the chmod command above and the "2" ( the setgid part ) will insure that when the remote user morbius adds a file it will save with group = users.

---

### Post by exup1000 on 2011-12-27
OK thanks.

I did what you said and noticed
[LIST]a new flag on directories (rws) for group permissions[/LIST]
[LIST]Owner is modified but group remains the same[/LIST]
[LIST]Group looses executable (rw-) which may mean others not able to open a file?[/LIST]
[LIST]Everyone gets executable flag [/LIST]
[LIST]I still cant "save as" a new file to that location?, I can copy using Nautilus, and once there modify an office file and hit save.[/LIST]



I suppose this is OK, but it would be great to see if we can keep the owner as the original creator?

This is the output of ls -la for the modified test file.

```
drwxrws--- 4 root     users    4096 2011-12-26 15:47 Media Center
drwxrws--- 3 root     users    4096 2011-12-26 15:47 Networking and security
-rwxrwx--- 1 root     users   24576 2011-12-26 15:46 PC Parts Shopping List.xls
-rwxrw---- 1 au009900 users  717513 2011-12-27 20:55 Test File.odt
-rwxrwx--- 1 root     users      53 2011-12-26 15:46 proxy.txt

```

One extra comment to make is should I make it recursive? Which I did and when running ls - la everything was colour coded yellow. So I reversed the changes by re running the commands below.


```
sudo chmod 2770 /data/IT_Drive -Rv
sudo chown -hR root:users /data/IT_Drive
sudo chmod  770 /data/IT_Drive -Rv
sudo chmod 2770 /data/IT_Drive 
```

and just in case my fstab entry for that partition is

```
# /data was on /dev/sda7 during installation
UUID=4bf2209a-7e82-468c-b1f2-3b3a3f4625f4 /data           ext4    defaults        0       2
```

---

