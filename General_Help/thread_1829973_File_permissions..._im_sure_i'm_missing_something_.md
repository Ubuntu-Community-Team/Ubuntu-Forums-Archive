---
title: "File permissions... im sure i'm missing something obvious"
date: 2011-08-21
forum: General Help
---

### Post by triunenature on 2011-08-21
So i have a computer with 3 users on it, and a folder using samba that everyone on the network has access to.  Lets say that, the folder is stored in /etc/sharedfolder.

What happens is, when user1 puts a folder in it, then logs off, user 2 attempts to modify it and fails, because permission is set to 755, and they are not in the same group.  (even if they were, it should still need to be 775)

Anyway, my current solution is, every 5 minutes a crontab changes permission like so:

chmod 777 -R /etc/sharedfiles && chown useradmin:superadmin -R /etc/sharedfiles

Which works, but seeing as there is getting close to a gig in there, this is a bad solution, as it eats up the computers resources.

Solutions that i think might work:

1) create a script that only changes permissions that need be changed.

2) change file permission settings to force all documents to inherit parent document settings 

The basic problem is, I don't know how to do either of these...

---

### Post by fdrake on 2011-08-21
what you r trying to do is too risky and too complicated. why?  you can simply add all the users that you need in a specific group (create a new group). And than make the folder change group ownership to the new group . apply permission 775 to the folder recursively and you are all set,

note: do you want also users to see each others files/folder? like john sees clair's file and vice-versa?

---

### Post by triunenature on 2011-08-21
> **fdrake said:**
> what you r trying to do is too risky and too complicated. why?  you can simply add all the users that you need in a specific group (create a new group). And than make all that file change group ownership to the new group . apply permission 755 and you are all set,

755 is the problem

7 = user
5 = group
5 = other

The problem is group would need to be 7, and by default it would be 5.  Creating the issue i presented in the first place. Also, since windows users access that file, I need there file permissions set correctly to.  Not to mention, what happens when user1 somehow changes file permissions to 700 on a particular file... with your solution, they'd have to call me, and i'd have to investigate.  I am trying to avoid all that.

And none of my solutions are risky...  My current solution is just resource intensive, but not risky

In this shared directoy /etc/sharedfiles, Yes everyone needs 100% access to all the files, so john needs to see bob's files.  Now in /home/bob, that folder is restricted to bob, and /home/john is restricted to john.

---

### Post by Morbius1 on 2011-08-21
>  2) change file permission settings to force all documents to inherit parent document settings There are a number of ways to do that both through Samba itself or through Linux file permissions but here's one way:

After the remote user has authenticated himself to samba force his and everyone else's identity to be the same. For example:
```
[sharedfolder]
path = /etc/sharedfolder
valid users = john, bob, whoever
force user = useradmin
```Any new folder saved will have as owner useradmin ( or whoever you set in force user ). The "valid users" has to do with authentication and the "force user" has to do with after passing authentication.

[I][COLOR=Blue]As a side note[/COLOR]: You really should get out of the habit of using "chmod 777 -R". The octal mode of chmod isn't smart enough to differentiate between a folder ( which has to have the execute bit on ) and a file. 777 wll make every file executable. One way that doesn't do that is this way:
```
chmod -R a+rwX /etc/sharedfiles
```That will make all folders 777 and all files 666 except those files that were executable to begin with - that's what the big "X" does.
[/I]

---

### Post by fdrake on 2011-08-21
ACLs should work too

```

sudo apt-get install acl
sudo vim /etc/fstab

```
edit fstab and apply acl to the partion containing your folder. something like this;
from this:
/dev/sda1       /               ext4    errors=remount-ro, 0       1
to this
/dev/sda1       /               ext4    errors=remount-ro,acl 0       1

reboot

```
setfacl -Rdm o::rwx /etc/sharedfiles
setfacl -Rdm g::rwx /etc/sharedfiles
setfacl -Rdm u::rwx /etc/sharedfiles
```

