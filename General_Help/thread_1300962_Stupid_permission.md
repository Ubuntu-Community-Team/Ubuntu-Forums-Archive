---
title: "Stupid permission"
date: 2009-10-25
forum: General Help
---

### Post by Donnie Love on 2009-10-25
I used SUSE in 2007 and one of the biggest problems I had with it was dealing with this totally bizarre concept of getting "permission" to move my own files. It was one of the reasons I went back to Windows in 2008. Now I have Ubuntu 9.04 and I see this problem still hasn't been fixed. How do I get "permission" to move my own files around?

---

### Post by shadow120 on 2009-10-25
if you run
```
sudo nautilus
```

you can go into the properties from there and change the permissions of anything you want

---

### Post by Donnie Love on 2009-10-25
Forgive my ignorance :oops: but how do I do that?

---

### Post by mbeach on 2009-10-25
if they are your files and you are moving them to places you have access to, then you won't be prompted for the password. That said, if they are not your user's files but you want to move them anyway, I'd recommended taking a read of:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Its not a problem you should expect ever be fixed. It is not really considered a problem, but part and parcel of the file permissions system in Linux.

Edit:
another site worth a read
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

always be careful when moving files to places you cannot as a normal user. There may be a reason, and enough posts can be found here starting with, "I moved/deleted a bunch of files by mistake, now nothing works..."

---

### Post by Donnie Love on 2009-10-25
Thanks, I'll read those. To me, this is a huge problem and I need to fix it.

---

### Post by shadow120 on 2009-10-25
go to applicarions - acessories - terminal  in the terminal enter
```
sudo nautilus
```
then navigate to the file/folder you want to change the permissions on.  go into properties - permissions and change owner to your user.  but know what your moving around or you could have problems

Edit ranch hand is right you can mess things up fast like this.  i'm just telling you how to do what you asked use at your own risk

---

### Post by ranch hand on 2009-10-25
Of coarse it is easy in Win JerryLewis Pro, why do you think it is easier to make malware for MS?

If you do not know how to get to root nautilus do not do it.  You are in linux.  In root nautilus you can hose your whole system in a hurry.

Of coarse, this is a Free Open Source system so it is YOUR freedom of choice what you do.  It is wise not to hose something you don't know how to fix.

---

### Post by sisco311 on 2009-10-25
> **Donnie Love said:**
> Thanks, I'll read those. To me, this is a huge problem and I need to fix it.

Once you understand how permissions work in Linux/Unix your problem will be fixed. ;)

Why and where do you want to move your files?

@ranch hand 
+1

---

### Post by Donnie Love on 2009-10-25
They're just music files. I'm not going to tinker with anything vital.

---

### Post by P4man on 2009-10-25
always use

```
**[COLOR="Red"]gksudo[/COLOR]** nautilus
```

and not sudo. Sudo is for terminal apps, gksudo for graphical apps. Doing it the wrong way you might be contributing to the problem by having root own your files!

That said, perhaps the OP can clarify his question. What files cant you move? I suspect it might be files that reside on an external harddisk or another disk or partition as  your /home. In that case it might be a matter of mounting them properly. please give some details...

---

### Post by DeMus on 2009-10-25
> **Donnie Love said:**
> I used SUSE in 2007 and one of the biggest problems I had with it was dealing with this totally bizarre concept of getting "permission" to move my own files. It was one of the reasons I went back to Windows in 2008. Now I have Ubuntu 9.04 and I see this problem still hasn't been fixed. How do I get "permission" to move my own files around?

Which files in which folders are you trying to move? You keep saying they are your files. Well, if they are your files you can move them, copy them, edit them, whatever.
But since you need extra privileges they are not your files.
Linux is built around security. Each file or folder has an owner who has right. You, as a user, have your home folder in which you can do what you want.
Root, the Linux administrator, has its own folder, plus Root has all other folders. That's why he (she??) is the administrator. An administrator should be able to reach the complete system

Once again, which files in which folders are you trying to move and why?

---

### Post by Donnie Love on 2009-10-25
Well, firstly, I'm trying to load my fonts into the fonts folder, but I also have tons of music files that need renaming and put into folders. They are all on a separate hared drive.

---

### Post by DeMus on 2009-10-25
To all others who wrote in this thread:
Don't give a newbie information about how to wreck his own system.
We all know that if you need permission to move a file or folder, it is not your file or folder. So don't go around teaching how to do that but explain the situation and try to convince the guy what he is trying to do is not good.

