---
title: "places never open"
date: 2010-02-15
forum: General Help
---

### Post by jorgeAAE on 2010-02-15
ubuntu 9.10, Places never open, I tried all reccomendations in forum and still doesnt work.
When trid to open computer or file system or any other in lower bar appers "opening ...." but never opens and after 4 or 5 seconds disappers every thing.
I tried ls -l with next result:jorge@jorge-laptop:~$ Is -I
Is: command not found
jorge@jorge-laptop:~$ ls -l
total 32
drwxr-xr-x 2 jorge jorge 4096 2010-02-08 00:41 Desktop
drwxr-xr-x 2 jorge jorge 4096 2010-02-08 00:41 Documents
-rw-r--r-- 1 jorge jorge  357 2010-02-07 22:53 examples.desktop
drwxr-xr-x 2 jorge jorge 4096 2010-02-08 00:41 Music
drwxr-xr-x 2 jorge jorge 4096 2010-02-08 00:41 Pictures
drwxr-xr-x 2 jorge jorge 4096 2010-02-08 00:41 Public
drwxr-xr-x 2 jorge jorge 4096 2010-02-08 00:41 Templates
drwxr-xr-x 2 jorge jorge 4096 2010-02-08 00:41 Videos
jorge@jorge-laptop:~$ chmod 755 ~
I also tried nautilus with following result:jorge@jorge-laptop:~$ nautilus

(nautilus:1831): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:1831): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1831): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1831): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Illegal instruction
jorge@jorge-laptop:~$ 



 and still doesnt open anything.
PLEASE HELP
[EMAIL="jabude@hotmail.com"]jabude@hotmail.com[/EMAIL]

---

