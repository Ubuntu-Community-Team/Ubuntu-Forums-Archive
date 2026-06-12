---
title: "Setting up folder access  permissions"
date: 2011-10-07
forum: General Help
---

### Post by faixan on 2011-10-07
Hi,

i need some really basic level help regarding file/folder access permission settings in ubuntu.
i've been using Ubuntu Maverick for about 8 months now, and have protected my files so far by not letting any one else use my computer, but that's not going to be possible any more.
i've read like dozen internet pages about 

chmod && chown and also understan the 4+2+1 logic but still i'm not able to apply all this.
what i want to do is that there are a few folders that i don't want any one to be able to access along with the stuff inside them, even with "sudo".
so if someone can please help and explain all the procedure to me.

for my understanding, suppose my username is  "hx" and the folder name is "prvt_fldr".

Thank you.

---

### Post by nothingspecial on 2011-10-07
If you give others access to sudo, you give them access to your files.

The answer is to not give the other users sudo.

---

### Post by faixan on 2011-10-07
> **nothingspecial said:**
> If you give others access to sudo, you give them access to your files.

The answer is to not give the other users sudo.

i don't want to give them access in any way, not even with sudo...

---

### Post by matt_symes on 2011-10-07
Hi

> **nothingspecial said:**
> If you give others access to sudo, you give them access to your files.

The answer is to not give the other users sudo.

This is very true.

For a different approach, I suppose you could create some encrypted directories to keep your confidential files in. Have a look at Cryptkeeper for an idea of password protected directories.

Kind regards

---

### Post by faixan on 2011-10-07
> **matt_symes said:**
> Hi



This is very true.

For a different approach, I suppose you could create some encrypted directories to keep your confidential files in. Have a look at Cryptkeeper for an idea of password protected directories.

Kind regards

can't i do it any simple way... i mean i'm beginner, not that good yet :(

---

### Post by matt_symes on 2011-10-07
Hi

Cryptkeeper is pretty simple. 

In Lucid you get a panel applet that allows you to create a directory with a password. 
To access that directory you unlock it by entering the same password from the same applet.
This is all through the desktop. No CLI at all.

Unsure about later versions of Ubuntu.

Kind regards

---

### Post by WasMeHere on 2011-10-07
Hi

Unless your directories with secret files are encrypted, someone at your computer can reboot with a live CD or USB and read all your files.

An easy way to get encryption is to select it when you install Ubuntu.

But take your time and read about *Cryptkeeper* as suggested by *matt_symes*. I think you can make it work.

If you want a reasonable level of security, don't give anyone else administration privileges (to run sudo)! And give only yourself read access to the relevant directories and files. Recently I explained *chmod*, have a look:
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11314855&postcount=2_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11314855&postcount=2")

Have fun
Olle

---

### Post by faixan on 2011-10-07
> **matt_symes said:**
> Hi

Cryptkeeper is pretty simple. 

In Lucid you get a panel applet that allows you to create a directory with a password. 
To access that directory you unlock it by entering the same password from the same applet.
This is all through the desktop. No CLI at all.

Unsure about later versions of Ubuntu.

Kind regards

Thanks, this seems to be working. i just made up a test text file and tested with other user accounts, seems working so far.. :) :)
thanks for help

---

### Post by faixan on 2011-10-07
> **Olle Wiklund said:**
> Hi

Unless your directories with secret files are encrypted, someone at your computer can reboot with a live CD or USB and read all your files.

An easy way to get encryption is to select it when you install Ubuntu.

But take your time and read about *Cryptkeeper* as suggested by *matt_symes*. I think you can make it work.

If you want a reasonable level of security, don't give anyone else administration privileges (to run sudo)! And give only yourself read access to the relevant directories and files. Recently I explained *chmod*, have a look:
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11314855&postcount=2_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11314855&postcount=2")

Have fun
Olle

that all explains only how to grant access to file/folders, what about revoking... like how would i revoke access of account named "ot" to file "prvt_fldr" at path /home/prvt_fldr while my account name is "hx"
what would be the command for revoking all sort of access of "ot"

---

### Post by matt_symes on 2011-10-07
Hi

Anybody with sudo access can do what they want on your machine. 

You might find ACL may help. I have not played with them myself so others will comment on the usefulness of them in this situation.

You can, of course, edit your sudoers file to limit commands to specific users (such as disallowing chmod to all users but yourself  which would have the effect of not allowing other users to make executable scripts - i expect not what you want)  but you wanted it easy ?....

The easy root is encryption.

Kind regards

---

### Post by faixan on 2011-10-07
> **matt_symes said:**
> Hi

Anybody with sudo access can do what they want on your machine. 

You might find ACL may help. I have not played with them myself so others will comment on the usefulness of them in this situation.

You can, of course, edit your sudoers file to limit commands to specific users (such as disallowing chmod to all users but yourself  which would have the effect of not allowing other users to make executable scripts - i expect not what you want)  but you wanted it easy ?....

