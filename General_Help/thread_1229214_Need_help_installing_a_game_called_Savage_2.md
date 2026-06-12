---
title: "Need help installing a game called Savage 2"
date: 2009-08-01
forum: General Help
---

### Post by lyfenda on 2009-08-01
Ok i have encountered a problem while downloading a game the game is called savage 2 a tortured soul and is a linux game the problem is this when i download i go to permissions and go to allow executing files as a programme and then i creat the archive in the home area and when i go to the terminal and add this code that should start the game installer to install the game this happens 

adam@ubuntu:~$ ~$ cd ~/Desktop
bash: ~$: command not found
adam@ubuntu:~$ ~/Desktop$ Savage2Install-2.1.0.1-i686.bin.exe.tmp
bash: /home/adam/Desktop$: No such file or directory
adam@ubuntu:~$ 

and nothing happens can you please help me ask me details i need help fast thank you.

---

### Post by wojox on 2009-08-01
```
cd Desktop
```

is the command you want. No tilde.

---

### Post by ridetheteapot on 2009-08-01
> 
adam@ubuntu:~$ ~$ cd ~/Desktop
bash: ~$: command not found
adam@ubuntu:~$ ~/Desktop$ Savage2Install-2.1.0.1-i686.bin.exe.tmp
bash: /home/adam/Desktop$: No such file or directory
adam@ubuntu:~$


check the diff :
> 
adam@ubuntu:~$ cd ~/Desktop
ls -l
# is executable set? if not chmod +x Savage*.exe*
adam@ubuntu:Desktop$ ./Savage2Install-2.1.0.1-i686.bin.exe.tmp


---

### Post by linux_tech on 2009-08-01
save the savage 2 install file to the desktop, then
```

cd ~/Desktop
chmod +x Savage2Install-2.1.0.1-i686.bin
```

then install:

```
sudo ./Savage2Install-2.1.0.1-i686.bin
```

---

