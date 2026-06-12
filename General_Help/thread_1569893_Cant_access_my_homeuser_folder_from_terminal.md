---
title: "Cant access my /home/user/ folder from terminal"
date: 2010-09-07
forum: General Help
---

### Post by octohedra on 2010-09-07
When i try to acces my /home/user/ 
cd /home/user
No such file or directory

Whats wrong? I can see it in "places" and execute/write/read it.. so its weird..

):P

---

### Post by eev2 on 2010-09-07
How about 
cd ~

---

### Post by octohedra on 2010-09-07
now i tried this:
user@machine:~$ sudo wine "/home/user/.wine/drive_c/warcraft iii/w3l.exe" -opengl
[sudo] password for user: 
wine: /home/user/.wine is not owned by you :o


??? I typed my root password and it says its not owned by me anyways?
What can i do?

---

### Post by eev2 on 2010-09-07
What is the output of 
ls -ld ~

---

### Post by WorMzy on 2010-09-07
Woah! Don't ever use wine with sudo, it's completely unnecessary and definitely not a good idea.

As for your home folder problem, can you run the following command in a terminal:
```
ls -l /home
```

Post the output here, embedded in [CODE[COLOR="Black"]][/COLOR][/CODE] tags.

---

### Post by octohedra on 2010-09-07
> **eev2 said:**
> What is the output of 
ls -ld ~
```
drwxrwxrwx 35 user user 4096 2010-09-07 12:53 /home/user
```> Woah! Don't ever use wine with sudo, it's completely unnecessary and definitely not a good idea.

As for your home folder problem, can you run the following command in a terminal:
     Code:
     ls -l /home 
Post the output here, embedded in [CODE[COLOR=Black]][/COLOR][/CODE] tags.     ```
total 4
drwxrwxrwx 35 user user  4096 2010-09-07 12:53 user

```

---

### Post by octohedra on 2010-09-07
i just wanted to get to my wine folder, and run files in there from the terminal... but i cant get there, it says "No such file or directory"..

---

### Post by eev2 on 2010-09-07
Try
sudo chown -R user:user ~

and then try to run your wine command without the sudo in the front.

---

### Post by octohedra on 2010-09-07
Thanks for the fast answers, i could manage to get to the c_drive folder inside /.wine but i cant get to my "Warcraft III" folder,

```
user@machine:~/.wine/drive_c$ dir
III        users              windows
Program\ Files    Warcraft\ III         
user@machine:~/.wine/drive_c$ cd warcraft\ III
bash: cd: warcraft III: No such file or directory
user@machine:~/.wine/drive_c$ cd III
bash: cd: III: No such file or directory
user@machine:~/.wine/drive_c$ cd warcraft\III
bash: cd: warcraftIII: No such file or directory

```

Edit: i just notice i wasnt typing exactly the same name, with capitals. I could manage to get to the folder.

Thanks!

---

### Post by octohedra on 2010-09-07
> **eev2 said:**
> Try
sudo chown -R user:user ~

and then try to run your wine command without the sudo in the front.

```
user@machine:~/.wine/drive_c$ sudo chown -R user:user ~
[sudo] password for user: 
chown: cannot access `/home/user/.gvfs': Permission denied
```

:o

---

### Post by octohedra on 2010-09-07
The game is working smooooooooooth!! 

Thanks !!!!!!! :popcorn:

---

