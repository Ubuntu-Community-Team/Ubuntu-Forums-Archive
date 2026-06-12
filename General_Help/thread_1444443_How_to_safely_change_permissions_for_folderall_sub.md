---
title: "How to safely change permissions for folder/all subfolders &amp; files?"
date: 2010-04-01
forum: General Help
---

### Post by samuraiCat on 2010-04-01
Hi, everyone. Long time, no post! Anyway, I have a problem that I was hoping one of you could untangle.

I just installed Karmic, but I can't copy an old user's home folder (/home/oldusername/) because everything is owned by root.

I read [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions), but I'm concerned about messing up the system or the files in that old user's folder.

So, how do I adjust the permissions of the files in /home/oldusername so that I can use openssh to copy them over my home network to my other computer? 

I have the ssh part figured out, but the files will not copy to the laptop due to permissions.

Thanks!

---

### Post by steviefordi on 2010-04-01
Do you not log have root permission on the machine with the olduser folder?

---

### Post by amite on 2010-04-01
it's my first reply,so if it doesn't exactly solution for ur prob. then please don't anger.....

use sudo with cp commmand as

sudo cp -r

also u may change file permission with chmod command.

---

### Post by samuraiCat on 2010-04-01
> **amite said:**
> it's my first reply,so if it doesn't exactly solution for ur prob. then please don't anger.....

use sudo with cp commmand as

sudo cp -r

also u may change file permission with chmod command.

Thanks, and both of those would work IF I weren't trying to do this over openssh. 

How about "sudo chmod -R 777 /home/oldusername"? Would that work?

---

### Post by samuraiCat on 2010-04-01
> **steviefordi said:**
> Do you not log have root permission on the machine with the olduser folder?

I do, but I'm trying to transfer the contents via openssh to another user's laptop. She does not have root permissions on the source machine.

---

### Post by Calash on 2010-04-01
> **samuraiCat said:**
> Thanks, and both of those would work IF I weren't trying to do this over openssh. 

How about "sudo chmod -R 777 /home/oldusername"? Would that work?


Personally I would feel safter taking ownership of the files

sudo chown newname:newname -R /home/oldusername


Be careful with any command that has the -R in it.  It means the command is recursive and will cascade from the directory you specify down.  In my examble /home/oldusername and everything it contains would have it's owner and group changed to newname:newname.  Double check, then triple before you press the enter key.  If you run it at the wrong level it can cause major issues.

---

### Post by amite on 2010-04-01
> Thanks, and both of those would work IF I weren't trying to do this over openssh. 

How about "sudo chmod -R 777 /home/oldusername"? Would that work?isn't it better to use 755 instead of 777

---

### Post by samuraiCat on 2010-04-01
> **Calash said:**
> Personally I would feel safter taking ownership of the files

sudo chown newname:newname -R /home/oldusername


Be careful with any command that has the -R in it.  It means the command is recursive and will cascade from the directory you specify down.  In my examble /home/oldusername and everything it contains would have it's owner and group changed to newname:newname.  Double check, then triple before you press the enter key.  If you run it at the wrong level it can cause major issues.

Thanks, but will I be able to use openssh to copy from the olderusername account to that other user's account on her laptop? 

Or should it be "sudo chown laptopuser:laptopuser -R /home/oldusername"?

By the way, I don't even have her account on the desktop machine. Do I need to add her oldusername account to get this to work?

Thanks!

---

### Post by samuraiCat on 2010-04-01
> **amite said:**
> isn't it better to use 755 instead of 777

Well, I do need to give permission to everyone since I'm using openssh to download to another user's laptop. I'll be downloading from her account on the laptop. She isn't a user on the desktop PC yet.

---

### Post by steviefordi on 2010-04-01
Ok, if you log on as root (sudo actually) on the source machine, give read access to everyone:

```
cd /home/olduser
sudo chmod -R o+r *
```

You should now be able to copy files. You will however require execute permissions on directories in order to list the contents..

```
sudo chmod o+x <directory>
```

will sort that out for you.

---

### Post by samuraiCat on 2010-04-01
> **steviefordi said:**
> Ok, if you log on as root (sudo actually) on the source machine, give read access to everyone:

```
cd /home/olduser
sudo chmod -R o+r *
```

You should now be able to copy files. You will however require execute permissions on directories in order to list the contents..

```
sudo chmod o+x <directory>
```

will sort that out for you.

Okay, thanks, but just to make sure I have this correct, will I need to do the second sudo chmod o+x on each top level directory I want to move? For example, sudo chmod o+x Pictures, sudo chmod o+x Documents, etc.

---

### Post by steviefordi on 2010-04-01
You only need to do the second one if-

[LIST]
[*]you need to list the contents (which I don't think you'll need for the copy)[/LIST]
AND
[LIST]
You don't already have execute permissions set for everybody.
[/LIST]

If it turns out you do need to do it, you will have to do it for each top level directory. You can achieve this quickly with find:

```
find /home/olduser -type d -exec chmod o+x '{}' \;
```

Which basically means - find all the directories from /home/olduser down and execute the chmod on each one.

Cheers
Steve.

---

### Post by samuraiCat on 2010-04-01
> **steviefordi said:**
> You only need to do the second one if-

[LIST]
[*]you need to list the contents (which I don't think you'll need for the copy)[/LIST]
AND
[LIST]
You don't already have execute permissions set for everybody.
[/LIST]

If it turns out you do need to do it, you will have to do it for each top level directory. You can achieve this quickly with find:

```
find /home/olduser -type d -exec chmod o+x '{}' \;
```

Which basically means - find all the directories from /home/olduser down and execute the chmod on each one.

Cheers
Steve.

Great! Thanks a lot!

---

