---
title: "What is fmask umask and dmask?"
date: 2010-04-13
forum: General Help
---

### Post by tonysonney on 2010-04-13
Hi Guys,
          I googled for it. But couldnt find anything proper. There were explanations saying fmask is related to umask. But what is umask?! I even found a thread in our forum. [http://ubuntuforums.org/showthread.php?t=7702](http://ubuntuforums.org/showthread.php?t=7702) . Am I right in saying umask is the permission of the file?
say 7 read, write and execute
6 read and write 

Am I right? Forgive my ignorance.

Cheers,
Tony

---

### Post by mcduck on 2010-04-13
fmask = file mask, umask = user mask and dmask = directory mask. And they all are used to define permissions (umask sets them to both files and directories, while fmask only applies to files and dmask to directories).

The masks are no the permissions of the file, they are used to get the permissions you want. In addition masks can't add any permissions, they only limit what permissions a file or a directory *can* have.

---

### Post by NiGhtMarEs0nWax on 2010-04-13
uhm, i always get confused too, but i think masks are the opposite from straight forward permissions, 

ie 777 permissions would be 000 in a mask.
755 would be 022 in a mask.
750 would be 027 in a mask.

i could be wrong, in fact, i probably am. if someone could clarify this for me?

---

### Post by Drenriza on 2010-04-13
umask is set to controld permissions (set by the server administrator) for newly created files & directories. That is created by other users on the system.

When you set a umask for example 0666 then you need to minus this 0666 with 0777 for a directory and 0666 for files.
And then you get a system umask of 0111. 0666 - 0777 = 0111 for your directoryes, and 0555 for your files.

The directory number to minus your umask with is 0777 and
the files number to minus your umask with is 0666

Another example. Directory.
0222 - 0777 = 0555
0274 - 0777 = 0503

and Files.
0222 - 0666 = 0444
0264 - 0666 = 0402

a umask 0000 is = 0777 = all permissions
Read
Write
Execute

a umask 0111 is = 0666 = Read + Write

When looking at permissions you see

x xxx xxx xxx
x = Type (directory, file, special files e.c.t)
#1 xxx = users
#2 xxx = groups
#3 xxx = others

These 3 x then has a value.
4 2 1   4 2 1   4 2 1
X X X   X X X   X X X
R W X   R W X   R W X

R = Read
W = Write
X = Execute

the value 7 is all the numbers in a XXX group put together 4+2+1 = 7 = all permissions.

If it was 0752 then it would be
#1 Users = all permissions 4+2+1 = 7
#2 Groups = Write + Execute 4+1 = 5
#3 Others = Write 2 = 2

Hope this helps

ADDED:
For the first digit in a umask. Its a sticky bit.

(4)xxx sets the SUID 
(2)xxx sets the SGID 
(1)xxx sets the sticky bit 
(6)xxx sets both the SUID and SGID 
(7)xxx sets all three 

The sticky bit does if more people (a group) has 0777 permissions to a file, then they can delete the file also. If i want
them to have all permissions but not able to delete the file i can set a sticky bit 1777 and then its only the owner of the file who can delete it. The group can still see the file, open it, change its contents. They can do all that the permissions alow them to EXECT deleting the file.

And then the permissions would look like this rwx-rwx-rwt the t reporsents the sticky bit. A umask of 1777


Its about remembering :)

---

### Post by NiGhtMarEs0nWax on 2010-04-13
what's the point in the first 0?

---

### Post by Drenriza on 2010-04-13
Edited #4

---

### Post by cjhabs on 2010-04-13
> **NiGhtMarEs0nWax said:**
> what's the point in the first 0?

It controls special permissions such as set uid (run as another user) and the sticky bit (keep a file in memory after executing)..

---

### Post by cong06 on 2010-04-13
Drenriza your post has been bookmarked in my firefox profile.

Sometimes Manpages just don't explain enough. And the general idea is good, but I'm also glad to know how the math is *actually* done.

---

### Post by NiGhtMarEs0nWax on 2010-04-13
> **cjhabs said:**
> It controls special permissions such as set uid (run as another user) and the sticky bit (keep a file in memory after executing)..


nice, thank you. :)

---

### Post by tonysonney on 2010-04-13
Thank you very much Drenriza. Does the same rule apply for dmask and fmask (I assume they are same)? 
    I know the permission can be changed using chmode. I recently came to know chown also does the same. Is there any difference between them?

