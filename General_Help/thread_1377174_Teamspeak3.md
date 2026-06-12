---
title: "Teamspeak3"
date: 2010-01-10
forum: General Help
---

### Post by Raiju on 2010-01-10
Installing Teamspeak 3. the '.run' extracts to a folder, so i just thought i had make a link to the file to run teamspeak. But i get a error when using the command anywhere outside of the teamspeak folder.
```
eric@raiju-Desktop:~$ sudo ln -s /home/eric/TeamSpeak3-Client-linux_amd64/ts3client_linux_amd64 /usr/local/bin/teamspeak3
eric@raiju-Desktop:~$ teamspeak3
teamspeak3: error while loading shared libraries: libfmodex64.so: cannot open shared object file: No such file or directory
```

---

### Post by Raiju on 2010-01-10
bump!@

---

### Post by Tahakki on 2010-01-10
Looks like you're missing a library - FMod Ex.

[Try this.]("http://www.fmod.org/index.php/release/version/fmodapi42806linux64.tar.gz")

---

### Post by Raiju on 2010-01-10
:/ you sure? if i navigate to the folder using nautilus or terminal and launch it, it runs no problem. but when i make a link to it or launcher i get that error

---

### Post by Tahakki on 2010-01-10
Oh right. Weird.

---

### Post by ALFA_1024 on 2010-01-10
I think you have to write a script wich cd first into the folder where your ts installation is loacated. then you can start ts.  Something like: echo 'cd /home/name/TeamSpeak3-Client-linux_amd64 ./ts3client_linux_amd64'>start_ts.sh chmod +x start_ts.sh ln ...  should do.  then you can link to this file  worked for me on fedora ...

---

### Post by Raiju on 2010-01-10
Didn't work for me. :/
start_ts.sh contains
```
cd /home/eric/TeamSpeak3-Client-linux_amd64 ./ts3client_linux_amd64
```
i did do chmod +x 
I just get another prompt and TS doesnt start

---

### Post by Tahakki on 2010-01-11
Try just running '/home/eric/TeamSpeak3-Client-linux_amd64/ts3client_linux_amd64'.

---

### Post by Raiju on 2010-01-11
eric@raiju-Desktop:~$ /home/eric/TeamSpeak3-Client-linux_amd64/ts3client_linux_amd64
/home/eric/TeamSpeak3-Client-linux_amd64/ts3client_linux_amd64: error while loading shared libraries: libfmodex64.so: cannot open shared object file: No such file or directory

:{

---

### Post by Unitas on 2010-02-03
From here: [http://forum.teamspeak.com/showthread.php?t=50901](http://forum.teamspeak.com/showthread.php?t=50901)

Open TS with the ts3client_runscript.sh file, not the ts3client_linux_amd64 file. Opens right up.

Be sure to chmod +x it first, it wasn't +x after the update for me.

---

### Post by supermorph on 2011-03-25
> **Unitas said:**
> From here: [http://forum.teamspeak.com/showthread.php?t=50901](http://forum.teamspeak.com/showthread.php?t=50901)

Open TS with the ts3client_runscript.sh file, not the ts3client_linux_amd64 file. Opens right up.

Be sure to chmod +x it first, it wasn't +x after the update for me.

i checked both the teamspeak-server & client install from the repo
i have found it does things direct, without the start script

while you are correct, would an actuall install of the application for that missing library fix it? e.g then they might be able to run direct

 i am aware that those applications i mension are version two.

heres how i setup myne for a sort of idea what i mean :-)

[http://ubuntuforums.org/showthread.php?p=10593783#post10593783](http://ubuntuforums.org/showthread.php?p=10593783#post10593783)

---

