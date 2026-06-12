---
title: "JDownloader wont write to /media/x/.. but works when i run with sudo?"
date: 2010-10-06
forum: General Help
---

### Post by fuzzylogic25 on 2010-10-06
I installed two programs recently, Vuze and JDownloader. Vuze seems to run perfectly fine and write to the /media/x directory.

However JDownloader keeps saying "cannot write to location /media/x" or something like that. Only when i run it as sudo will it write to that location. So currently thats what I have done. But how do i make it so it runs without sudo and still can write to /media/x

also, why is it that vuze has write permissions but jdownloader doesnt?

---

### Post by endotherm on 2010-10-06
what are the permissions on the folder?

I've never found a rhyme or reason for it, but some applications can work with a folder if they have access to just it, whereas other apps require access to the entire path to that folder. 

what are the permissions on /media and on x?
```

ls -al /media
ls -al /media/x

```

---

### Post by fuzzylogic25 on 2010-10-07
Here is what i get:

=================================================================

john@cmp:~$ ls -al /media
total 32
drwxr-xr-x  5 root    root     4096 2010-10-08 10:09 .
drwxr-xr-x 22 root    root     4096 2010-10-07 23:03 ..
drwx------  1 john    john     8192 2010-10-02 00:07 BACKUP2TB
drwxr-x--- 11 john root        4096 2010-10-04 01:52 DATA2TB
drwx------  1 john john       12288 2010-09-15 23:37 WIN7
john@cmp:~$ ls -al /media/DATA2TB
total 56
drwxr-x--- 11 john    root     4096 2010-10-04 01:52 .
drwxr-xr-x  5 root    root     4096 2010-10-08 10:09 ..
drwx------ 10 john    john     4096 2010-10-04 01:46 Downloads
drwx------  9 john    john     4096 2010-10-04 16:08 Important
drwx------  2 root    root    16384 2010-09-22 20:07 lost+found
drwx------  5 john    john     4096 2010-09-23 15:49 .Trash-1000


=================================================================

The folder I am getting JDownloader to write to is /media/DATA2TB/Downloads/

---

### Post by endotherm on 2010-10-08
the ownership of Data2TB is a little unusual, so lets set the owner-group to 'john'.
```
sudo chmod john:john /media/DATA2TB
```

the next thing to check is the exact file that can't be accessed. run the program as yourself from a terminal and post back the output. in this suse thread, the issue was access to a config database in the users $home.
[http://forums.opensuse.org/english/get-help-here/applications/404077-jdownloader-only-root.html](http://forums.opensuse.org/english/get-help-here/applications/404077-jdownloader-only-root.html)

---

### Post by fuzzylogic25 on 2010-10-08
this is what happens when i try that:


john@cmp:~$ sudo chmod john:john /media/DATA2TB
chmod: invalid mode: `john:john'
Try `chmod --help' for more information.

---

### Post by Jiaz on 2010-10-08
he meant chown ;) not chmod and yes , the cause of the issue are wrong folder rights

---

