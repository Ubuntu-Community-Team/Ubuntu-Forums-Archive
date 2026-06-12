---
title: "how to load a script at boot??????"
date: 2010-08-28
forum: General Help
---

### Post by anirudhmalpe on 2010-08-28
I have created a script which is displayed below to lock the terminal with a password protection.I copied the following shell script to the init.d folder and executed the command "update -rc.d filename defaults" to load the script to the system but it shows me a error saying that my script does'nt satisfy the specifications.so please help me by adding the specifications for the following script and please tell me if I am doing this in a wrong way.



#!/bin/bash

stty -echo

while [ "$m" != "password" ]

do

clear

echo "\nkeyboard locked"

echo "\nenter the same password to unlock:\c"

read m

done

clear

echo "keyboard unlocked"

stty echo



please help me with the specifications since i'm a beginner in this can you please add the specifications compatible for init.d for the above program.

---

### Post by akoskm on 2010-08-28
> **anirudhmalpe said:**
> I have created a script which is displayed below to lock the terminal with a password protection.I copied the following shell script to the init.d folder and executed the command "update -rc.d filename defaults" to load the script to the system but it shows me a error saying that my script does'nt satisfy the specifications.so please help me by adding the specifications for the following script and please tell me if I am doing this in a wrong way.



#!/bin/bash

stty -echo

while [ "$m" != "password" ]

do

clear

echo "\nkeyboard locked"

echo "\nenter the same password to unlock:\c"

read m

done

clear

echo "keyboard unlocked"

stty echo



please help me with the specifications since i'm a beginner in this can you please add the specifications compatible for init.d for the above program.

You should put the script in the /etc/init.d/ directory, and mark it as executable
```

chmod +x <filename>

```, and then run
```

update-rc.d <filename> defaults

```, replace the <filename> with the name of your script.

---

### Post by anirudhmalpe on 2010-08-28
hi akoskm,
I did as said above and restarted but it didnt shutdown and is showing me a error "init: usplash post-start process (2556) terminated with status 1"

---

### Post by akoskm on 2010-08-28
> **anirudhmalpe said:**
> hi akoskm,
I did as said above and restarted but it didnt shutdown and is showing me a error "init: usplash post-start process (2556) terminated with status 1"

Interesting error message, since it's a shutdown process, and the script should run after the booting process. :confused:
Anyway, I was thinking about the functionality of this terminal-locking script. When do you want to lock your keyboard? Before the booting process, after, somewhere in the middle, because you can solve this in other ways.
What I described above is the simplest way to load a script at boot time - I mean, to execute the same sequence of commands at every booting in the given runlevel. I not sure is this applying to the scripts which are requiring some input from the keyboard - do you even allowed to request some input in the middle of the booting process, in this area my knowledge ends...

---

### Post by alket on 2010-08-28
in /etc/rc.local

From terminal
```
sudo gedit /etc/rc.local
```
and write it above exit 0.

---

### Post by anirudhmalpe on 2010-08-28
> **akoskm said:**
> Interesting error message, since it's a shutdown process, and the script should run after the booting process. :confused:
Anyway, I was thinking about the functionality of this terminal-locking script. When do you want to lock your keyboard? Before the booting process, after, somewhere in the middle, because you can solve this in other ways.
What I described above is the simplest way to load a script at boot time - I mean, to execute the same sequence of commands at every booting in the given runlevel. I not sure is this applying to the scripts which are requiring some input from the keyboard - do you even allowed to request some input in the middle of the booting process, in this area my knowledge ends...
I want to lock the terminal when I open it.If you know a way to lock the terminal please let me know.

---

### Post by akoskm on 2010-08-28
> **anirudhmalpe said:**
> I want to lock the terminal when I open it.If you know a way to lock the terminal please let me know.

If you want to lock the Terminal application inside your GNOME Desktop then you can try the following:
Save your script in the current users bin directory: ~/bin, and modify your .bashrc profile - if this file doesn't exist in your ~ directory just create one:
```

nano ~/.bashrc

```
and add the following line:
```

~/bin/<script name>

```.
Replace the <script name> with the actual name of your script.
Save this file, close the Terminal and start it again. Now the Terminal will ask for the password.

For testing purposes set up a test script, like:
```

#!/bin/bash
echo "Enter the magic word: "
read w
echo "Your input: "$w

```, and add that to your .bashrc profile.
After restarting the Terminal you can see that it asks first for input
```

Enter the magic word: 
asd
Your input: asd
akoskm@akoskm-laptop:~$

``` and after it gives access to the command line.

---

