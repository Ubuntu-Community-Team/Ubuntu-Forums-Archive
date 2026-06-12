---
title: "List open files"
date: 2010-09-10
forum: General Help
---

### Post by jimmys_ on 2010-09-10
Hello.

Is there a way I can list all open files by a user? I found the command lsof but it the command lists too many files some of which are not used directly by the user. What I want is to view only the files that are currently open like text files, documents, pictures etc and not other system files.

Thank you

---

### Post by ubulal on 2010-09-10
```
lsof -Fn -u USERNAME | sort  | uniq | grep /home
```

may be a start...

---

### Post by jimmys_ on 2010-09-10
It narrows down the results but still shows too many unwanted results and what if the file is not located in the home directory?
Thanks though ;)

---

### Post by ubulal on 2010-09-10
AFAIK there is no way to only show files that the user "double clicked in the filemanager" or something like that.  You have to grep lsof output.  You could grep for all interesting file extensions for example:

```

lsof -Fn -u username | sort | uniq | grep -E "\.(txt|jpg|mp3)$"

```

---

### Post by jimmys_ on 2010-09-10
I thought that it wouldn't be that easy. I think the way you are proposing will be fine. But I can't make it work yet. For example I have a txt and jpg file opened but can't find it with the lsof command. And using the parameters you proposed, shows nothing. Do I do something wrong?

---

### Post by ubulal on 2010-09-10
Some (most?) apps don't keep the file descriptor open all the time.  They load the file content into memory and then close the descriptor, so lsof won't list it anymore.  No way to circumvent that.  If you want to know exactly what files your users access, you'd have to put everything on some kind of fileserver and use it's logging capabilities.

But you can see the file name arguments of some apps in ps(1) output...

---

### Post by jimmys_ on 2010-09-10
Thanks for your help.
Actually I'm trying to develop a program that will be executed locally and that will extract information for the files that a user opens and also if that is a text file, it will extract it's contents.

---

### Post by nagaprathyush on 2010-09-10
Wow, you guys are awesome!!! :D I have kept an mp3(syndic calls) and txt(plane) file open and got the following results......

**$ lsof -F -u trollan | sort | uniq | grep -E "\.(txt|mp3)$"**
n/home/trollan/.thunderbird/xkxw9z6r.default/zindus/log/logfile.txt
n/host/dc downloads/05 Syndic Calls.mp3

**$ lsof -n -u trollan | sort | uniq | grep -E "\.(txt|mp3)$"**
thunderbi 3540 trollan   43w      REG        7,0    46266      24817 /home/trollan/.thunderbird/xkxw9z6r.default/zindus/log/logfile.txt
thunderbi 3540 trollan   44w      REG        7,0    46266      24817 /home/trollan/.thunderbird/xkxw9z6r.default/zindus/log/logfile.txt
thunderbi 3540 trollan   45w      REG        7,0    46266      24817 /home/trollan/.thunderbird/xkxw9z6r.default/zindus/log/logfile.txt
thunderbi 3540 trollan   46w      REG        7,0    46266      24817 /home/trollan/.thunderbird/xkxw9z6r.default/zindus/log/logfile.txt
thunderbi 3540 trollan   74u      REG        7,0    46266      24817 /home/trollan/.thunderbird/xkxw9z6r.default/zindus/log/logfile.txt
vlc       4565 trollan   24r      REG        8,6 17262484       2568 /host/dc downloads/05 Syndic Calls.mp3
[B]
$ lsof -Fn -u trollan | sort | uniq | grep -E "\.(txt|mp3)$"[/B]
n/home/trollan/.thunderbird/xkxw9z6r.default/zindus/log/logfile.txt
n/host/dc downloads/05 Syndic Calls.mp3
[B]
$ ps aux | grep -E "\.(txt|mp3)$"[/B]
trollan    4565  2.0  1.5 151768 32296 ?        Sl   15:14   0:28 vlc /host/dc downloads/05 Syndic Calls.mp3
trollan    4599  0.0  0.9  65552 18608 ?        S    15:15   0:00 gedit /host/dc downloads/Standard Jokes/plane.txt

Can someone explain the significance of -F argument in lsof ? Read the man page, but that was somewhat difficult to comprehend for me ......

---

### Post by ubulal on 2010-09-10
> **jimmys_ said:**
> Thanks for your help.
Actually I'm trying to develop a program that will be executed locally and that will extract information for the files that a user opens and also if that is a text file, it will extract it's contents.

man inotify
That should provide everything you need.  Once the daemon has the path name of a newly opened file, checking the file type and reading it's content should be a peace of cake.  Can't help you with the inotify specifics though, as I've never programmed with it myself.  Would have to study man pages, too.

> **nagaprathyush said:**
> 
Can someone explain the significance of -F argument in lsof ? Read the man page, but that was somewhat difficult to comprehend for me ......

-Fn makes lsof print only the path **n**ame of the open files and leave out all the other things it normally prints (command name, PID, user, etc.) but which we're not interested in.

---

### Post by nagaprathyush on 2010-09-10
Ohhkay, thanks for the reply Mr.Ubulal ;) .....

---

### Post by jimmys_ on 2010-09-10
> **ubulal said:**
> man inotify
That should provide everything you need.  Once the daemon has the path name of a newly opened file, checking the file type and reading it's content should be a peace of cake.  Can't help you with the inotify specifics though, as I've never programmed with it myself.  Would have to study man pages, too.




Yes I think you are right. I have studied inotify in the past but haven't tested it and I totally forgot about it. I'll give it a try. Although I'll probably have some problems since it requires to explicitly declare the directory to watch.

---

### Post by ubulal on 2010-09-10
> **jimmys_ said:**
> Yes I think you are right. I have studied inotify in the past but haven't tested it and I totally forgot about it. I'll give it a try. Although I'll probably have some problems since it requires to explicitly declare the directory to watch.
 
Yeah, if inotify doesn't watch directories recursively, than that's up to your app. Happy hacking! :)

---

### Post by jimmys_ on 2010-09-28
I have experimented with inotify but I have noticed some problems. After I establish a watch to a directory, when I open the directory, the program notifies that some of the files containing were opened. Probably this doesn't have to do with inotify but with the OS which also opens the file descriptors when accessing the directory.

Trying to watch multiple directories, I kept one fd variable and used several wd. It seems though that doing actions on the second directory, inotify notifies about the 1st one. I don't know if it's clear what I'm saying but has anyone tried to use it for multiple directories or recursively and encountered any problems?

---

