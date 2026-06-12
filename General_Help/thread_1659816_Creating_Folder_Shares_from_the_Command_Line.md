---
title: "Creating Folder Shares from the Command Line"
date: 2011-01-04
forum: General Help
---

### Post by ForrestDean on 2011-01-04
Is there a way to create a shared folder on the Ubuntu system from a command line that is viewable from Windows.  Is there a way to do this without using any gui and without having to edit any files?

---

### Post by Morbius1 on 2011-01-04
Yes there is and it's usually associated with a GUI only application.

Let's use as an example the Documents folder in your home directory: /home/morbius/Documents

To create a share:
```
net usershare add documents /home/morbius/Documents "morbius documents" everyone:F guest_ok=y
```net usershare add = is the command sequence to add
documents = is the name of the share
/home/morbius/Documents = is the path to the directory you wish to share
"morbius documents" = is the comments next to the share
everyone:F = this will allow users the ability to read / write (F) to the share. If you only want to allow read access then substitute R for F.
guest_ok=y = will allow guest access. If you want only authenticated useres then change that to guest_ok=n"

The only thing left to do is change the permissions on the target directory to allow "guests" to actually write to that share:
```
chmod 0777 /home/morbius/Documents
```To verify the share definition run the following command:
```
net usershare info --long
```In this particular case you should get the following output:
> [documents]
path=/home/morbius/Documents
comment=morbius documents
usershare_acl=Everyone:F,
guest_ok=yIf it doesn't work or you want to delete it:
```
net usershare delete documents
```Note: This will the delete the sharing of th Documents folder not delete the folder itself.

---

### Post by ForrestDean on 2011-01-04
That worked perfectly.  Thank you very much! :)

---

### Post by Phasma Felis on 2012-04-07
I tried following these instructions, and everything appears to be working correctly on the Ubuntu side, including the expected output from "net usershare info --long", but I can't see the shared folder on the Windows machine. I assume it should be in My Network Places? On the suggestion of another site, I've loaded up /etc/samba/smb.conf, changed the workgroup name to match the Windows box, set "browseable = yes" and "read only = no", but it doesn't seem to make a difference.

The server is running Ubuntu 11.10, and the client is running Windows XP. (I'd like to get it working with an OS X 10.6 machine as well.)

---

### Post by Morbius1 on 2012-04-08
You should start a new topic since the original post dealt with a specific request on a system with a functional network and Samba configuration.

When you do, it would help if you included the output of each of the following commands:
```
testparm -s
net usershare info --long
hostname
smbtree
```It could be something simple like your hostname being 16 characters or longer in length.

BTW, Usershares as described in this topic have share definitions in /var/lib/samba/usershares. It appears you also have share definitions for the same folder in smb.conf. They are both Samba shares but it's anyone's guess which one Samba will listen to so get rid of one or the other.

---