---

### Post by mcduck on 2010-04-13
> **tonysonney said:**
> Thank you very much Drenriza. Does the same rule apply for dmask and fmask (I assume they are same)? 
    I know the permission can be changed using chmode. I recently came to know chown also does the same. Is there any difference between them?

Chown doesn't change permissions, it changes the owner & group.

---

### Post by tonysonney on 2010-04-13
Aah .Ok.. Thanks,
Cheers,
Tony

---

### Post by Drenriza on 2010-04-14
> **tonysonney said:**
> Thank you very much Drenriza. Does the same rule apply for dmask and fmask (I assume they are same)? 
    I know the permission can be changed using chmode. I recently came to know chown also does the same. Is there any difference between them?


umask is a combination of both dmask and fmask. The math/permissions is the same for all 3. 

dmask can only be used for directoryes
fmask can only be used for files
umask is a combination of both and sets the directory and file default permissions at the same time. For the entire system.

```
chmod
``` is used for changing permissions on files/directoryes. 

```
chown
``` is used to change user & group ownership of a file/directory and has nothing to do with permissions on the file/directory.

example.
```
chmod 777 test
``` this would change the default file permissions on test.txt to all permissions for users/group/others.

```
chown cristian:cristian test.txt
``` this will change the user & group ownership of a file to cristian. you can also do 
```
chown root:root test.txt
```
```
chown cristian:economics test.txt
```

or any other owner:group combo.

---

### Post by tonysonney on 2010-04-14
Hi Drenriza,
     Thank you very much. You are a star.

Cheers,
Tony

---

### Post by Drenriza on 2010-04-15
Glad that i was able to help.

I hope the information was usefull in some way. If their is anything else i can help you with at some point. I will gladly help.

Kind Regards

---

### Post by spirit.986 on 2011-03-21
I have searched in google but i wasn't able to find an answer that solves my problem... 

As the question is:
How can i change the umask on a per user basis so that each user can have its own umask to fit his needs?

For example:
I have four accounts on my system ex. 
    -admin1 : admin, 
    -admin2 : admin, 
    -manager : stuff,
    -user : user,

-So now I want everything from the admin group to be by default set to 002 (so that every user that is in the admins group can have a full share (-rwx rwx r--) of everything that is created by the admins).

-Then the similar to the above managers shoud have 022 umask.

-And each of the regular users should have 002 or 022 or 077 it is up to the users choice.

I hope that i have provided enough info thorough the example.

Thanks in advance.. :)

---

### Post by Aleksandar_B on 2011-08-07
> **Drenriza said:**
> umask is set to controld permissions (set by the server administrator) for newly created files & directories. That is created by other users on the system.

When you set a umask for example 0666 then you need to minus this 0666 with 0777 for a directory and 0666 for files.
And then you get a system umask of 0111. 0666 - 0777 = 0111 for your directoryes, and 0555 for your files.

The directory number to minus your umask with is 0777 and
the files number to minus your umask with is 0666

Another example. Directory.
0222 - 0777 = 0555
0274 - 0777 = 0503

and Files.
0222 - 0666 = 0444
0264 - 0666 = 0402

a umask 0000 is = 0777 = all permissions
Read
Write
Execute

a umask 0111 is = 0666 = Read + Write

When looking at permissions you see

x xxx xxx xxx
x = Type (directory, file, special files e.c.t)
#1 xxx = users
#2 xxx = groups
#3 xxx = others

These 3 x then has a value.
4 2 1   4 2 1   4 2 1
X X X   X X X   X X X
R W X   R W X   R W X

R = Read
W = Write
X = Execute

the value 7 is all the numbers in a XXX group put together 4+2+1 = 7 = all permissions.

If it was 0752 then it would be
#1 Users = all permissions 4+2+1 = 7
#2 Groups = Write + Execute 4+1 = 5
#3 Others = Write 2 = 2

Hope this helps

ADDED:
For the first digit in a umask. Its a sticky bit.

(4)xxx sets the SUID 
(2)xxx sets the SGID 
(1)xxx sets the sticky bit 
(6)xxx sets both the SUID and SGID 
(7)xxx sets all three 

