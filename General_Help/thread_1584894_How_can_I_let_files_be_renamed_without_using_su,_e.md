---
title: "How can I let files be renamed without using su, etc.?"
date: 2010-09-29
forum: General Help
---

### Post by seaworthy4life on 2010-09-29
I have a program that is trying to install an update, and in the process it tries to rename a file, but is not allowed to do that.  I thought that it should be allowed regardless, since the program is installed in the Home folder, but it is not allowing name changes without root privileges.  I am thinking I either need to turn off this option somewhere or input a command like sudo which will let me have that privilege for 15 minutes or something like that, but that doesn't seem to be working.

---

### Post by snowpine on 2010-09-29
Please be specific. What is the name of the program you're trying to update, what is the path and name of the file it's trying to change, and what is the specific error message?

Generally speaking, in Ubuntu, we update all of our programs at once through the Update Manager, which does indeed need to be run with "sudo" privileges.

---

### Post by seaworthy4life on 2010-09-30
OK.  The program I am trying to update is called Teamspeak, a volp type of program for gamers.  The current version is not carried in Synaptic and it is far different than the former version.  It has its own internal updating system within the program itself.  I am getting this hang when it tries to rename old files.  

Starting file updates
add/replace CHANGELOG._z_
add/replace plugins/libclientquery_plugin.so._z_
Could not rename '/home/justin/TeamSpeak3-Client-linux_x86/CHANGELOG' to '/home/justin/TeamSpeak3-Client-linux_x86/_old_CHANGELOG'
Could not rename '/home/justin/TeamSpeak3-Client-linux_x86/plugins/libclientquery_plugin.so' to '/home/justin/TeamSpeak3-Client-linux_x86/plugins/_old_libclientquery_plugin.so'
rolling back file updates
Update cancelled

This seemed odd because I thought I remembered that renaming a file in the Home directory did not require root privileges, but of course I could be wrong, but that is how it is on my machine.  Maybe Ubuntu is different on this.  I just don't know how to apply the command for this type of application.  Maybe there is simply a setting that is off.  I have not been able to locate it.  I could not find any threads with an issue similar to this.  Thank you for your help.

---

### Post by waperboy on 2010-09-30
Sounds like either the file in question is locked because it's in use, or you happened to be root when installing the software?

Do a

  ls -l

in the directory

 /home/justin/TeamSpeak3-Client-linux_x86/plugins

(and the parent directories as well), see who owns the files, and make sure that the software is not running when you try to update it.

---

### Post by seaworthy4life on 2010-10-01
Let me get something clear.  Does renaming a file normally require root privileges?  Probably not in the Home directory, but I was just wondering. 

The software has its own internal update function.  It must run when it is updating because it is light years ahead of the version in Synaptic.  It won't let the program rename the file because on my system, renaming files requires root permissions, even when the file is in the Home directory.  I don't know why and I can't figure out how to change that setting if that is even possible.  The only other option I can think of is to find out a command to use in a terminal before updating, some version of sudo or whatever, which will allow the program to rename the file. 

FYI Here are permissions on the files and I know for sure that the program was not installed as root.  Does this mean for some reason I don't have write permission over them if the group does not?  (Do I need to fix that?)

-rwxr-xr-x 1 root root 856543 2010-09-21 03:04 libclientquery_plugin.so
-rw-r--r-- 1 root root    72918 2010-09-21 03:04 CHANGELOG

---

### Post by sisco311 on 2010-10-01
> **seaworthy4life said:**
> Let me get something clear.  Does renaming a file normally require root privileges?  Probably not in the Home directory, but I was just wondering. 


In order to rename a file, you need write permission on its parent directory and execute (a.k.a. search) permissions on its parent directories back to root (/).

[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

> **seaworthy4life said:**
> 
FYI Here are permissions on the files and I know for sure that the program was not installed as root.  Does this mean for some reason I don't have write permission over them if the group does not?  (Do I need to fix that?)

-rwxr-xr-x 1 root root 856543 2010-09-21 03:04 libclientquery_plugin.so
-rw-r--r-- 1 root root    72918 2010-09-21 03:04 CHANGELOG

The files in question (and probably all files in TeamSpeak3-Client-linux_x86) are owned by root, so you either installed the application as root or run it as root at least once. 

Anyway, to fix your issue, simply change the owner of the TeamSpeak directory (recursively) from root to justin:
```
sudo chown -R $USER: ~/TeamSpeak3-Client-linux_x86
```

---

