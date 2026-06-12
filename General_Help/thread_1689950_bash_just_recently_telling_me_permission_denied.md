---
title: "bash just recently telling me permission denied"
date: 2011-02-17
forum: General Help
---

### Post by S_p_or_t_o on 2011-02-17
ok, so i have steam dedicated servers app on a hard drive separate from the file system

running 10.10 maverick x64.

everything was great until i tried running my update bash today

```
#!/bin/bash
#mount /dev/by-label/steam /media/steam
#cd /media/steam/steam

./steam -command update -game left4dead -dir .
./steam -command update -game left4dead2 -dir .
./steam -command update -game zps -dir .
./steam -command update -game orangebox -dir .
./steam -command update -game tf -dir .
./steam -command update -game dods -dir .
./steam -command update -game alienswarm -dir .
./steam -command update -game "Counter-Strike Source" -dir .
./steam -command update -game "Counter-Strike Source" -dir gungame/
./steam -command update -game "Counter-Strike Source" -dir zombiemod/

```it tells me
```
eat@joes:/media/steam/steam$ ./update.bin
bash: ./update.bin: Permission denied
eat@joes:/media/steam/steam$
```that's when i discovered goofy permission stuff not taking effect (edited to illustrate)
```
eat@joes:/media/steam/steam$ ls -al
-rw-r--r--  1 eat eat     589 2011-02-17 14:03 update.bin
eat@joes:/media/steam/steam$ chmod -v +x update.bin 
mode of `update.bin' changed to 0755 (rwxr-xr-x)
eat@joes:/media/steam/steam$ chmod -v 777 update.bin 
mode of `update.bin' changed to 0777 (rwxrwxrwx)
eat@joes:/media/steam/steam$ ls -al
-rw-r--r--  1 eat eat     589 2011-02-17 14:03 update.bin
eat@joes:/media/steam/steam$ 

```i tried right clicking on the file and selecting "allow executing file as program". the check box unselects itself as soon as i left off the mouse button.

i ran this and just the normal ./steam both in sudo once to see, but it gets the same error

i chown the file and then the entire directory to no avail

---

### Post by DaithiF on 2011-02-17
your drive is being automounted with exec permissions turned off (its a window fat file system I'm guessing).   this is a recent & rather frustrating change.

my favourite solution is the answer here:
[http://askubuntu.com/questions/17540/how-do-i-set-executable-permissions-on-a-removable-drive](http://askubuntu.com/questions/17540/how-do-i-set-executable-permissions-on-a-removable-drive)

---

### Post by S_p_or_t_o on 2011-02-17
thanks

---

