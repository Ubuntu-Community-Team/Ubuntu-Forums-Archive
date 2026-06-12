---
title: "Cannot get papagayo to run - edit script ?"
date: 2010-01-23
forum: General Help
---

### Post by LuridCinema on 2010-01-23
Hey Im trying to get aprogram to run. I have java configured to work but the program won't start. It says "**Please edit the startup script before running Papagayo." in the startup script but WHAT & HOW do I edit ???. ** The shell script sez :

#!/bin/sh

if echo $(dirname $0) | grep '^/.*' > /dev/null; then
    PAPAGAYO_DIR=$(dirname $0)
else
    PAPAGAYO_DIR=$(pwd)/$(dirname $0)
fi
PAPAGAYO_LOCATION=$PAPAGAYO_DIR/papagayo.py
export PAPAGAYO_LOCATION

export LC_ALL=C
export LANG=C
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$PAPAGAYO_DIR

if [ -e "$PAPAGAYO_LOCATION" ]; then
    python $PAPAGAYO_LOCATION $*
else
    echo "**Please edit the startup script before running Papagayo.**"
fi

I have the folder in my Home folder .. , Ive tried putting home/papagayo where it says "(dirname $0)"    what am I doing wrong ???

Im a complete NOOB when it come to scripting.. I googled "**Please edit the startup script before running Papagayo"  **but found nada

---

### Post by LuridCinema on 2010-01-23
Or.. can someone show me where I can learn about startup scripts ??

---

### Post by n0dix on 2010-01-23
> **LuridCinema said:**
> Or.. can someone show me where I can learn about startup scripts ??

Do you run the program in the papagayo directory in /home/<user>. For example: /home/<user>/papagayo ??

---

### Post by LuridCinema on 2010-01-23
Yes I TRY to run it in the home directory .. nothing happens
I open a terminal in the papagayo drectory home/user/papagayo 
Tried clicking on the papagayo file and click run and nothing
I also tried open with ..sun java and nothing

---

### Post by n0dix on 2010-01-23
Do manually:
1. Copy the directory papagayo/ to /home/<user>.
2. export /home/<user>/papagayo
   export LC_ALL=C
   export LANG=C
   export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/<user>/papagayo
3. cd /home/<user>/papagayo
4. python papagayo.py

Good luck!

---

### Post by LuridCinema on 2010-01-23
I tried that

p9@p9-desktop:~/papagayo$ export /home/p9/papagayo
bash: export: `/home/p9/papagayo': not a valid identifier

---

### Post by LuridCinema on 2010-01-23
Still trying .. I treid so far :

p9@p9-desktop:~/papagayo$ export LC_ALL=C
p9@p9-desktop:~/papagayo$ export LANG=C
p9@p9-desktop:~/papagayo$ export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/p9/papagayo
p9@p9-desktop:~/papagayo$ python papagayo.py
Traceback (most recent call last):
  File "papagayo.py", line 24, in <module>
    from LipsyncFrame import LipsyncFrame
  File "/home/p9/papagayo/LipsyncFrame.py", line 26, in <module>
    import lm
  File "/home/p9/papagayo/lm.py", line 5, in <module>
    import _lm
ImportError: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by LuridCinema on 2010-01-23
from the read me :
Installing
------------------------------------------------

To install Papagayo on your Linux system, all you should need to do is to decompress the package and place it wherever you like on your system. To launch Papagayo, run the script called 'papagayo' included in the download. If you run into problems, you may need to make small adjustments to that startup script.

---

### Post by n0dix on 2010-01-23
> **LuridCinema said:**
> 
ImportError: libstdc++.so.5: cannot open shared object file: No such file or directory

To solve this problem, run:
```
sudo apt-get install libstdc++5
```

---

### Post by LuridCinema on 2010-01-23
p9@p9-desktop:~$ sudo apt-get install libstdc++5
[sudo] password for p9: 
Sorry, try again.
[sudo] password for p9: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++5 has no installation candidate
p9@p9-desktop:~$ sudo apt-get install libstdc++.so.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libstdc++.so.5
p9@p9-desktop:~$

---

### Post by LuridCinema on 2010-01-23
p9@p9-desktop:~$ sudo apt-get install libstdc++5
[sudo] password for p9: 
Sorry, try again.
[sudo] password for p9: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++5 has no installation candidate
p9@p9-desktop:~$ sudo apt-get install libstdc++.so.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libstdc++.so.5
p9@p9-desktop:~$



[IMG]file:///home/p9/Desktop/Screenshot.png[/IMG][IMG]http://spasunlimitedofhouston.com/Screenshot1.png[/IMG]

---

### Post by n0dix on 2010-01-23
Sadly i realize that software: Papagayo, have very time without update, since 2005. I think it's difficult to run. However, i try to run the lib: libstdc++5, but it's update to another version. I recommend you to try a similar software instead.

---

### Post by LuridCinema on 2010-01-23
OK fine.. thanxx for all the effort & hand holding !

---

### Post by LancerNZ on 2011-01-03
> **n0dix said:**
> Sadly i realize that software: Papagayo, have very time without update, since 2005. I think it's difficult to run. However, i try to run the lib: libstdc++5, but it's update to another version. I recommend you to try a similar software instead.
Sorry, but I don't think that's solving the problem. Old though it is, Papagayo is reputed as being *_the_* choice of software for lipsyncing. Other similar softwares just don't cut the ice. I'm not a coder myself - though is there a workaround, like changing a line in the script to make it work for Ubuntu 10.04-LTS?

It's kind of crap when people tell you programs not working are your fault because your distro's not up-to-the-hour in updates, and then when you've updated "latest" in everything, the community blames the program you want for being old. Surely Open Source is meant to be a solution to such problems?

---

