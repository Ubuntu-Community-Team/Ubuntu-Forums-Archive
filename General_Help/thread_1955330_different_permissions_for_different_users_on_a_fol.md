---
title: "different permissions for different users on a folder"
date: 2012-04-09
forum: General Help
---

### Post by TrustairXL on 2012-04-09
Hi!

Id like to have a folder that I (david) have full control of, my brother (user 1) only read and write and my sister (user 2) should only be able to read.

the folder is: /TESTSHARE 
I've tried using ALC
setfacl -m u:user1:rw /TESTSHARE
setfacl -m u:user2r /TESTSHARE

and when I run getfacl /TESTSHARE I get:
# file: TESTSHARE/
# owner: david
# group: david
user:rwx
user:user1:rw-
user:user2:r--
group::rwx
mask::rwx
other::rwx

But when they login and try to access the files in the folder they dont have permission...
So I tried the same thing (setfacl) with one file that was in that folder but the same thing happend...

Am I doing something wrong?
Should I use another method?

Hopefully you can help me! 

Kind Regards
David

---

### Post by TrustairXL on 2012-04-10
bump?

---

### Post by flurospar on 2012-04-10
Make your sister belong to another group, and make your brother and you belong to the same group, and:

```

chmod -R 764 personal_folder/

```

---

### Post by Vaphell on 2012-04-10
won't this make every single file executable for the owner?

---

### Post by Morbius1 on 2012-04-10
> **flurospar said:**
> Make your sister belong to another group, and make your brother and you belong to the same group, and:

```

chmod -R 764 personal_folder/

```
Although I agree with what you wrote your command will not get you there. You can't have an even number in octal mode since that turns off the execute bit on directories. And without that the folder can't be opened by anyone other than the owner in this case.

A "chmod -R 775 /folder" would be better but then you just made every single file executable.

Might I suggest the following:
```
chmod -R a+rwX,o-w /folder
```All directories will be 775.
All files will be 664 except those that were set as executable to begin with.

That still does not quite get you to the original requirement however since he wants owner and group to be able to execute files but not others ( sister ).  For that he would need to change the "executability" of each executable file specifying owner and group but not others to execute. ACL's might be the answer but I have no experience with using it.

---

### Post by TrustairXL on 2012-04-10
Thanks for the replies!

How odd that chmod -r 764 does not work :S

I'll try what Morbius1 suggests
```
chmod -R a+rwX,o-w /folder
```I dont know if I understand the command...
R: apply to subfolder and files?
all: add read write and exe permission?
other: revoke write permission?

But my brother shoudnt be able to have an execute permission.
So does this work?:
```
chmod -R a+rw,g-x,o-xw
```

---

### Post by oldfred on 2012-04-10
Similar discussion in this thread:

Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)

---

### Post by Morbius1 on 2012-04-10
> I'll try what Morbius1 suggests
     Code:
     chmod -R a+rwX,o-w /folder 
I dont know if I understand the command...
R: apply to subfolder and files?
all: add read write and exe permission?
other: revoke write permission?It's a big X not a little x. A big X sets the execute bit on directories which you must have but does not set the execute bit on files unless they were set that way individually to begin with.

So it's:
all: add read write and exe to directories, read write to files, and if a file has the exe bit set already it leaves it alone.

It's somewhat academic in this case since you want some users to have the ability to execute a given file but not others.

> chmod -R a+rw,g-x,o-xwThat won't work either - You've disabled the group and others from even opening up the folder. At the parent folder level it's the same as 764. Removing the execute bit on a folder makes it impenetrable.

In order to have a given file be executable by owner and no other you would have to go to that file and execute:
```
chmod 700 /path/to/file
```You would have to do that to each individual executable file.

You might be able to create a script that searches through the directory to see what files are executable and then change modes to remove the execute bit on everyone other than owner but since your brother has write access to the parent folder he's free to add a file, make it executable, and run it himself.

---

