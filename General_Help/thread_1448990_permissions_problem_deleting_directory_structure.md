---
title: "permissions problem deleting directory structure"
date: 2010-04-07
forum: General Help
---

### Post by drreed on 2010-04-07
I've recently installed xubuntu 9.10 and when I try to delete a folder with many sub-folders, this is what happens:

dav@dav-desktop:~/Downloads$ ls -l
total 1266644
-rw-r--r--  1 dav  dav  243161797 2010-04-06 20:06 2010_01_16_PlatinumArtsSandbox2.5Multiplatform.zip
drwxr-xr-x  2 dav  dav       4096 2010-04-05 12:01 attrition
-rw-r--r--  1 dav  dav       1464 2010-04-05 11:45 consent.tgz
drwxr-xr-x  5 dav  dav       4096 2010-04-06 07:24 Game Editor
-rw-r--r--  1 dav  dav    8290678 2010-04-06 07:20 gameEditor.zip
drwxr-xr-x  9 root root      4096 2010-01-26 17:56 javafx-sdk1.2
-rwxr-xr-x  1 dav  dav   32127420 2010-04-06 23:22 javafx_sdk-1_2_3-linux-i586.sh
-rw-r--r--  1 dav  dav   80366029 2010-04-06 20:45 jdk-6u19-linux-i586-rpm.bin
-rw-r--r--  1 dav  dav    1292621 2010-04-06 20:18 lgm16b3.jar
-rw-r--r--  1 dav  dav      58222 2010-04-06 17:30 MadSwatter-2009082119.xpi
drwxr-xr-x 10 dav  dav       4096 2010-04-05 21:10 Nexuiz
-rw-r--r--  1 dav  dav  931253731 2010-04-05 20:50 nexuiz-252.zip
-rw-r--r--  1 dav  dav     140008 2010-04-03 12:32 PyNet.pdf
-rwxrwxrwx  1 dav  dav        956 2010-04-05 11:49 ros.sh
-rw-r--r--  1 dav  dav      43044 2010-04-02 16:44 wrath.jpg
-rw-r--r--  1 dav  dav     252420 2010-04-05 11:46 zipcode.tgz
dav@dav-desktop:~/Downloads$ sudo rmdir javafx-sdk1.2
rmdir: failed to remove `javafx-sdk1.2': Directory not empty
dav@dav-desktop:~/Downloads$ sudo rm javafx-sdk1.2
rm: cannot remove `javafx-sdk1.2': Is a directory
dav@dav-desktop:~/Downloads$ cd javafx-sdk1.2
dav@dav-desktop:~/Downloads/javafx-sdk1.2$ rm *
rm: cannot remove `bin': Is a directory
rm: remove write-protected regular file `COPYRIGHT.html'? sudo rm *
rm: cannot remove `docs': Is a directory
rm: cannot remove `emulator': Is a directory
rm: remove write-protected regular file `invoice.properties'? y
rm: cannot remove `invoice.properties': Permission denied
rm: cannot remove `lib': Is a directory
rm: remove write-protected regular file `LICENSE.txt'? y
rm: cannot remove `LICENSE.txt': Permission denied
rm: cannot remove `profiles': Is a directory
rm: remove write-protected regular file `README.html'? y
rm: cannot remove `README.html': Permission denied
rm: cannot remove `samples': Is a directory
rm: cannot remove `servicetag': Is a directory
rm: remove write-protected regular file `src.zip'? y
rm: cannot remove `src.zip': Permission denied
rm: remove write-protected regular file `THIRDPARTYLICENSEREADME.txt'? y
rm: cannot remove `THIRDPARTYLICENSEREADME.txt': Permission denied
rm: remove write-protected regular file `timestamp'? y
rm: cannot remove `timestamp': Permission denied
dav@dav-desktop:~/Downloads/javafx-sdk1.2$ ls -l
total 1344
drwxr-xr-x  2 root root    4096 2010-01-15 16:50 bin
-rw-r--r--  1 root root    5161 2010-01-26 16:10 COPYRIGHT.html
drwxr-xr-x  3 root root    4096 2010-01-15 16:52 docs
drwxr-xr-x  3 root root    4096 2010-01-26 17:56 emulator
-rw-r--r--  1 root root    5517 2010-01-15 16:55 invoice.properties
drwxr-xr-x  5 root root    4096 2010-01-26 17:56 lib
-rw-r--r--  1 root root   14474 2010-01-26 16:10 LICENSE.txt
drwxr-xr-x  2 root root    4096 2010-01-26 17:56 profiles
-rw-r--r--  1 root root   13828 2010-01-15 16:51 README.html
drwxr-xr-x 13 root root    4096 2010-01-26 17:56 samples
drwxr-xr-x  2 root root    4096 2010-01-26 17:56 servicetag
-rw-r--r--  1 root root 1198156 2010-01-15 16:50 src.zip
-rw-r--r--  1 root root   90992 2010-01-15 16:51 THIRDPARTYLICENSEREADME.txt
-rw-r--r--  1 root root      92 2010-01-15 16:49 timestamp
dav@dav-desktop:~/Downloads/javafx-sdk1.2$ su
Password: 
su: Authentication failure
dav@dav-desktop:~/Downloads/javafx-sdk1.2$ 

This is worse than anything I've ever encountered with Windows.

sudo doesn't let me, su doesn't work. Why the confirmation messages? To paraphrase (Ritchie?): "UNIX is an operating systems that allows skilled people to do powerful things. Windows is an OS that prevents unskilled people from doing stupid things"

I know Linux is not UNIX, but really . . .

I must not be finished configuring this install or something. How do I delete this directory structure without manually traversing it and confirming every deletion?

I understand not logging in as root, sudo (while annoying,) is something I have to accept with Ubuntu, but why doesn't it work? 

Maybe it's the rm command, maybe i have to use an option to tell it I really want to delete something? I don't see that in the man page.:confused:

---

### Post by makingtheswitch on 2010-04-07
```
sudo rm -r /the/directory/you/want/gone/
```You have to use the "-r" to state that you wish to apply the "rm" recursively before it will remove a directory -and- its contents.

And you have to pre-fix the command with "sudo" to elevate your current permissions to allow you to remove files that you do not have permission to remove normally.

---

### Post by sisco311 on 2010-04-07
> **drreed said:**
> 
Maybe it's the rm command, maybe i have to use an option to tell it I really want to delete something? I don't see that in the man page.:confused:

Yep, it's the rm command. You have to use the -r option to remove directories:
```
rm -r path/to/dir
```

```
man rm | less +/"By default, rm does not remove directories."
```
;)

---

### Post by drreed on 2010-04-07
> **sisco311 said:**
> Yep, it's the rm command. You have to use the -r option to remove directories:
```
rm -r path/to/dir
``````
man rm | less +/"By default, rm does not remove directories."
```;)

Lol - thanks!

---

### Post by sisco311 on 2010-04-07
You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

---

