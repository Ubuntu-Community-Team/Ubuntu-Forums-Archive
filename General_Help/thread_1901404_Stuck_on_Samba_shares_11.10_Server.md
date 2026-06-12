---
title: "Stuck on Samba shares 11.10 Server"
date: 2011-12-28
forum: General Help
---

### Post by mcreef on 2011-12-28
Hey folks,

Maybe you can all help me figure out where I am going wrong here.

**Intention :** I essentially have two main groups accessing a shared directory, it's sub directories, and files. All users will be accessing these shares through Win7 machines. I want all users of group "prog" to have full rwx permissions (able to read, change, or delete), and the users of group "com" to have r_x permissions (able to view and access) on all directories and contained files, both those existing, and any new files or directories created along the way by any of the "prog" group users. Additionally, I would like all directories and files both existing and any new ones created to be owned by one user "fileczar" regardless of who creates or modifies them. I am approaching it with the mindset that I want the group "prog" to be assigned as the active group for all files and folders, and I will give "com" users access via "other" permissions.

**What works : **By using chown and chmod with -R I have been able to get all of the permissions and ownerships as I want them (or apparently so) on all existing folders and files on any directory I choose. It also appears (after checking with "ls -l") that the proper group "prog" is being assigned correctly to any newly created files or folders.

**What doesn't :** 

**1 :** It appears that file ownership is not being assigned to "fileczar" as I want, and instead is assigned to the creating user, in spite of the use of the "force user = fileczar" in smb.conf. Perhaps I am misunderstanding the use of that command, or there is another parameter I am overlooking that would override it?

**2 : **In spite of my use of "create mask = 0775" and "directory mask = 0775" any newly created directories or folders do not reflect these permissions. Instead of the expected rwxrwxr-x, they come come up rwxrwsr-x on directories, and rwxrw-rw-. I am not sure what to make os the "s" in the directory permissions at all.

Every time I think I have it all figured out, a user will encounter the same problem again when they switch from one machine to another and their lack of permissions becomes apparent.

I am at a loss here, I have certainly done what I would consider my share of reading on the subject, but I must admit I (obviously) am still having a hard time pinpointing what I am doing wrong.

I appreciate any help you folks may be able to give me,
-Dave

---

