---
title: "Delete File From Public Group"
date: 2012-03-22
forum: General Help
---

### Post by hateborne on 2012-03-22
Afternoon Ladies and Gents,

I am trying to delete a file owned by myself but in a different group. 

Specifically:
```
-rwxr-xr-x 1 hateborne www-data     18 2012-03-22 13:39 rootfile.txt
```My groups:
```
uid=1000(hateborne) gid=1000(hateborne) groups=1000(hateborne),4(adm),20(dialout),24(cdrom),33(www-data),46(plugdev),107(lpadmin),108(sambashare),109(admin)
```I have access to the group and I am the owner of the file. However, I cannot remove the file. I am met with a 'Permission denied' message. Yes I could sudo to remove it, but that isn't what I am trying to accomplish. I am trying to allow users in group "www-data" to delete their own files and have access (but not able to delete) the group's files.

Is there some fancy trick or some obvious error I am making?

-Hate

---

### Post by papibe on 2012-03-22
Hi hateborne.

The permission to delete a file doesn't reside on the file itself, but in the directory that contains it.

For example:
```
$ mkdir temp
$ cd temp
$ touch file1
$ touch file2
$ chmod 777 file1 file2
ls -la
total 8
dr**[COLOR="Red"]w[/COLOR]**xr-xr-x  2 user user 4096 2012-03-22 15:10 .
drwxr-xr-x 85 user user 4096 2012-03-22 15:06 ..
-rwxrwxrwx  1 user user    0 2012-03-22 14:47 file1*
-rwxrwxrwx  1 user user    0 2012-03-22 14:47 file2*

```
If you try to delete file1, you will have no problems because you have write permission to the directory (see red w).
```
$ rm file1
$
```
No problems there.

But if you are not allow to write in the directory, you won't be able to delete files, even if you have file ownership and full file permissions.
```
$ chmod u-w .
$ ls -la
total 8
dr**[COLOR="Red"]-[/COLOR]**xr-xr-x  2 user user 4096 2012-03-22 15:10 .
drwxr-xr-x 85 user user 4096 2012-03-22 15:06 ..
-rwxrwxrwx  1 user user    0 2012-03-22 14:47 file2*

$ rm file2 
rm: cannot remove `file2': Permission denied

```

Does that help to understand permissions a little better?
Regards.

---

### Post by hateborne on 2012-03-22
Thank you for the reply papibe.

Yes, it does make it a bit more clear. I guess I need to figure out a way to allow users in the "www-data" group to delete their OWN files but not the other members' files. Any suggestions would be greatly appreciated.

The directory layout is:
```
drwxr-xr-x  5 www-data www-data   4096 2012-03-22 13:39 .
drwxr-xr-x 12 root     root       4096 2012-03-22 15:35 ..
drwxr-xr-x  2 www-data www-data   4096 2012-03-22 13:25 folder1
drwxr-xr-x  5 www-data www-data   4096 2012-03-22 13:28 folder2
-rwxr-xr-x  1 www-data www-data 140029 2012-03-22 13:22 index.php
drwxr-xr-x  2 www-data www-data   4096 2012-03-22 13:26 misc
-rwxr-xr-x  1 hateborne www-data     18 2012-03-22 13:39 rootfile.txt
```The first immediate thing I noticed was the difference in "." and "..", but I cannot say what exactly that means. When attempting to remove (rootfile.txt), it fails. 

If I change from 755 to 766 flag, the user would be able to delete the other group members' files. (Or would a 766 flag on directory and 755 flag on files work?)

Thanks Again,
-Hate

---

### Post by papibe on 2012-03-22
> **hateborne said:**
> The first immediate thing I noticed was the difference in "." and "..", but I cannot say what exactly that means.
'.' represents the current directory.
'..' is the parent directory.

As for your main concern, I would take the same approach that the OS takes for the /home directory:[LIST]
[*]Create subdirectories for each user.
[*]Each directory will be owned by the user, so he/she not only can create files, but delete them too.
[*]For extra security I would create the directories as 700, so just the proper user can see, write and delete only his/her own files.
[/LIST]
Just some thoughts.
Regards.

---

### Post by redmk2 on 2012-03-22
You can use a common directory and still stop one user from deleting other users data.  The /tmp directory is setup this way.  See ```
$ ls -lh /|grep tmp
drwxrwxrw**[COLOR="Red"]t[/COLOR]**  14 root  root     4.0K 2012-03-22 14:54 tmp

```

In the direcrory is this```
drwxr-xr-x 2 red red 4.0K 2012-03-22 13:58 hsperfdata_bruce
drwx------ 2 red red 4.0K 2012-03-22 13:58 icedteaplugin-bruce
drwx------ 2 red red 4.0K 2012-03-22 08:43 keyring-8UrAEI

``` 

The red **[COLOR="Red"]t[/COLOR]** is the sticky bit set on the directory /tmp.  As all users have access, but no common group the sticky bit will only allow the owner of the file to delete the file. See [**_[COLOR="Blue"]here[/COLOR]_**]("http://unix.stackexchange.com/questions/23063/sticky-bit-vs-setgid-for-facilitating-shared-write-access") and [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid").

One other thought:  The directories use the eXecute bit to provide access or traversal to subdirectories.  If you want users to be able to decend into lower directories you need to set the execute bit (i.e. 1 as in 7 or 5 or 1 on the directory chmod).

---

### Post by hateborne on 2012-03-22
Excellent, thank you both for the answers!

Marking this as solved now.


-Hate

---

