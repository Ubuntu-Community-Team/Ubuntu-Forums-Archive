---
title: "File perms problem"
date: 2012-08-10
forum: General Help
---

### Post by oygle on 2012-08-10
I have somehow messed up the file/folder permissions, and now can't access files, unless the perms is changed in Nautilus.

How do I change it back to what is was, that is, the default perms for files and folders under /home/

I have a few recursive commands, but they don't seem to be doing what I need

```

sudo chown -R fred:fred /home/fred/Documents

$ sudo chmod -R 644  /home/fred/Documents

```

Seems a new folder is given a 755, and a new file is given a 644, so I need a recusrive chown and a recursive chmod to do that for all folders/files.

---

### Post by claracc on 2012-08-10
Files inside my /home/user/Documents have permissions 664

Normal folders in /home/user as Music, Documents, Downloads, videos have permissions 751, The Mail one is 700.

The -R in chmod and chown is to do the changes recursively, why you say the chown and chmod -R command are not doing what you say?

---

### Post by albandy on 2012-08-10
I recomend you to use  700 for you home folder, as with 755 or 750 you are allowing other users to acces it.


Try this script I have made:

```

#! /bin/bash
FOLDER_DEFAULT=755
FILE_DEFAULT=644

find /home/fred | while read data
do
if [ -d "$data" ]
then
echo "$data is a folder. Changing to $FOLDER_DEFAULT"
chmod $FOLDER_DEFAULT "$data"
else
echo "$data is a file. Changing to $FILE_DEFAULT"
chmod $FILE_DEFAULT "$data"
fi
done


```

---

### Post by ajgreeny on 2012-08-10
And you should not need sudo for the chmod command if the files are owned by you, which they should be in your home.

Why do you believe they are owned by somebody else, I presume root?

---

### Post by oygle on 2012-08-12
> **claracc said:**
> The -R in chmod and chown is to do the changes recursively, why you say the chown and chmod -R command are not doing what you say?

They did have all ????? for perms after I did the cmod, but then I found out that Nautilus can do a recursive change on perms, so I used that.

I would rather use shell/bash though.

---

### Post by oygle on 2012-08-12
> **albandy said:**
> I recomend you to use  700 for you home folder, as with 755 or 750 you are allowing other users to access it.

Thanks for the script, I will use that. No-one else here used the Ubuntu computer.

---

### Post by oygle on 2012-08-12
> **ajgreeny said:**
> And you should not need sudo for the chmod command if the files are owned by you, which they should be in your home.

Why do you believe they are owned by somebody else, I presume root?

I can't remember how they got there, but some videos and other files had root as owner, so I needed to change those.

Will I get a message if I don't use sudo, and then try and change file perms that are owned by root. I'm the 'admin', and in the same group as root of course.

I just answered my own question, tried

```

fred@ubuntu64:~$ sudo chown -R fred:fred /home/fred
chown: cannot access `/home/fred/.gvfs': Permission denied

```

---

