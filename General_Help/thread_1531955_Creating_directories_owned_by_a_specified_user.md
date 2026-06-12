---
title: "Creating directories owned by a specified user"
date: 2010-07-15
forum: General Help
---

### Post by dsub42 on 2010-07-15
Hi I have just installed an SSD as a secondary hard drive and formatted as ext4. (the Ubuntu installation is on a different drive)

Im very new to linux, Could someone inform me how I would go about creating a directory on the SSD that is owned by the user 'Test user'

Im sorry if this is a daft question, im just moving from windows to linux and struggling a lot.

Any help would be appreciated

---

### Post by slooow on 2010-07-15
Start a terminal
log in as your test_user with "su test_user"
then type "sudo mkdir /directory_name"
if you have no clue what the command mean, you can look them up with
"man command_name"

---

### Post by linuxman94 on 2010-07-15
> **slooow said:**
> Start a terminal
log in as your test_user with "su test_user"
then type "sudo mkdir /directory_name"
if you have no clue what the command mean, you can look them up with
"man command_name"

That will create a directory owned by root, not by "test user"

---

### Post by linuxman94 on 2010-07-15
By default, the directory will be owned by the user who created it. If you just want that specific user to be able to access and modify the files in that directory, just right-click the folder and select "Properties" then click the tab called "Permissions" and configure the permissions.

---

### Post by dsub42 on 2010-07-16
but how do i make a directory on a different drive using the command interface??

unbuntu is installed on the standard hard disk .. i have just installed an SSD and want to create a user owned directory on that??

---

### Post by Braik on 2010-07-16
Hi there,
 
Well, i think slooow is partially right, let me explain you.
 
First you have to mount your hard drive for example in this way
```
 sudo mkdir /mnt/ssdrive
sudo mount /dev/sdXY /mnt/ssdrive

```
So you create a path in the /mnt folder and then you mount your drive partition sdXY (XY are the identifiers of this drive) on that path
 
Once this is done you have to follow the slooow technique
```
 su test_user
cd /mnt/ssdrive
mkdir directory_name

```
the mkdir command without sudo to keep the test_user as the owner
And thats it...

---

### Post by dsub42 on 2010-07-16
Thanks Braik but im just a little confused with the first stage
 sudo mkdir /mnt/ssdrive
sudo mount /dev/sdXY /mnt/ssdriv
My drive device is called 'SSD' ... could you clarify what you mean here?

mount: special device /dev/sdXY does not exist

what is the XY equivelant of my drive or how would i find out?

---

### Post by Braik on 2010-07-16
Hi there,
 
> sudo mkdir /mnt/ssdrive
sudo mount /dev/sdXY /mnt/ssdriv
My drive device is called 'SSD' ... could you clarify what you mean here?

 
You mean that 'SSD' is the label... in this first step I am guiding you to create a mounting point for your drive (/mnt/ssdrive)
 
type this at terminal
```

fdisk -l

```
with an lowercase L and not a one
 
You will have a list of HD of your system and you will identify the XY I asked you to put, if you don't understand the output just paste the result here and I will try to explain you

---

### Post by QLee on 2010-07-16
Braik probably didn't note that you've just joined and might need a little clarification.

[QUOTE=dsub42]Thanks Braik but im just a little confused with the first stage
 sudo mkdir /mnt/ssdrive [/QUOTE]

The suggestion is to open a terminal window and enter the command (the "ssdrive" portion of the command is a placeholder for the name you choose for the folder (directory). just using ssdrive in this case should be fine but you could choose a different name if you wanted to (it's just to give you a named location for the drive in your filesystem).

[QUOTE=dsub42]sudo mount /dev/sdXY /mnt/ssdriv[/QUOTE]

This command is to mount your drive to the location. (the reason Fdisk -l is run, is so Braik can tell you what to fill in for the placeholders X & Y in the device node style of notation)

After you have given the data by entering Braik's suggested fdisk command it should be possible to determine the X & Y on your system. And after you have the correct partition mounted you can follow the rest of the advice to create the directory you asked for.

Caveat: However, since you are a new user, normally a user has the proper permissions in their home directory (they own those files) and sometimes new users get confused about the differences in GNU/Linux filesystems, there may not be a need to create a user owned folder someplace outside of the user's home. Just wanted to mention that for your consideration.

---

