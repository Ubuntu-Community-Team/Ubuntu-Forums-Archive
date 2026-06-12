---
title: "PyLotRO cant get past the black screen"
date: 2010-04-14
forum: General Help
---

### Post by purdurabo on 2010-04-14
i am tring to run ddo on my ubuntu system,right? well most of the how-to that i used came from 
 
[http://forums.ddo.com/showthread.php?t=212618&highlight=ddo+run+ubuntu](http://forums.ddo.com/showthread.php?t=212618&highlight=ddo+run+ubuntu) 
 
and 
 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17785](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17785) 
 
i got every thing installed, now here is the problem. when i hit login all i get is ***FINISHED*** on my out-put window and a full black screen. 
i am running ubuntu 9.1. the news box and the server info both come up on the pylotro. i did a patch and the game updated. still a black screen. so i patched again, and this is what i got: 
 
Connecting to patch.ddo.com:80 
 
 
 
Checking files... 
 
files to patch: 1 bytes to download: 138504 
 
Patching files: 
 
 
 
Downloading patchclient.dll................................................ 
 
 
 
........................................ 
 
 
 
Decrypting.................................. 
 
File in use. It will be self patched. 
 
 
 
Self patch required. Program will restart. 
 
 
 
Connecting to patch.ddo.com:80 
 
 
 
Checking files... 
 
files to patch: 1 bytes to download: 0 
 
Patching files: 
 
Downloading patchclient.dllFile in use. It will be self patched. 
 
 
 
Self patch required. Program will restart. 
 
 
 
*** Finished *** 
 
so i then tried to login again, and guess what? still a big black screen!!!!!!! 
could some one please explain this to me, and how to fix it?????

---

### Post by Thonyv on 2010-08-18
I am having the same problem.

When I run pylotro in terminal after I close out the window it gives 'Segmentation fault'
In my kern.log I also get these errors individually at different times when it tries to start the game
'kernel: [  403.156471] pylotro[2222]: segfault at 0 ip (null) sp bf8fa3bc error 4 in libm-2.11.1.so[110000+24000]'
'kernel: [ 3645.981018] pylotro[2994]: segfault at 0 ip (null) sp bfbe0b8c error 4 in libc-2.11.1.so[110000+153000]'
'kernel: [ 6072.683889] pylotro[3323]: segfault at 0 ip (null) sp bff54c1c error 4 in libssl.so.0.9.8[110000+42000]'
'kernel: [ 7143.397986] pylotro[3581]: segfault at 0 ip (null) sp bf9f41fc error 4 in libcrypto.so.0.9.8[110000+138000]'

When the screen goes black it tries to reset my monitor's resolution to 1920x1080, but the monitor only supports 1600x900. After the black screen crashes it leaves my resolution at 960x600.

I am not sure where the preferences are stored but the DDO installation I copied was from windows and should have already been set to run at 1280x720. The exact same installation works fine on another comp I have that is running the same os/wine verion (Ubuntu 10.04/Wine 1.1.42).

Any insight is greatly appreciated.

EDIT: After playing around and comparing settings from both machines it appears that these errors occur even when the game run properly. Found the Userpreferences.ini file and turned off fullscreen mode so at least it doesn't reset my desktop resolution when the game fails to load. However, it is still opening the game window at an unspecified resolution and crashes as a black screen seconds after opening. I can't seem to find anything in any log files that will give me a better clue as to what is happening.

---

