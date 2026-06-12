---
title: "auto mount NTFS for a specific user only"
date: 2011-04-14
forum: General Help
---

### Post by barry_hk on 2011-04-14
I am a still a novice at Ubuntu, so please bear with me if I don't get some specifics right.

My ubuntu is 10.10.  I want to automount an internal NTFS partition automatically for one user but not the rest.  How can I do it ?

I tried setting fstab but it seems the automounting will then be done for all users.
I had set chown and chmod to allow only root to mount.  But then I cannot figure out how to sudo mount during the login process. I tried putting in the command "**echo *password* | sudo -S mount /dev/sda3 /media/*partition-name***" in startup applications, but it doesn't work - although this command works fine after I have logged in.

Please help.

---

### Post by Morbius1 on 2011-04-14
(1) Run the following command to see how the system sees your partition:
```
sudo blkid -c /dev/null
```You will get something that looks like this:
> /dev/sdc1: LABEL="BACKUP" UUID="66E4DC83E4DC56C1" TYPE="ntfs" (2) Make a permanent home for the partition to live in:
```
sudo mkdir /media/Data
```(3) Add the following line ( as an example ) to the end of fstab:
```
UUID=66E4DC83E4DC56C1 /media/Data ntfs defaults,nls=utf8,uid=1000,umask=077 0 0
```(4) Save fstab and run the following command to test for errors and mount the new fstab entry:
```
sudo mount -a
```uid=1000 will make you the owner. 
umask=077 will make the partition read / writable by the owner ( the "0" part ) and inaccessible by everyone else ( the "7" part ) - well, inaccessible by everyone but root anyway.

---

### Post by barry_hk on 2011-04-14
Thanks, Morbius1. Will try tomorrow (1am here now... I'm on bed already)

---

### Post by barry_hk on 2011-04-14
Thanks a lot !!  It worked perfectly.

What if, on top of my own full access, I want to grant read access to another one user but not the remaining ?  I guess it has something to do with the umask parameters but cannot find out how.

---

### Post by Morbius1 on 2011-04-15
An example:

[1] Create a new group
```
sudo groupadd newgroup
```[2] Add all the users you want to give access to the partition to that group
```
sudo gpasswd -a morbius newgroup
```[COLOR=Blue]*Note: you will need to logout and login again for the group change to take affect.*[/COLOR]

[3] Modify the fstab line to accommodate the new group users:
```
 UUID=66E4DC83E4DC56C1 /media/Data ntfs defaults,nls=utf8,uid=1000,gid=newgroup,umask=027 0 0
```The "gid=newgroup" will change the group from root.
"umask=027" will make the partition read / writable to you, read only to members of "newgroup", and inaccessible to everyone else.

[COLOR=Blue]EDIT: I modified this post because I didn't read your requirements correctly. Getting sloppy, sorry.

A note on umask:

Each posistion represents a different user:
The first number is the owner.
The second is the group.
The third is everyone else.

Each number represents a type of permission that you want to remove:
0 - does nothing ( meaning full access for that type of user )
1 - Removes execute ( for a directory you need execute to be on or else you won't be able to open it )
2 - Removes write
4 - Removes read

And they're addative so a 7 ( 4+2+1 ) removes everything.
[/COLOR]

---

### Post by barry_hk on 2011-04-15
Dear Morbius1, thanks a lot !  very clear explanation, and it can be applied to similar situation as well.  Thanks again.

---

