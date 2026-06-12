---
title: "Trying to understand how permissions work"
date: 2012-03-05
forum: General Help
---

### Post by sfang on 2012-03-05
I'm reading about permissions, but it's getting confusing.

1) According to the various wiki and forums, the base permission is 777 for folders and 666 for files. So if I want to set a umask=002 I would end up with

Folder permissions: 775 -> owner/group have full access
File permissions: 664 -> owner/group can read and write, others can only read.

Am I getting this right?

2) Say, I want the folder permissions to be rwxrwx--- (770), meaning no one else besides owner/group can read/create files, etc.  For file permission I want rw-rw---- (660), meaning no one can execute and only owner/group can read and write. How would I set up both of these values with umask? Because for folders it would be 007 and for files, 006. Should I use dmask and fmask or am I'm needlessly complicating things?

I also would like to know why file permissions are 666 instead of 777. Is that because only the superuser can execute anything?

3) I was reading this guide to[ fstab]("http://ubuntuforums.org/showthread.php?&t=283131") and there is this bit:

> Best is to set directories with executable permissions and file with read write. To do this, use fmask and dmask (rather then umask):
dmask=027
fmask=137

With these options files are not executable (all colored green in a terminal w/ ls)I understand dmask = 027 means permission of 750, but what about fmask=137, is it a typo? Shouldn't it be 136? I mean 666 - 530 = 136.

Sorry for all these questions, but I'd like to better understand how permissions work.

---

### Post by HiImTye on 2012-03-05
[http://ubuntuforums.org/showpost.php?p=9115998&postcount=4](http://ubuntuforums.org/showpost.php?p=9115998&postcount=4)
explains about permissions

---

### Post by sfang on 2012-03-05
HiImTye, thanks for the reply.

Yes, it's one of the topics I've read. However, I'd like to clarify the points above, if possible.

---

### Post by raja.genupula on 2012-03-05
have you gone through this 

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by cortman on 2012-03-05
Honestly, I never use the numerical system for assigning partitions. Chmod also has letter tag options of

```

r- read
w- write
x- execute
```

and

```

u- user, you
g- group, a user group to which you belong
o- other, everyone besides you and your group
```

I personally find these to make much more sense and be way easier to remember than the numbers.

---

### Post by HiImTye on 2012-03-05
> **cortman said:**
> Honestly, I never use the numerical system for assigning partitions. Chmod also has letter tag options of
...
I always use chmod, it's less to remember

---

### Post by Khayyam on 2012-03-05
> **sfang said:**
> 1) [...] So if I want to set a umask=002 I would end up with:

Folder permissions: 775 -> owner/group have full access
File permissions: 664 -> owner/group can read and write, others can only read.

Am I getting this right?

With 775 'other' also has 'access' but not write. WRT 664 on files, correct. 

> **sfang said:**
> 2) Say, I want the folder permissions to be rwxrwx--- (770), meaning no one else besides owner/group can read/create files, etc.  For file permission I want rw-rw---- (660), meaning no one can execute and only owner/group can read and write. How would I set up both of these values with umask? Because for folders it would be 007 and for files, 006.

Well, no .. files, unlike directories, do not need +x in order to be accessed, and so a mask of 007 will produce files of 660.

```
% umask u=rwx,g=rwx,o=
% umask
007
% umask -S
u=rwx,g=rwx,o=
% mkdir test
% ls -ld test
drwxrwx--- 2 user group 4096 Mar  6 03:50 test/
% touch test/file.txt
% ls -l test/file.txt
-rw-rw---- 1 user group 0 Mar  6 03:51 test/file.txt
```

What generally causes the confusion is the fact that directories have the +x so that there contents can be accessed, whereas files have +x in order to be executable.

> **sfang said:**
> I also would like to know why file permissions are 666 instead of 777. Is that because only the superuser can execute anything?

0666 will be u+rw,g+rw,o+rw and 0777 will be u+rwx,g+rwx,o+rwx ... the executable flag is so that the file can be executed. As most files are not executables ugo+x doesn't need to be set. 

> **sfang said:**
> Sorry for all these questions, but I'd like to better understand how permissions work.

No problem ... I understand that it can be confusing at first.

best ... khay

---

### Post by sfang on 2012-03-05
> **raja.genupula said:**
> have you gone through this

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I've read Ubuntu's wiki and help page, Arch's wiki, linuxcommmand.org and many topics around here. :)

> **cortman said:**
> Honestly, I never use the numerical system for assigning partitions. Chmod also has letter tag options of

```

r- read
w- write
x- execute
```and

```

u- user, you
g- group, a user group to which you belong
o- other, everyone besides you and your group
```I personally find these to make much more sense and be way easier to remember than the numbers.

Pretty good sugestion. I might use letters for the time being...

> **Khayyam said:**
> 
Well, no .. files, unlike directories, do not need +x in order to be accessed, and so a mask of 007 will produce files of 660.

Ah, that was the missing link! Now I understand why in point #3 fmask is 0137. Everything makes sense now. The command umask -S is highly useful too, good to know about it.

Khayyam and everyone, a big thank you for the help! :D

---

### Post by Khayyam on 2012-03-06
> **sfang said:**
> [...]Pretty good sugestion. I might use letters for the time being...

Its much easier to get a handle on, and as umask, chmod, etc, understand this notation its just saves alot of unnecessary mental switching from numeric notation to symbolic notation.

> **sfang said:**
> Ah, that was the missing link! Now I understand why in point #3 fmask is 0137. Everything makes sense now. The command umask -S is highly useful too, good to know about it.

Ahhh .. good .. from my experience its that one point that causes people most problems. Yes, umask does 'symbolic notation' as well, though you rarely see it referred to, and as most people have a better handle on, and generally use, the symbolic notation, its a bit of a wonder why. 

> **sfang said:**
> Khayyam and everyone, a big thank you for the help!

Your welcome ... you should probably now [make this thread as [SOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

best ... khay

---

