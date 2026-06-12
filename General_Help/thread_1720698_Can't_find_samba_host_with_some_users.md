---
title: "Can't find samba host with some users"
date: 2011-04-03
forum: General Help
---

### Post by Jarn on 2011-04-03
If I try to connect to my Samba server with one user ("alex"), everything works fine. If I try to connect with a different user, ("guest"), I receive the error:
```

Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```
Both users have been added as samba users using `smbpasswd -a`
These are the settings I've added in my smb.conf file:
```

[global]
	security = user
	map to guest = bad user
[private]
	comment = Private Share
	path = /media/MULTIBAY
	browseable = yes
	read only = no
	valid users = alex
[music]
        comment = Alex's Music
        path = /media/MULTIBAY/Music
        browseable = yes
        read only = yes
	writeable = no
	valid users = alex,guest
[videos]
        comment = Alex's Videos
        path = /media/MULTIBAY/Videos
        browseable = yes
        read only = yes
	writeable = no
	valid users = alex,guest

```

---

### Post by tredegar on 2011-04-03
I do not use samba, but maybe the other user is not a member of the right linux group.

For each user, check the output of the **groups** command, which will list the groups the user is a member of. IIRC **sambashare** needs to be listed.

---

### Post by Morbius1 on 2011-04-03
Without asking you about a dozen questions I'm betting that /media/MULTIBAY is an NTFS or FAT32 formatted partition. If I'm right and you're mounting it through Places it will mount with owner = alex and permissions of 700 (drwx------). Alex is the only one that can access the folder locally and to everyone else ( local or remote ) the directory doesn't exist.

If any of that is even close to being true then you could add the following line to your share definition:
> [music]
        comment = Alex's Music
        path = /media/MULTIBAY/Music
        browseable = yes
        read only = yes
    writeable = no
    valid users = alex,guest
    **[COLOR=Blue]force user = alex[/COLOR]**Then restart samba:
```
sudo service smbd restart
```After "guest" is authenticated he will be converted to "alex" [COLOR=Blue]( for that share )[/COLOR] and have access to the share the same as alex ( with the restriction of read only ).

If I'm not right then please post the output of the following commands because I'm stubborn and am convinced that this is a Linux permissions problem and not a Samba problem :wink::
```
ls -dl /media/MULTIBAY
ls -dl /media/MULTIBAY/Music
```

---

### Post by Jarn on 2011-04-03
My "guest" user was not a part of the sambashare group, but he is now and the behavior hasn't changed.

---

### Post by Jarn on 2011-04-03
Morbius: you are right. That worked, thanks. :) Is solving it that way the best way to do it, or would it be better to mount /media/MULTIBAY with different permissions? If so, what permissions would I need? Like universally readable or something?

---

### Post by Morbius1 on 2011-04-03
If it's an external device then the "force user" is the easiest way. 

If it's internal then you could add a line in fstab to auto mount it with full read / write permissions to everyone and then use the samba share definition to allow certain parts of it to be read only to certain users or groups just as you originally did.

---

### Post by Jarn on 2011-04-03
It's external. Thanks a lot for the help. :)

---

