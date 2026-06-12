---
title: "Setting permissions on directory for child objects to follow"
date: 2012-02-05
forum: General Help
---

### Post by dglad4 on 2012-02-05
Okay so after I migrated from Windows Server 2003 to Ubuntu Server 10.04 LTS I've found it harder to work with permissions. Although I have managed to work most of it out like chown and chmod there is one problem. In Windows where you can change file and directory permissions from the Security tab under Advanced I usually wipe the inheritance of the parents permissions and set new permissions for everything under that folder (the child objects). This way when someone creates a new file, permissions are inherited from the parent directory. In Ubuntu I find I set the owner of a folder with chown -R and then the permissions with chmod -R but when someone creates a file in the directory it does not follow the parent. I've come to the conclusion that umask that is set on the volume is giving the files the permissions. Is there a command to set permissions on a parent directory and have the child objects follow? I've put in attachments of what I did with Ubuntu and what I did in Windows to make it work when the OS was originally Windows.

Thanks for your help, much appreciated.

dglad4.

---

### Post by Lampi on 2012-02-05
Your parent directory is missing the [sticky bit]("https://help.ubuntu.com/community/FilePermissions#Sticky_Bit")

chmod +t on the parentfolder will make sure ownership is passed to the "children" ;)

At least that's how I understand it. I don't use it, so feel free to correct me if I'm wrong.

---

### Post by Lars Noodén on 2012-02-05
Close.  You want to set the sticky bit for the group:

```

sudo chmod g+s -R /srv/ds1/Administrators/

```

That will ensure that files created in those directories inherit the same group membership.

---

### Post by Morbius1 on 2012-02-05
I don't think it's the "sticky bit" you want it's the setgid bit.

The sticky bit prevents anyone other that than the owner to remove or rename a file within the directory. The setgid bit forces every file/directory to "inherit" the group of the parent directory.

So to set the setgid bit:
* Change the group of the parent folder ( example ):
```
sudo chown :plugdev /path
```* Then set the setgid:
```
sudo chmod 2775 /path
```* Note: you can also combine the setgid ( 2 ) with the sticky bit (1 ):
```
sudo chmod 3775 /path
```You will have to change the default umask to 002 so that every file will save as:
> owner: plugdev 664

---

### Post by dglad4 on 2012-02-05
> **Morbius1 said:**
> I don't think it's the "sticky bit" you want it's the setgid bit.

The sticky bit prevents anyone other that than the owner to remove or rename a file within the directory. The setgid bit forces every file/directory to "inherit" the group of the parent directory.

So to set the setgid bit:
* Change the group of the parent folder ( example ):
```
sudo chown :plugdev /path
```* Then set the setgid:
```
sudo chmod 2775 /path
```* Note: you can also combine the setgid ( 2 ) with the sticky bit (1 ):
```
sudo chmod 3775 /path
```You will have to change the default umask to 002 so that every file will save as:

Okay well I did what you wrote above except for the last step as I didn't really get what to do. I have found that from all but the last step new files were being created with the parents group. Excellent! Only problem is new files are being created like this -rw-r--r-- so only the user can write to the file, although everyone can rename, delete and ovcourse read the file which is odd behaviour. The parent is set as drwsrwsr-x which the files are not inheriting but folders are receiving drwxr-sr-x. I am totally confused in all this now but maybe you guys understand it. Thank you for all your responses though, I am getting somewhere rather than nowhere :)

---

### Post by Morbius1 on 2012-02-05
Sorry, I should have explained that last step:
```
gksu gedit /etc/profile
```Change the last line to:```
umask 002
```Logout and log back in again.

---

### Post by dglad4 on 2012-02-05
> **Morbius1 said:**
> Sorry, I should have explained that last step:
```
gksu gedit /etc/profile
```Change the last line to:```
umask 002
```Logout and log back in again.

Perfect! That has done the trick :) Just got some questions though. So this is a home NAS setup here with 3 data drives (Data Store x as /srv/dsx) and there are different folders for different things. All data by default should be read to everyone, write for admin and write for owner. Administrators is just the same except access to everyone is denied. ds1/userdata is only writeable to root, everyone else read. Everyones personal data is r+w only to them. finally there is a folder called "public" which is in userdata too and everyone is able to r+w data so everyone can share data.

It looks like umask sets a default for every file in the system nd by changing the numbers to 0 it turns off the default for  user/group/everyone in permissions. Am I right? Because I want to apply the method we just worked out to the drives so under each specific parent all child objects will follow. If I were to set umask to 000 and have the "everyone" state follow the parents too would that effect the operatign system itself or would it be just the same if I used the group users?

Cheers.

---

### Post by Morbius1 on 2012-02-05
You don't want to set umask to 000. Setting it to 002 is relatively harmless since by default ( without a setgid ) it will change a new file from "owner: owner 644" to "owner: owner 664". Owner is still the only one with write access to the file. Changing it to 000 will make every file 666 and at that point you are running Windows ;)

The added requirement relating to using it as a NAS is probably best handled by whatever file transfer protocol you are using.

---

### Post by Lars Noodén on 2012-02-05
It looks like there might be a bug.  I'm not seeing away to unset the setgid bit either numerically (0775) or using the character representations (g=rwx)

---

### Post by Morbius1 on 2012-02-05
> **Lars Noodén said:**
> It looks like there might be a bug.  I'm not seeing away to unset the setgid bit either numerically (0775) or using the character representations (g=rwx)
I noticed that myself. The only way to remove it is :
```
sudo chmod g-s /path
```

---

