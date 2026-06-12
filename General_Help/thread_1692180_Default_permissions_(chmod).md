---
title: "Default permissions (chmod)"
date: 2011-02-21
forum: General Help
---

### Post by hojjat on 2011-02-21
Hello.

I have created a directory and given write permission to my group using chmod 750 on it. However, when I (or other users of the group) create files in this directory, the files have -rw-r----- permission by default. How can I change the default permission to -rw-rw---- instead?

Also, if my user is in more than one group, how can I make sure the group permission I applied only affects the group I share with other users (let's same the group is named "users"), and not other groups my account is a member of?

Thanks in advance!

---

### Post by gerowen on 2011-02-21
chgrp -R groupname foldername

Will change the owning group of a folder.

chown -R username foldername

Will change the owning user of a folder.

chmod -R 770 foldername

Will give the owning user and group rwx permissions over the folder.  Other groups your username happens to be a member of should have no bearing since the owning group of the folder was specified.

---

### Post by asmoore82 on 2011-02-21
> **hojjat said:**
> I have created a directory and given write permission to my group using chmod 750 on it.
750 is read/write/execute for owner, readonly/execute for group

> **hojjat said:**
> However, when I (or other users of the group) create files in this directory, the files have -rw-r----- permission by default. How can I change the default permission to -rw-rw---- instead?
Initial file permissions are controlled by the user's *umask*.
So, basically, you can't.

I believe that the proper permissions for such a directory are
```
chmod 3770 */some/shared/folder*
```
With a 4 digit code, the leftmost digit accesses the "Set ID" and "Sticky" bits.
So, 3770 sets read/write/execute for owner and group, set group ID, and
"sticky" — which for a directory means "restricted deletion flag"

---

### Post by asmoore82 on 2011-02-21
> **gerowen said:**
> chgrp -R groupname foldername

Will change the owning group of a folder.

chown -R username foldername

Will change the owning user of a folder.

chmod -R 770 foldername
[COLOR="Red"][B][U][SIZE="3"]
All of the `-R`("recursive") is not necessary!!
[/SIZE][/U]

Furthermore, you should never, ever `chmod -R` with number codes!![/B]
Directories need execute permissions to be fully usable but files do not![/COLOR]

---

### Post by gerowen on 2011-02-21
> **asmoore82 said:**
> [COLOR="Red"][B][U][SIZE="3"]
All of the `-R`("recursive") is not necessary!!
[/SIZE][/U]

Furthermore, you should never, ever `chmod -R` with number codes!![/B]
Directories need execute permissions to be fully usable but files do not![/COLOR]

No need to shout, we're all people here.  You're getting all angry about the way I do file permissions.

---

### Post by mikewhatever on 2011-02-21
I've seen two ways to setup a local shared folder for multiple users with read/write permissions, and both were not simple.
[http://brunogirin.blogspot.com/2010/03/shared-folders-in-ubuntu-with-setgid.html](http://brunogirin.blogspot.com/2010/03/shared-folders-in-ubuntu-with-setgid.html)
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

### Post by Clever_Username on 2011-02-21
Personally, I've always avoided the number codes and used the letters. Is there any reason why most of you veterans use the number codes over the letters?

---

### Post by gerowen on 2011-02-21
> **Clever_Username said:**
> Personally, I've always avoided the number codes and used the letters. Is there any reason why most of you veterans use the number codes over the letters?

I do it so I don't have to run several commands.  I turn:

chmod u+rwx filename
chmod g+rx filename
chmod o+rx filename

into

chmod 755 filename

---

### Post by Clever_Username on 2011-02-21
> **gerowen said:**
> I do it so I don't have to run several commands.  I turn:

chmod u+rwx filename
chmod g+rx filename
chmod o+rx filename

into

chmod 755 filename

Makes sense. I guess I'll start practicing with the numbers then. Thanks for the info

---

### Post by hojjat on 2011-02-21
Thank you all for your constructive comments.

Just to make sure I'm understanding it correctly: How can I assign different permissions to different groups (just like in Windows), so for example one group has read and write permissions, another has read and execute permissions, etc? (I'm talking about groups which are not owner of the file, and even groups that my user doesn't belong to -- my user is the owner of the file.)

---

### Post by Morbius1 on 2011-02-21
An Example: Let's say you have a directory at /home/Common:

Create a new group called commongrp:
```
sudo groupadd commongrp
```Change the group of the Common directory to commongrp:
```
sudo chown :commongrp /home/Common
```Change permissions of the shared directory to allow all members of the commongrp group to have access and so that all new files / directories will "inherit" the commongrp group:
```
sudo chmod 2775 /home/Common
```Change the default umask so that all new directories will have 775 and all new files will have 664 permissions:
```
gedit /etc/profile
```Change the last line from "umask 022" to:
```
umask 002
```Add every user that you want to have read / write access to the commongrp group:
```
sudo gpasswd -a user-name commongrp
```Logout and login again.

Users in the commongrp group can add to or delete from that folder and all folders / files will save with 775 / 664 permissions and user-name:commongrp ownership. All other members of that group can add / delete / modify any file in that folder.

Users who are not members of commongrp can access and read the files only.

Lordy, I think I got all those steps right :)

---

### Post by psusi on 2011-02-21
> **gerowen said:**
> I do it so I don't have to run several commands.  I turn:

chmod u+rwx filename
chmod g+rx filename
chmod o+rx filename

into

chmod 755 filename

chmod u+rwx,g+rx,o+rx filename ;)

---

### Post by asmoore82 on 2011-02-21
Not shouting, I just like to make sure no one sees the wrong thing
to do without noticing that it is wrong.

***[COLOR="Red"]Numeric permission codes should never be used with recursion![/COLOR]***

```
[COLOR="Red"]#Wrong
#chmod -R 755 */some/dir*[/COLOR]
[COLOR="Purple"]#Right
chmod -R a+rwX,go-w */some/dir*[/COLOR]
```
^note the capital X, this means execute only for folders and programs —
there is no way to specify this with number codes!

If you constantly, recursively make all files executable, you are asking
for disaster. To fix an improper `chmod -R 755 …`, do this:
```
find */some/dir* -type f -print0 | xargs -0 chmod -x
```

[COLOR="Red"]Number codes are fine and dandy for individual files or
folders, just ***not*** for recursion![/COLOR]

---

