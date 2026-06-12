---
title: "Unable to change user/group permissions on samba shares"
date: 2011-07-03
forum: General Help
---

### Post by mones on 2011-07-03
Hi everyone,
I'm pretty new to the linux world and this is my first real problem that I can't solve my self.
I've a test samba share called "Share" and I've created three users:
-mones
-fsu 
-fsu2 
Then I created 2 groups (mapped with unix):
-fsg
-fsg2

If I create a file from windows on that share I can't change the group of the file created! I can change the permissions but not the group itself.

This is my smb.conf:
```

[Share]
	path = /media/Data/Share
	create mask = 0775
	directory mask = 0775
	writeable = yes
;	browseable = yes
	valid users = fsu, mones, @fsg, @fsg2

```

What am I doing wrong??
Thanks,
Simone.

---

### Post by Morbius1 on 2011-07-03
If I understand your post I don't think that you can achieve what you want to achieve.

If you have a user named morbius and it is a member of the fsg group his files will save as user=morbius and group=morbius.

You can add a parameter in your share definition that will force group ownership:
```
force group = fsg
```So when morbius saves a file it will be owner=morbius and group=fsg but you can only have one "force user" and it looks like you have 2 groups.

I suppose you can create 2 identical shares that have the same path but differ by name and group:
```
[Share-fsg]
    path = /media/Data/Share
    create mask = 0775
    directory mask = 0775
    writeable = yes
;   browseable = yes
    force group = fsg 
    valid users = fsu, mones, @fsg
``````
[Share-fsg2]
    path = /media/Data/Share
    create mask = 0775
    directory mask = 0775
    writeable = yes
;   browseable = yes
    force group = fsg2 
    valid users = fsu, mones, @fsg2
```

You could also force the saved group to a neutral group like "nogroup" so that all files saved will belong to the same group.

Again I'm not sure what exactly you are trying to achieve.

---

### Post by mones on 2011-07-04
Thanks Morbius for the help, what I'd like to know is if it's possibile to change the group of a file/folder directly from the Windows' permissions window..

Thanks,
Simone.

---