now any user should be able to add a file/ folder and the permission(by default) will be for file rw(for everyone) for folder rwx(for everyone)


@Morbius1 : i like your idea of using 1 user , but just a question if useradmin (the forced user) has root like privileges does it mean he would be able to extend its permissions to other folders since you are practically logged in with a local user? i don't know I never tried, so was wondering what happens then? I mean if all users are logged as an user in the system they can changed that users home files and data right? A curiosity that i would like to find out.

---

### Post by Morbius1 on 2011-08-21
Samba constrains you to the share you are accessing. In fact by default samba won't even allow you to follow a symbolic link. If "useradmin" just doesn't feel right then you could even make it "nobody" ( which is the guest user ) if you want.

---

### Post by Topsiho on 2011-08-21
I don't think /etc is the place for your shared folder. /etc contains the system configurations, and your shared folder just doesn't fit in.

And: if you install a new version of Ubuntu, as everybody does once in a while, your system partition(s) get reformated, which destroys all data in it (if not backed up).

The usual procedure is to put /home in it's own partition, which you should NOT format during a new install. So your personal files get preserved (but back them up anyway, one never knows). So my idea is to put the shared folder in the /home partition, setting the permissions as needed.

However: Windows can't read linux file systems, so if you need to read the files from a windows computer (you mentioned samba), then the partition must be an ntfs filesystem. That means that you should create a ***separate partion*** for it, giving it a name, such as shared, and making it an ntfs filesystem. Don't know about permissions in that case.

Or you give it a fat or fat32 filesystem, and forget about permissions (I am afraid).

Hope this helps.

Topsiho

---

### Post by Morbius1 on 2011-08-21
> **Topsiho said:**
> I don't think /etc is the place for your shared folder. /etc contains the system configurations, and your shared folder just doesn't fit in.

And: if you install a new version of Ubuntu, as everybody does once in a while, your system partition(s) get reformated, which destroys all data in it (if not backed up).
I agree that /etc/ is a very odd place indeed for a shared folder.

> The usual procedure is to put /home in it's own partition, which you should NOT format during a new install. So your personal files get preserved (but back them up anyway, one never knows). So my idea is to put the shared folder in the /home partition, setting the permissions as needed.

However: Windows can't read linux file systems, so if you need to read the files from a windows computer (you mentioned samba), then the partition must be an ntfs filesystem. That means that you should create a ***separate partion*** for it, giving it a name, such as shared, and making it an ntfs filesystem. Don't know about permissions in that case.

Or you give it a fat or fat32 filesystem, and forget about permissions (I am afraid).Don't have a arguement with anything you posted except you are looking at this from a dual boot perspective. The original post concers a Samba share accessible by clients on his lan so none of that is relevant.

---

### Post by Topsiho on 2011-08-22
> **Morbius1 said:**
> I agree that /etc/ is a very odd place indeed for a shared folder.

Don't have a arguement with anything you posted except you are looking at this from a dual boot perspective. The original post concers a Samba share accessible by clients on his lan so none of that is relevant.

You might be right, and I may be missing something.
But I think the shared map should be accessible using Samba, from the lan. And I think this means that in this lan there are Windows computers, which should be able to at least read the content of this shared map.

Thanks for agreeing with me that /etc is no place to be for a shared map :)

Topsiho

---

### Post by Morbius1 on 2011-08-22
But my point is that SMB, Samba, cifs is a virtual file system that hides what the actual filesystem is from the client . Locally, Windows cannot access a ext3 partition so the best thing to do as you suggested is to make a shared ntfs or fat32 partition so both OS's can access them. 

But across the network Windows doesn't know that it is an ext3 partition - all it sees is a cifs share.

---

### Post by Topsiho on 2011-08-24
Aha.

In that case I am wrong of course, and have learned something.
Thank you.

Topsiho

---

### Post by linkageless on 2011-08-24
Strikes me that the obvious thing you are missing is setting the default umask of these users. In samba I believe the "create mask" and "directory mask" options are the ones you want, but check the smb.conf man page on your system.

---