The easy root is encryption.

Kind regards

i understand the sudo access part, and that is one of the things i want to be done that no one other than my account should be able to use "sudo" along with a few certain files/folders that would become inaccessible to all other users except me...
and by easy i only mean that someone explain the whole procedure with a little more detail and better named files than used elsewhere on internet. :\

---

### Post by WasMeHere on 2011-10-08
> **faixan said:**
> that all explains only how to grant access to file/folders, what about revoking... like how would i revoke access of account named "ot" to file "prvt_fldr" at path /home/prvt_fldr while my account name is "hx"
what would be the command for revoking all sort of access of "ot"
(This system was developed at universities once upon a time, when the computers were far away and people had terminals in their rooms.) You can set/unset read,write,execute access for user,group,others.. *Group* refers to other users in the same group as you, *other* refers to people outside your group. So you revoke access to group and others
```
chmod -R go-rwx /home/prvt_fldr
``` or 
```
chmod -R 700 /home/prvt_fldr
``` Watch the result with
```
ls -l
```
So in order to revoke access of account named "ot" this way, you also revoke access to all other users except yourself (your own user account).

---

### Post by faixan on 2011-10-08
> **Olle Wiklund said:**
> (This system was developed at universities once upon a time, when the computers were far away and people had terminals in their rooms.) You can set/unset read,write,execute access for user,group,others.. *Group* refers to other users in the same group as you, *other* refers to people outside your group. So you revoke access to group and others
```
chmod -R go-rwx /home/prvt_fldr
``` or 
```
chmod -R 700 /home/prvt_fldr
``` Watch the result with
```
ls -l
```
So in order to revoke access of account named "ot" this way, you also revoke access to all other users except yourself (your own user account).
This is what i tried and it's output.

```

user@ubuntu:~ $chmod -r 700 /media/****/prvt_test/
chmod: cannot access `700': No such file or directory
chmod: changing permissions of `/media/***/prvt_test/': Operation not permitted

```

then i tried with sudo and this is what i got in output

```

[05:44 PM] user@ubuntu:~ $sudo chmod -R 700 /media/****/prvt_test/
[05:44 PM] user@ubuntu:~ $cd /media/****/prvt_test/
[05:44 PM] user@ubuntu:/media/****/prvt_test $ls -l
total 144
-rwxrwxrwx 1 root root 45437 2011-10-08 17:29 266487_460s.jpg
-rwxrwxrwx 1 root root 95480 2011-10-08 17:29 267734_460s.jpg

```


