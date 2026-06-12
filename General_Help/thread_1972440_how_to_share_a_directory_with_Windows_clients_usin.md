---
title: "how to share a directory with Windows clients using command line?"
date: 2012-05-03
forum: General Help
---

### Post by anon0 on 2012-05-03
This has be done by command line (SSH) because I'm running Ubuntu Server and have no access to the GUI. Right now I have no files being shared.

---

### Post by Gyokuro on 2012-05-03
Hi

Which server release are you using? In case 10.04.4

sudo apt-get install samba smbfs winbind

and then edit /etc/samba/smb.conf

---

### Post by anon0 on 2012-05-03
thanks! smb.conf is pretty big, how about a quick pointer on where to add the line to share a particular directory?

---

### Post by Morbius1 on 2012-05-03
Creating a share from CLI:

> **Morbius1 said:**
> Yes there is and it's usually associated with a GUI only application.

Let's use as an example the Documents folder in your home directory: /home/morbius/Documents

To create a share:
```
net usershare add documents /home/morbius/Documents "morbius  documents" everyone:F guest_ok=y
```net usershare add = is the  command sequence to add
documents = is the name of the share
/home/morbius/Documents = is the path to the directory you wish to share
"morbius documents" = is the comments next to the share
everyone:F = this will allow users the ability to read / write (F) to  the share. If you only want to allow read access then substitute R for  F.
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
guest_ok=y                      If it doesn't work or you want to delete it:
```
net usershare delete documents
```Note: This will the delete  the sharing of th Documents folder not delete the folder itself.
Depending on who you are logged in as and who owns the folder you are trying to share you may need to preface the command with a sudo.

---

### Post by anon0 on 2012-05-03
Thanks, although all I did was added this syntax at the end of the file. 
```
[sharename]
path = ...
writeable = Yes
```

It seems to work. I'm not sure when we need to use the "net" command.

---

### Post by Morbius1 on 2012-05-03
I misread your original post. I thought you wanted to create a Samba share using one line from the terminal.

---

### Post by anon0 on 2012-05-04
> **Morbius1 said:**
> I misread your original post. I thought you wanted to create a Samba share using one line from the terminal.

I see, yes I can run editors from the command line, I just don't have GUI. Thanks for the information!

---

