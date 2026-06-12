---
title: "firefox"
date: 2009-12-12
forum: General Help
---

### Post by hotshot247 on 2009-12-12
when i go to mediafire.com to upload a file, firefox 3.5 crashes everytime. is their something i can do about that or do i have to wait for a patch?

---

### Post by serpantman on 2009-12-12
Try making sure nothing is using the file your uploading. Go. 

fuser -m /complete/path/to/file

look for a number

ps -e | grep thatnumber

look for name of a process with a PID next to it.

kill the process PID that is using the file. With 

kill pid#

---

### Post by hotshot247 on 2009-12-12
no, the file that i am trying to upload is not in use but i tried what you said anyways just to make sure. i also tried to upload other files and all of them did exactly the same thing. the screen dims when i try to upload it letting me know that firefox is crashing for some reason.

---

### Post by serpantman on 2009-12-12
If firefox requires any sort of plugin for mediafire you should try updating that.

copy the plugin too.

/usr/lib/firefox/plugins/

If you can't get firefox to work maybe try another browser. Or see if media fire allows ftp uploads etc... I know you'd rather have firefox working but i don't have any other ideas.

---

### Post by 3rdalbum on 2009-12-12
1. Make sure you are using the official Adobe Flash Player.

2. Try disabling your Firefox addons.

3. Try Google Chrome.

---

