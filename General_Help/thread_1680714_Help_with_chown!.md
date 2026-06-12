---
title: "Help with chown!"
date: 2011-02-03
forum: General Help
---

### Post by akemzo on 2011-02-03
I need to gain full access to a folder on my desktop, pls teach me how to CHOWN this folder (i know how to use chown in root directory but can't in desktop)..........



root@ubuntu:~# chown -R akemzo:akemzo /Desktop/x264
chown: cannot access `/Desktop/x264': No such file or directory
root@ubuntu:~# cd Desktop
root@ubuntu:~/Desktop# chown -R akemzo:akemzo /x264
chown: cannot access `/x264': No such file or directory

---

### Post by kanishkdudeja on 2011-02-03
```
chown -R akemzo:akemzo /home/akemzo/Desktop/x264 
```

---

### Post by beta0x64 on 2011-02-03
The reason that it was not working for you is because the path to the directory was incorrect.

/ is called the root directory. /Desktop would mean a folder in your root directory. /home is a valid directory with all the folders for each user, for example you. /home/akemzo/Desktop would be your Desktop!

Next time, if you know that you are in the akemzo directory, you should just write Desktop/x264 not /Desktop/x264. Alternatively you could write ./Desktop/x264. The . means the currently directory. .. means the parent directory (the one containing the one you are in. In this case, home.)

---

### Post by akemzo on 2011-02-03
Thanks so much for you help :) , pardon if i ask again, what would be the path to the folder on the desktop? the folder contains an install ffmpeg and i wanna use a program to access it.

---

### Post by nothingspecial on 2011-02-03
```
/home/$USER/Desktop/x264
```

or ```
~/Desktop/x264
```

or ```
/home/akemzo/Desktop/x264
```

They all mean the same thing.

---