i'm so lost on this :'(

---

### Post by WasMeHere on 2011-10-08
> **faixan said:**
> This is what i tried and it's output.

```

user@ubuntu:~ $chmod -[COLOR="Red"]r[/COLOR] 700 /media/****/prvt_test/
chmod: cannot access `700': No such file or directory
chmod: changing permissions of `/media/***/prvt_test/': Operation not permitted

``` [COLOR="Red"]r[/COLOR] should be [COLOR="Red"]R[/COLOR]

then i tried with sudo and this is what i got in output

```

[05:44 PM] user@ubuntu:~ $sudo chmod -R 700 /media/****/prvt_test/
[05:44 PM] user@ubuntu:~ $cd /media/****/prvt_test/
[05:44 PM] user@ubuntu:/media/****/prvt_test $ls -l
total 144
-rwxrwxrwx 1 root root 45437 2011-10-08 17:29 266487_460s.jpg
-rwxrwxrwx 1 root root 95480 2011-10-08 17:29 267734_460s.jpg

```
What about the stars? Did you put them there for the post or did you actually use **** in your command line?

I see that root owns the files. This explains why you need *sudo*. But it did not change the access flags to what it should
```
-rwx------
```
What filesystem is it? chmod works on linux type file systems, but windows type file systems, FAT, Fat32 and NTFS have a different way of setting the file access. From linux you would do it when you mount the partition.

If you keep your secret files in a partition with FAT, Fat32 or NTFS, use encryption! If you keep them in a linux partition, chmod will work and give a reasonable level of protection.

---

### Post by faixan on 2011-10-08
> **Olle Wiklund said:**
> What about the stars? Did you put them there for the post or did you actually use **** in your command line?

I see that root owns the files. This explains why you need *sudo*. But it did not change the access flags to what it should
```
-rwx------
```
What filesystem is it? chmod works on linux type file systems, but windows type file systems, FAT, Fat32 and NTFS have a different way of setting the file access. From linux you would do it when you mount the partition.

If you keep your secret files in a partition with FAT, Fat32 or NTFS, use encryption! If you keep them in a linux partition, chmod will work and give a reasonable level of protection.

those stars are just the drive name i hid here... i'm bad but not that bad :P
and yes this partition mounted is NTFS :\
and i figured the "r" & "R" part too, but thanks for confirmation...
so now i gotta move all my files roughly 4GB in my WUBI partition :\ :( :(

---

### Post by faixan on 2011-10-08
and one thing i was trying but didn't work, to put my user account in "root" group, but it doesn't work from the Users and Groups settings in ubuntu... what am i doing wrong there? :s

---

### Post by WasMeHere on 2011-10-08
Don't worry about that! Run your normal activities as a 'normal' user and use the *sudo* command to run the system tasks!

[S]Back to the disk: what file system is it?
Run *sudo fdisk -lu* and post the output![/S]

There is another possibility and it is to create another linux partition, with e.g *ext3* file system, and keep your files there. They need not be in the system partition (WUBI in your case).

---

### Post by faixan on 2011-10-08
> **Olle Wiklund said:**
> Don't worry about that! Run your normal activities as a 'normal' user and use the *sudo* command to run the system tasks!

[S]Back to the disk: what file system is it?
Run *sudo fdisk -lu* and post the output![/S]

There is another possibility and it is to create another linux partition, with e.g *ext3* file system, and keep your files there. They need not be in the system partition (WUBI in your case).

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    63488879    31744408+   7  HPFS/NTFS
/dev/sda2        63488880   488375999   212443560    f  W95 Ext'd (LBA)
/dev/sda5        63488943   268285499   102398278+   7  HPFS/NTFS
/dev/sda6       268285563   488375999   110045218+   7  HPFS/NTFS


```

---

### Post by faixan on 2011-10-08
> There is another possibility and it is to create another linux partition, with e.g ext3 file system, and keep your files there. They need not be in the system partition (WUBI in your case).

well for now i'm gonna go with moving my stuff... but i'm keeping this option in mind when i do the complete re hauling of my system. :) thanks :)

---

### Post by WasMeHere on 2011-10-08
Are you satisfied with your WUBI installation? In that case keep it. Otherwise you could make a dual boot system with Ubuntu and Windows.

0. Keep your secret files where they are and encrypt them!

1. Is there space enough left on any of your partitions to make a linux partition for your secret files? Mount them all and run ```
df
``` and post the result, unless you can decide without showing me.

2. Maybe it is an option to keep your secret files in the WUBI partition, but I would *not* suggest that.

3. You can also keep them on a USB disk or stick. In this case, keep your secret files encrypted!

*. Always remember to take backup regularly!

Think about this for a while ... and come back

---

### Post by faixan on 2011-10-08
there's enough space in my WUBI partition, and all other options i've noted. i'll use any of those when i start fixing things up, for now i need an extremely quick solution... that's why i'm gonna go with moving the files. :)

---

### Post by faixan on 2011-10-11
> **Olle Wiklund said:**
> (This system was developed at universities once upon a time, when the computers were far away and people had terminals in their rooms.) You can set/unset read,write,execute access for user,group,others.. *Group* refers to other users in the same group as you, *other* refers to people outside your group. So you revoke access to group and others
```
chmod -R go-rwx /home/prvt_fldr
``` or 
```
chmod -R 700 /home/prvt_fldr
``` Watch the result with
```
ls -l
```
So in order to revoke access of account named "ot" this way, you also revoke access to all other users except yourself (your own user account).

moved the files and all this worked like a charm...

ummm, but i think in hurry i missed "-R" what difference would it make?? :\

---

### Post by haqking on 2011-10-11
> **faixan said:**
> moved the files and all this worked like a charm...

ummm, but i think in hurry i missed "-R" what difference would it make?? :\

-R means do it recursively

---

### Post by faixan on 2011-10-11
> **haqking said:**
> -R means do it recursively

ok, that means it'll apply the permissions to the folders present inside as well... right?!

---

### Post by Lars Noodén on 2011-10-11
> **faixan said:**
> ok, that means it'll apply the permissions to the folders present inside as well... right?!

It will also change the files' permissions, too.  That's something you may not want, at least in regards to the executable bit.  You can use **find** instead to apply the permissions to the folders and files separately.

```

# set permissions for directories
find /home/prvt_fldr -type d -exec chmod u=rwx,g=,o= {} \;

# set permissions for plain files
find /home/prvt_fldr -type f -exec chmod u=rw,g=,o= {} \;

```

---

### Post by haqking on 2011-10-11
> **Lars Noodén said:**
> It will also change the files' permissions, too.  That's something you may not want, at least in regards to the executable bit.  You can use **find** instead to apply the permissions to the folders and files separately.

```

# set permissions for directories
find /home/prvt_fldr -type d -exec chmod u=rwx,g=,o= {} \;

# set permissions for plain files
find /home/prvt_fldr -type f -exec chmod u=rw,g=,o= {} \;

```

edit: answered above by lars

---

### Post by faixan on 2011-10-13
> **haqking said:**
> edit: answered above by lars

Thanks a lot guys. :) :)

---

