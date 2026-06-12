---
title: "java jre, bittorrent and bash"
date: 2005-01-24
forum: General Help
---

### Post by it_clumps! on 2005-01-24
hi!

yesterday i installed some stuff on my pc..great job, i thought.
this morning i started ubuntu and my terminal..doesn't work!

it gives me the following message with every command i try to use:

bash: dircolors: command not found
mariella@mariella:~ $ ls
bash: ls: command not found

so i can't do almost anything!
help me plz!

( I checked bash.bashrc and I found an error i made yesterday installing java jre. i had to write:

JAVA_HOME=/usr/java/jre1.5.0_01
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH

but on the third line i wrote : PATH=$JAVA_HOME/bin.
After that, without restarting gnome, i installed bittorrent from the bash and restarted my pc.. )

thank u

m

---

### Post by it_clumps! on 2005-01-24
well.
i searched the internet and i found that the problem i have was caused by my error in defining the PATH.
now, i need to use root to edit bash.bashrc and change it.
how can i act as root if i can't use sudo, sudo -s, su and in general the bash?
there is an emergency terminal or something like that? i have already tried the emergency terminal i found in the user login "page" at startup and it doesn't work!! ](*,)  

thanx 

m

---

### Post by martijntje on 2005-01-24
You can use export to change your PATH variable once. After that, you should be able to restore the error.
  
  Your path should be something like this:
  > /usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin:/usr/bin/X11
  
  So just run > export PATH=/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin:/usr/bin/X11
 
 export is a command internal to bash, and so should work just fine :)

---

### Post by it_clumps! on 2005-01-24
[QUOTE=martijntje]You can use export to change your PATH variable once. After that, you should be able to restore the error.
  
  Your path should be something like this:
  
  
  So just run 
 
 export is a command internal to bash, and so should work just fine :)[/QUOTE]

wow, it worked!!
thank u 

if u have some spare time:
hum hum.. what did i do running export?
what is that long path? 

m

---

### Post by martijntje on 2005-01-24
export is a simple command to export variables to the system.
Some programs depend on those variables to do various things. Changing these variables, basically changes options in the program.

bash (the shell you use) is an example of such a program. If you type a command, and that command is not an internal command (like export is, it's built into bash), it looks through all the files in all your PATH directories to see if it can find the command.

In your case, you messed up the PATH variable, so bash couldn't find any programs, thus nothing worked.

The long PATH line i gave you, was basically a list of all common program directories.
Also, running the export thingy i gave you, hasn't permanently solved your problem.

bash runs a few files on startup, to, among other things, initialize variables like PATH. To permanently solve your problem, you will have to put the correct export line in one of those files.

Hope this cleared things up. Feel free to search google in case you have any more question :P

---

### Post by it_clumps! on 2005-01-28
[QUOTE=martijntje]export is a simple command to export variables to the system.
Some programs depend on those variables to do various things. Changing these variables, basically changes options in the program.

bash (the shell you use) is an example of such a program. If you type a command, and that command is not an internal command (like export is, it's built into bash), it looks through all the files in all your PATH directories to see if it can find the command.

In your case, you messed up the PATH variable, so bash couldn't find any programs, thus nothing worked.

The long PATH line i gave you, was basically a list of all common program directories.
Also, running the export thingy i gave you, hasn't permanently solved your problem.

bash runs a few files on startup, to, among other things, initialize variables like PATH. To permanently solve your problem, you will have to put the correct export line in one of those files.

Hope this cleared things up. Feel free to search google in case you have any more question :P[/QUOTE]


hehehe, thank u

sometimes i'm so curious that i can't wait!!  :wink: 

m

---

