---
title: "How to create a launcher with a .bin file"
date: 2010-11-08
forum: General Help
---

### Post by coyoterunner on 2010-11-08
hello,

I am trying to make a launcher to a bin file.I am able to execute the bin file using sudo ./filename.bin. But when i am trying to use it with a launcher i cannot execute it. I understand that i must not use the ./ symbol in the launcher.


I did my homework (google is my friend) and i found that ./ represents the PATH variable. Thus, i copied the bin file to usr/local/bin to avoid using ./ before the filename.  Unfortunately i had no success in the launcher. I tried using in the launcher the whole path or only with the filename but to no avail. I checked that even when i use the terminal i cannot execute the bin file using the whole path. The only way i can execute this file is to go to the directory where bin file is and execute it.

What i am missing here?

Thx in advance,

Chris

---

### Post by Barriehie on 2010-11-08
Try this for launcher command:
```

/bin/bash /usr/local/bin/SomeFileName.bin
```

---

### Post by coyoterunner on 2010-11-09
It is not working... I tried it also in the terminal and it tells me that it cannot execute the binary file. 

Note that i have changed the permission to be an executable file.

Can it be that a bin file cannot be used with a launcher?

---

### Post by Barriehie on 2010-11-09
I had a .run file when I installed vbox, it looked like a bash script except for the extension. Might have to be root.
```

sh filename.run
```

---

### Post by gandaran on 2010-11-09
> The only way i can execute this file is to go to the directory where bin file is and execute it.
and how do you execute it? what application is it? shouldn't you have to run the .bin file to install it?

---

### Post by mister_playboy on 2010-11-09
I'd like an answer to this question... in my case the binary is a Sega system emulator, Kega Fusion. :popcorn:  Right now all I can do is navigate to it in Dolphin and double click or cd to the directory and run from the terminal.

---

### Post by coyoterunner on 2010-11-09
The only way i can execute the bin file is using the terminal and going to the directory where the bin file is and using only 

```
./filename.bin
``` 

It is not an installer. It is a game thats loads. I just wanted to make a launcher to avoid terminal.Pffff

Absolute paths do not work. It is strange!


the command sh didnt worked either  :(:(

---

### Post by gandaran on 2010-11-09
> **coyoterunner said:**
> The only way i can execute the bin file is using the terminal and going to the directory where the bin file is and using only 

```
./filename.bin
``` 

It is not an installer. It is a game thats loads. I just wanted to make a launcher to avoid terminal.Pffff

Absolute paths do not work. It is strange!


the command sh didnt worked either  :(:(
try 
[COLOR="DarkRed"]exec /path-to-folder/filename.bin[/COLOR]
[COLOR="DarkRed"]or
exec ./path-to-folder/filename.bin[/COLOR]
I'm not sure if any of the two can work but try anyway.

---

### Post by |{urse on 2010-11-09
Maybe some genius will help us both out.

#!/bin/bash
read -p "path to bin" -e PATH
read -p "bin name" -e NAME
exec $PATH/$NAME

did using exec work?

---

### Post by coyoterunner on 2010-11-09
Nothing !!!

exec is not working! This is getting on my nerves! Anyway i appreciate u all for the help. Although i am convinced that there must be a way to execute a bin file with a launcher. Strange that i cannot find a hint on the internet.

---

### Post by gandaran on 2010-11-09
> **coyoterunner said:**
> Nothing !!!

exec is not working! This is getting on my nerves! Anyway i appreciate u all for the help. Although i am convinced that there must be a way to execute a bin file with a launcher. Strange that i cannot find a hint on the internet.
I don't know but maybe bin files can only be run from terminal!
so this is just an idea, try it, ensure the file is marked as executable and enter the launch command like this
```
gnome-terminal ./path-to-folder/filename.bin
```
or
```
gnome-terminal sh /path-to-folder/filename.bin
```
or
```
gnome-terminal -x sh /path-to-folder/filename.bin
```

---

### Post by |{urse on 2010-11-09
Actually all of those suggestions work just fine in my script. =)

---

### Post by efflandt on 2010-11-09
Where is the bin file located (its full path) and what are its file permissions?  If you create a bin directory in your home directory ( **mkdir ~/bin** ), the next time you log into your system, that bin directly will be in your PATH.  If you put your bin file in your bin directory you will not need a path to the bin file in your launcher.  But that may also depend whether your bin file needs to find the path to any related files or config files.

efflandt@XPS-8100:~$ echo $PATH
/home/efflandt/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by coyoterunner on 2010-11-10
If it is working for other people then the bin file may have a problem. Although it is executed normally from the terminal!

Regarding permissions, I right clicked the bin file and tick the option to be an executable file. Isnt that enough?

```
gnome-terminal ./path-to-folder/filename.bin
```

Did not worked. It replied with no such file or directory

```
gnome-terminal sh /path-to-folder/filename.bin
```

Did not worked. Syntax error in bin file.

```
gnome-terminal -x sh /path-to-folder/filename.bin
```

Did not worked. No such command


I have put the .bin files together with the configurations files in /usr/local/bin

Do you suggest me to copy all files to my home folder and try executing the bin file using only its name?

---

### Post by |{urse on 2010-11-10
If it helps i have my .bin in the same folder as my script.

---