The sticky bit does if more people (a group) has 0777 permissions to a file, then they can delete the file also. If i want
them to have all permissions but not able to delete the file i can set a sticky bit 1777 and then its only the owner of the file who can delete it. The group can still see the file, open it, change its contents. They can do all that the permissions alow them to EXECT deleting the file.

And then the permissions would look like this rwx-rwx-rwt the t reporsents the sticky bit. A umask of 1777


Its about remembering :)

Great explanation, but I would like to make a note that sticky bit (first number in umask) only applies to folders not individual files!

---

### Post by spezticle on 2012-08-19
> **Drenriza said:**
> umask is set to controld permissions (set by the server administrator) for newly created files & directories. That is created by other users on the system.

When you set a umask for example 0666 then you need to minus this 0666 with 0777 for a directory and 0666 for files.
And then you get a system umask of 0111. 0666 - 0777 = 0111 for your directoryes, and 0555 for your files.

The directory number to minus your umask with is 0777 and
the files number to minus your umask with is 0666

Another example. Directory.
0222 - 0777 = 0555
0274 - 0777 = 0503

and Files.
0222 - 0666 = 0444
0264 - 0666 = 0402

a umask 0000 is = 0777 = all permissions
Read
Write
Execute

a umask 0111 is = 0666 = Read + Write

When looking at permissions you see

x xxx xxx xxx
x = Type (directory, file, special files e.c.t)
#1 xxx = users
#2 xxx = groups
#3 xxx = others

These 3 x then has a value.
4 2 1   4 2 1   4 2 1
X X X   X X X   X X X
R W X   R W X   R W X

R = Read
W = Write
X = Execute

the value 7 is all the numbers in a XXX group put together 4+2+1 = 7 = all permissions.

If it was 0752 then it would be
#1 Users = all permissions 4+2+1 = 7
#2 Groups = Write + Execute 4+1 = 5
#3 Others = Write 2 = 2

Hope this helps

ADDED:
For the first digit in a umask. Its a sticky bit.

(4)xxx sets the SUID 
(2)xxx sets the SGID 
(1)xxx sets the sticky bit 
(6)xxx sets both the SUID and SGID 
(7)xxx sets all three 

The sticky bit does if more people (a group) has 0777 permissions to a file, then they can delete the file also. If i want
them to have all permissions but not able to delete the file i can set a sticky bit 1777 and then its only the owner of the file who can delete it. The group can still see the file, open it, change its contents. They can do all that the permissions alow them to EXECT deleting the file.

And then the permissions would look like this rwx-rwx-rwt the t reporsents the sticky bit. A umask of 1777


Its about remembering :)

I sort of get this and maybe i'm making it more complicated than it really is, but 0666 - 0777 ... well, that would equal -1 -1 -1 unless you did it the other way around, i could see 0777-0666 = 0111 but... then thats where i get confused.. it's like trying to write while looking into a mirror

---

### Post by Morbius1 on 2012-08-19
This is kind of a confusing thread because fmask, dmask, and umask taken together pertain only to Windows filetypes ( NTFS and FAT32 ) whereas umask alone pertains to both windows and Linux filetypes but are implemented 2 different ways.

[U]On Linux Filesystems 

[/U]At the moment of birth every file has permissions of 666 and every directory has permissions of 777. A system wide umask is created to modify these permissions immediately after birth and it's currently set at 002. So when you create a new file it's permissions are:

666
002 <-- minus the umask
==
664

And every new directory has permissions of:

777
002 <-- minus the umask
==
775

_On Windows Filesystems_

Windows fileystems have no Linux file permission attributes so a virtual filesystem is used to create a "view" to give them the appearance that they do have them. The system wide umask has no affect on these filesystems nor does a chmod or a chown. They can only be set when the "view" is created in fstab.

At the moment of birth NTFS files and folders start out with exactly the same permissions: 777. If you were to set up in fstab a umask of 002 for these partitions then the result would be different from a Linux filesystem:

File: 777 - 002 = 775
Folder: 777 - 002 = 775

The folder setting is fine and that's the way you want them to be but the files have all been made executable - every single one of them. You can change that by separating umask into it's constituent parts: fmask and dmask:

So if you set up fstab this way for an NTFS partition: dmask=002,fmask=113

File: 777 - 113 = 664
Folder: 777 - 002 = 775

---