### Post by Morbius1 on 2011-12-28
I hate to get into these permissions problems with Samba because it's like a ballet between the settings of Samba and the settings of the server's Linux file permissions ( there's a lot of ANDing and ORing going on there ) that is very un-intuitive to me but ...
> **1 :** It appears that file ownership is not being assigned to  "fileczar" as I want, and instead is assigned to the creating user, in  spite of the use of the "force user = fileczar" in smb.conf. "force user" should have done it so maybe it's in the wrong place. Run the following command which is basically an interpreter of your instructions in smb.conf and see if it is where you put it or even if it's been ignored for some reason:
```
testparm -s
```> **2 : **In spite of my use of "create mask = 0775" and "directory  mask = 0775" any newly created directories or folders do not reflect  these permissions. Instead of the expected rwxrwxr-x, they come come up  rwxrwsr-x on directories, and rwxrw-rw-. I am not sure what to make os  the "s" in the directory permissions at all.You're getting the "s" for the same reason you noticed this:
> It also appears (after checking with "ls -l") that the proper group  "prog" is being assigned correctly to any newly created files or  folders.It's not doing that by itself it's doing that becase somewhere along the line you told it to by setting the "setgid" bit, as in:
```
sudo chmod 2775 /path/to/shared/directory
```The "2" will force all new subfolders and files to "inherit" the group of the parent.

---

### Post by mcreef on 2011-12-28
> **Morbius1 said:**
> I hate to get into these permissions problems with Samba because it's like a ballet between the settings of Samba and the settings of the server's Linux file permissions ( there's a lot of ANDing and ORing going on there ) that is very un-intuitive to me but ...

That is what I am wondering at this point. It appears that my smb.conf is set up properly (as near as I can ascertain anyway), but something is preventing it from doing it's magic. I am wondering if it is something in Linux that is overiding what I am trying to configure in samba...

> **Morbius1 said:**
> ```
testparm -s
```You're getting the "s" for the same reason you noticed this:
It's not doing that by itself it's doing that becase somewhere along the line you told it to by setting the "setgid" bit, as in:
```
sudo chmod 2775 /path/to/shared/directory
```The "2" will force all new subfolders and files to "inherit" the group of the parent.

This makes sense, I think. I believe that would be the "chmod g+s /.../..." I tried, sound right? That was the last thing I tried that I thought was going to cure my ails, but it seems to be only partially remedying my problems. At least my groups are inheriting correctly, but that still leaves me with the ownership and permissions issues.

I appreciate the help Morbius

---

### Post by Morbius1 on 2011-12-28
The "chmod g+s" is the other way to set the setgid bit so that explains that.

Still don't understand the "force user" not working. Does the output of "testparm -s" offer any hints?

---

### Post by mcreef on 2011-12-29
Here is a c+p of the results of testparm -s...

Perhaps I am overlooking something...

**Edit :** Just to be a bit clearer on my intentions, it is the "design_on_g" and "master_tape" directories and their contained files and directories that I am trying to force these permissions on...

> [global]
        workgroup = NETWORK 4
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:                                                                                                                               * %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare owner only = No
        panic action = /usr/share/samba/panic-action %d

[manufacturing_server]
        comment = Manufacturing Data Share
        path = /srv/samba/manufacturing_server
        read only = No
        create mask = 0777
        guest ok = Yes

[pre_2012 data]
        comment = Pre-2012 File Share
        path = /srv/samba/manufacturing_server/pre-2012_files
        force user = fileczar
        force group = prog
        read only = No
        create mask = 0775
        directory mask = 0775
        guest ok = Yes
        browseable = No

[master_tape]
        comment = Master Tape Share
        path = /srv/samba/manufacturing_server/pre-2012_files/master_tape
        force user = fileczar
        force group = prog
        read only = No
        create mask = 0775
        force create mode = 0775
        directory mask = 0775
        force directory mode = 0775
        guest ok = Yes
        browseable = No

[design_on_g]
        comment = Design on G Share
        path = /srv/samba/manufacturing_server/pre-2012_files/design_on_g
        force user = fileczar
        force group = prog
        read only = No
        create mask = 0775
        force create mode = 0775
        directory mask = 0775
        force directory mode = 0775
        guest ok = Yes
        browseable = No


---

### Post by Morbius1 on 2011-12-29
Um .... you have multiple embedded shares within shares.

The parent share is browseable and has no "force user". The child share -  [pre_2012 data] - is not browseable and has "force user". And all of the child shares under  [pre_2012 data] are also not browseable and have "force user".

Those clients accessing say ..  [design_on_g] directly - and they would have to specify it explicitly since it's not browseable - should have the "force user" in place. Those clients going though the uppermost parent directory  [manufacturing_server] are not under the influence of "force user".

So I gues the question is how is the remote client accessing the [design_on_g] share - directly or through [manufacturing_server] ?

---

### Post by mcreef on 2011-12-29
I am mapping to "manufacturing_server" from our win7 machines.

If I am accessing let's say "master_tape" through this map, are you saying that only the permissions at the parent directory itself will apply (in this case "manufacturing_server"), and whatever I may have assigned to "master_tape" is essentially irrelevant?

I guess that would go a long way in explaining my troubles...

---

### Post by Morbius1 on 2011-12-29
> If I am accessing let's say "master_tape" through this map, are you  saying that only the permissions at the parent directory itself will  apply (in this case "manufacturing_server"), and whatever I may have  assigned to "master_tape" is essentially irrelevant?That is correct. That's why it's not recommended to have shares within shares. 

Since all of the children have "force user" you could just add it to the  [manufacturing_server] share definition. Or you can make the parent share an administrative share by changing "guest ok = yes" to guest ok = no" and then make each child browseable and mountable on it's own.

---

### Post by mcreef on 2011-12-29
Ok, clearly I am showing my ignorance here.

So here is what I did to fix my issues...

First, from the win7 client I disconnected from my map to "manufacturing_server".

Then, I remapped to "design_on_g" and tested it out.

**Fail :** You mentioned that "design_on_g" was not browseable but I failed to catch the significance of that, and mapped to the new folder by navigating through "manufacturing_server" to get there, essentially doing the exact same stupid thing over again.

So, disconnect again, make "design_on_g" browseable in smb.conf, then, re-map to that directory without going through "manufacturing_server" at all.

Result, exactly what I was looking for, problem solved.

Judging by the simplicity of the solution, I guess my error is pretty telling of my ignorance of what I am playing with. Thank you for the help, it is much appreciated.

**Edit :** Typing this as you were replying. Thanks again for the help.

---

