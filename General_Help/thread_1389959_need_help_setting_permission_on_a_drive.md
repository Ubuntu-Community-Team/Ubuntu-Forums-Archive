---
title: "need help setting permission on a drive"
date: 2010-01-25
forum: General Help
---

### Post by Mia_tech on 2010-01-25
guys, I have a secondary drive for storage (local drive) which I want to give a regular user rwx rights, but so far unable to... I've tried (all this is at the root level of the drive)

chmod -R ugo+rwx /media/share

no errors here, but still unable to create a file/folder

even tried

chown -R user /media/share

here, I got filename: operation not permitted

this is a fat32 drive, which I'm mounting at boot using fstab file.... like so

/dev/sdb1 /media/share vfat auto 0 0

any help appreciated.

---

### Post by Mia_tech on 2010-01-25
I just changed the entry in the fstab file to

defaults,auto  0 0

same result

---

### Post by howefield on 2010-01-26
I have just done something similar with an ext4 drive.

```
cd /media
sudo chown user Data
```

was all I had to do, but don't know if it is the same with "fat" drives.

---

### Post by rnerwein on 2010-01-26
hi
try this: /dev/sda3 /vista_data ntfs defaults,noauto,umask=000        0    0
just replace the mountpoint by yours and ntfs by vfat - thats works for me with ntfs and windoof is windoof i think
ciao

---

### Post by Morbius1 on 2010-01-26
> **rnerwein said:**
> hi
try this: /dev/sda3 /vista_data ntfs defaults,noauto,umask=000        0    0
just replace the mountpoint by yours and ntfs by vfat - thats works for me with ntfs and windoof is windoof i think
ciao

We can debate whether you want the "noauto" option in that fstab line as this will make it so that partition will not mount at boot but the umask=000 will give you what you want.

Your original idea of using chmod and chown only works for linux filesystems - ext3/4. You set permissions and ownership on windows filesystems in fstab.

---

### Post by Mia_tech on 2010-01-26
yes, aparently fat32/ntfs partition work a bit funny in linux, but I finally got it working; now umask=000 gives everyone rwx rights, but how about if I want to put my users in a group and give that group rwx rights only... how would "umask=" look in that case, or there would be extra entries in the fstab file

thanks

---

### Post by Morbius1 on 2010-01-26
Change this:
> /dev/sda3 /vista_data ntfs defaults,noauto,umask=000        0    0To this:
> /dev/sda3 /vista_data ntfs defaults,noauto,[COLOR=Blue]gid=group_number,umask=007[/COLOR]        0    0For example, by default all new users created in ubuntu are members of the plugdev group ( gid=46 ) so the line would look like this:
/dev/sda3 /vista_data ntfs defaults,noauto,[COLOR=Blue]gid=46,umask=007[/COLOR]        0    0

[COLOR=Blue]EDIT:[/COLOR]
The umask digits represent owner,group,others. A "0" = rwx, a 7 = no access.
In this case the owner (root) and all members of plugdev will have rwx.

---

### Post by Morbius1 on 2010-01-26
You know, if you ever plan on sharing that partition across your home network and you want to use nautilus-share you might consider going all the way with this thing and take possession of the mount point:

Using the same example, this:
> /dev/sda3 /vista_data ntfs defaults,noauto,[COLOR=Blue]gid=46,umask=007[/COLOR]        0    0Would become this:
> /dev/sda3 /vista_data ntfs defaults,noauto,[COLOR=Blue]uid=1000,[COLOR=black]gid=46,umask=007[/COLOR][/COLOR]        0    0The uid is the user id and 1000 should be you. To verify that uid is 1000 type **id** in a terminal. Then to share it in nautilus you will be able to do that without jumping through hoops.

---

### Post by Mia_tech on 2010-01-26
> **Morbius1 said:**
> You know, if you ever plan on sharing that partition across your home network and you want to use nautilus-share you might consider going all the way with this thing and take possession of the mount point:

Using the same example, this:
Would become this:
The uid is the user id and 1000 should be you. To verify that uid is 1000 type **id** in a terminal. Then to share it in nautilus you will be able to do that without jumping through hoops.

isn't that kind of redundant? giving yourself access and the group... if you're member of the group you don't need to give access to yourself

---

### Post by Morbius1 on 2010-01-26
> isn't that kind of redundant? giving yourself access and the group... if you're member of the group you don't need to give access to yourselfYou're correct, but nautilus-share ( right click the folder > Sharing Options ) by default allows a user to share only folders he owns. Root owns /vista_data in this example, not you.

You can "gksu nautilus" and share the folder as root but that just seems kind of spooky.;) You can also set natilus-share to allow users to share folders other than the ones they own by setting a parameter in smb.conf but then all users will have this ability.

If you have no intention of sharing this partition over the lan using nautilus-share, then you are correct it's redundant and unnecessary.

---

### Post by Mia_tech on 2010-01-26
well, even if I would to share the drive over the network, I would make a group "netusers" add all my network users to this group and put it in the fstab file.... that way I don't have to worry about setting permission to a single user, and when it comes to troubleshoot user permission it is a lot easier if you use a group instead of users for permission weather it is a folder or a file.

---

### Post by Morbius1 on 2010-01-27
Don't mean to beat a dead horse but I think you and I are are talking past each other. 

You're talking about "Classic Sharing" where a share definition can look like this and is located in **smb.conf **:
```
[sharename]
comment = Any comment you like
path = /vista_data
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force group = netusers 
```I'm talking about "Simple Sharing" ( aka, Nautilus-share, or Usershare ) where the share definition can only have 4 lines, looks like this, and is located in **/var/lib/samba/usershares**:
```
[sharename]
path=/vista_data
comment=Any comment you like
usershare_acl=Everyone:F,
guest_ok=y

```To create a Nautilus-share you open Nautilus, right click a folder you own, select "Sharing Options", and check 1 to 3 boxes. When you click "Create Share" nothing is added to smb.conf.

When you use "Classic Samba" one way or another you have to supply a sudo password to create the share. With Nautilus-share you do not because by default a user can only share a folder he owns.

With the partition mounted this way:
```
/dev/sda3 /vista_data ntfs defaults,noauto,[COLOR=Black]gid=46,umask=007[/COLOR]       0    0                      
```The owner is root so the user cannot use Nautilus-share to share /vista_data unless you do the things I outlined in post #10. With the addition of uid=1000 the owner becomes you so now you can use Nautilus-share.

Since you seem to be using "Classic Sharing" this is really all academic.

---

