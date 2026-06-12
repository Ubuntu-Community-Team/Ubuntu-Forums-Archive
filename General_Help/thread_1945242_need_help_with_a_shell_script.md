---
title: "need help with a shell script"
date: 2012-03-22
forum: General Help
---

### Post by 3djake on 2012-03-22
Hi all

What I am trying to do is launch a shell script with a shell script (weird I know).

The shell script needs to be launched in the terminal and the terminal needs to stay open for it to work, also I want to know how to stop the shell script I am trying to launch for asking for a password every single time

```

cd /home/usr/.program
./script.sh
```

or I could just create a desktop entry
```

[Desktop Entry]
Name=Program
Exec=sh -c "cd cd /home/usr/.program; ./script.sh"
Terminal=true
```

The problem is that the terminal will not stay open and does not work proper as a executable, also I do not want it to ask for a password.

Just trying to make this useful shell script as easy as possible for my mother to use as I do not want her to have to learn how to use the terminal

Thanks

---

### Post by lechien73 on 2012-03-22
Hi,

The first thing I would do is launch it with the directory path, rather than using "cd", so:

```
/home/usr/.program/script.sh
```

Also make sure it the executable bit is set:

```
chmod +x /home/usr/.program/script.sh
```

If the script contains "sudo" commands, then it will ask for a password. To stop this, you can add the script.sh to the /etc/sudoers file (more info here: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)).

There is another way as well, which involves storing the password as plaintext; however you'd want to make sure it was on a non-public computer. Also you'd have to update the script whenever the password was changed. See this thread for more info: [http://ubuntuforums.org/showthread.php?t=1935874](http://ubuntuforums.org/showthread.php?t=1935874)

---

### Post by papibe on 2012-03-22
Hi 3djake.

If you want to see it run it on a terminal, I think this may work:
```
xfce4-terminal --hold --working-directory=/home/usr/.program -x /home/usr/.program/script.sh

```
Hope that helps.
Regards.

---

### Post by 3djake on 2012-03-22
Thanks guys, this should work.
I will try these out later on.

In regards to the no password

So basically all I need to do is

```

sudo visudo

```
and the add this to the sudoers file
```

myuser ALL = (root) NOPASSWD: /home/usr/.program/script.sh

```
is this correct?

Thanks

---

### Post by 3djake on 2012-03-22
> **papibe said:**
> Hi 3djake.

If you want to see it run it on a terminal, I think this may work:
```
xfce4-terminal --hold --working-directory=/home/usr/.program -x /home/usr/.program/script.sh

```
Hope that helps.
Regards.

in regards to this, I get an error [Unable to execute child process "/home/usr/.program/script.sh" (No such File or Directory)]

I have also tried the following
```
xfce4-terminal --hold --working-directory=/home/usr/.program --command=/home/usr/.program/script.sh

```
but I get the same error, what am I doing wrong, I know its something really simple but I have not had my usual 5 cups of coffee today.

Cheers

---

### Post by papibe on 2012-03-22
I used the same path as the one on your example.

Probably you have to replace '/home/usr/.program' with the actual path in your system.

For instance, if you username is '3djake' probably the path would be '/home/3djake/.program'

Regards.

---

### Post by 3djake on 2012-03-22
NVM one of the folders had a capital letter rofl. I just knew it was something like that

Now I just need to figure out what I need to add to sudoer

---

### Post by 3djake on 2012-03-23
so I have being trying to get the shell script to stop asking for a password by editing sudoers and I am doing something wrong.

So I added

```

User_Alias USRGRP1 = jake
Cmnd_Alias SHELLSC = /home/usr/.program/script.sh, /home/usr/Desktop/launcher.sh 

USRGRP1 ALL = (root) NOPASSWD: SHELLSC
USRGRP1 ALL = (root) NOPASSWD: /home/usr/.program/script.sh
USRGRP1 ALL = (root) NOPASSWD: /home/usr/Desktop/launcher.sh

```

it still asks me for a password and I am obviously a complete noob at this.

Thanks

---

### Post by azmyth on 2012-03-23
I believe you need to add the command using sudo in your script to the sudoers file as well.

---