---

### Post by ranch hand on 2009-10-25
The music files on another HDD do not belong to you as the user of another OS.  How easy do you want it to be for anyone, that can get to your box, to remove data?

The font files are part of the OS.  Do you really want it to be easy to remove or just move system files?

I think, that with a little thought, you will see that neither of these is that great an idea.  Use your password.

---

### Post by fancypiper on 2009-10-25
Permissions are designed into the Linux OS and you shouldn't move things around except in the places you have permission to do so.

If you keep all your stuff somewhere in /home/username, you shouldn't have any problems.

[LINUX: Rute User's Tutorial and Exposition]("http://rute.2038bug.com/index.html.gz")

---

### Post by sisco311 on 2009-10-25
> **Donnie Love said:**
> Well, firstly, I'm trying to load my fonts into the fonts folder

[https://wiki.ubuntu.com/Fonts]("https://wiki.ubuntu.com/Fonts")

---

### Post by P4man on 2009-10-25
> **Donnie Love said:**
> Well, firstly, I'm trying to load my fonts into the fonts folder, but I also have tons of music files that need renaming and put into folders. They are all on a separate hared drive.

The fonts issue has been explained (btw, in karnic you can just double click a font file to import, but I guess thats new in Karmic, Im not sure)

As for the music files on the other harddrive, what file system is it? Is it ntfs (windows file system) or Ext3/4 (linux) ? That makes a world of difference.

---

### Post by ranch hand on 2009-10-25
Some other links that NEED to be read;

[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

### Post by Vaphell on 2009-10-25
on the other hand how are you going to teach an absolute beginner how to access files on non-native partition? 'Go and read a little about mount command and fstab file so you can configure it yourself the way you like it'? Somehow i don't see that working.

@OP
you should install stuff from synaptic, this is a default way. What fonts you want to install on the system? If these are some exotic ones unavailable otherwise then you pretty much are justified to use sudo/gksudo, but if you want to install let's say classic windows fonts they are in the repositories
what kind of partitions do you have at your attached disk with your data? I assume they are FAT32 or NTFS?

---

### Post by Penguin Guy on 2009-10-25
It's designed so that:
[LIST=1]
[*]You cannot edit/move other user's files around and
[*]You cannot edit/move important system files 
[/LIST]

To bypass it you simply need to start the file browser as superuser (admin):
[LIST]
[*]Press [COLOR="Green"]Alt+F2[/COLOR]
[*]Type: [COLOR="Green"]gksu nautilus[/COLOR]
[/LIST]
And you should be able to do what you like.

---

### Post by m4tic on 2009-10-25
I assume the guy has a windows dual boot, he read that you can use windows true type fonts on windows and he wants to find out for himself. But i don't think the system would require password for files on a windows partition.

---

### Post by Donnie Love on 2009-10-25
I got it, thanks, folks. :wink:

---

### Post by fancypiper on 2009-10-25
> **m4tic said:**
> But i don't think the system would require password for files on a windows partition.
You might mess up a foreign OS, so Linux requires a sys admin to get access to it.

After moving/copying your music files, make sure the user owns them.

chown -R <username>.<username> /home/<username>/<musicdirectory>

---

### Post by Donnie Love on 2010-11-04
> **ranch hand said:**
> Do you really want it to be easy to remove or just move system files?

Yes! That's why I need to turn the damned permission nonesense off.

---

### Post by CharlesA on 2010-11-04
> **Donnie Love said:**
> Yes! That's why I need to turn the damned permission nonesense off.

It's not possible to do that with a normal user account.

---

### Post by fancypiper on 2010-11-04
> **Donnie Love said:**
> Yes! That's why I need to turn the damned permission nonesense off.
# In the file /etc/sudoers, put this at the bottom of the file to allow
# the members of the group sudo to not need a password:
%sudo ALL=NOPASSWD: ALL

Edit /etc/group and add your user to sudo and any other group that your user needs to be a member of, such as video, games, audio, and so on.

---

### Post by CharlesA on 2010-11-04
> **fancypiper said:**
> # In the file /etc/sudoers, put this at the bottom of the file to allow
# the members of the group sudo to not need a password:
%sudo ALL=NOPASSWD: ALL

You'd still have to use "sudo" which the OP doesn't want to do.

---

