---
title: "Custom Commands"
date: 2011-12-09
forum: General Help
---

### Post by coolguy918 on 2011-12-09
Let's say that I have a specific shell script located deep within /usr/share or something like that. I don't want to type /the/full/path/scriptname each time I want to run it, so I want to be able to add a custom command that will run it automatically (like being able to just type *scriptname* at the terminal instead of the full path). How would one go about doing something like this?

---

### Post by dcstar on 2011-12-09
> **coolguy918 said:**
> Let's say that I have a specific shell script located deep within /usr/share or something like that. I don't want to type /the/full/path/scriptname each time I want to run it, so I want to be able to add a custom command that will run it automatically (like being able to just type *scriptname* at the terminal instead of the full path). How would one go about doing something like this?

[LIST=1]
[*]Create an alias in your shell profile.
[*]Put the path to the scripts in your profile PATH.
[*]Make links from a PATH folder to the scripts.
[/LIST]

---

### Post by Tank Jr on 2011-12-10
I would go to /usr/local/bin and put a symlink.
```
cd /usr/local/bin
sudo ln -s <path to script>
```

Alternately you can create a directory called bin in our home, add it to your path and put the symlink there.

---

### Post by coolguy918 on 2011-12-10
> **Tank Jr said:**
> I would go to /usr/local/bin and put a symlink.
```
cd /usr/local/bin
sudo ln -s <path to script>
```Alternately you can create a directory called bin in our home, add it to your path and put the symlink there.

...wait a second... what exactly is a symlink and how will it work?

---

### Post by sum1nil on 2011-12-10
You could use an alias for the long path name. Try looking at this link about [Alias]("http://www.brighthub.com/computing/linux/articles/79232.aspx")

:popcorn:

---

### Post by Tank Jr on 2011-12-10
I meant a symbolic link. You can think of it as a shortcut.
The directory /usr/local/bin is in your path already; any executable in that directory can be invoked directly from the terminal without typing the whole path. Now if you have an executable script somewhere, and you create a symbolic link for it in /usr/local/bin, you can use the script from the terminal.

---

### Post by mcduck on 2011-12-10
> **Tank Jr said:**
> 
Alternately you can create a directory called bin in our home, add it to your path and put the symlink there.
You don't even need to add ~/bin to your path, it's automatically added into user's path at login time if the directory exists. ;)

---

### Post by coolguy918 on 2011-12-10
Well I must be totally dumb because while I *kinda* get what you guys are trying to say, it still doesn't make sense. It sounds like you guys want me to do this in my profile, and I want this to be a system-wide change. Like for example, when I installed GNOME on my server (don't judge me for installing a GUI on a server :P ), it also installed Firefox and registered the "firefox" command, so any user who happens to have X11 tunneling enabled can simply type "firefox" at the terminal and Firefox will come up on the screen. I want to do something similar to this for my custom shell script, where I can just type "customscriptname" at the terminal and have it executed without having to use CD and whatnot. And it's not in /usr/bin, it's in a subfolder of a subfolder of /usr/share. I don't know if I got confused while typing that or if you guys are confused, so just clearing that up. Like does that make any sense?

---

### Post by mutley89 on 2011-12-10
What dcstar said in more detail:

1.  Create an alias. An alias is simply a name that bash replaces with the text assigned to it. add this to the end of your ~/.bashrc, or to /etc/bashrc to make it apply to all users
```
alias somename='/usr/share/path/to/script'
```then run the following to source (reread) your bashrc:
```
. ~/.bashrc
```typing somename will then run your script

2. Extend your PATH to include the directory containing the scripts: The PATH variable is a list of directories where bash searches for a command. To add to it, add this to the end of ~/.profile:
```
PATH=$PATH:/directory/containing/yourscript
```again after sourcing .profile you can simply type the name of the script

3. Make a symlink from a directory that is already in the PATH. A symlink is a file that points to another file.  Make one as follows:
```
sudo ln -s /path/to/yourscript /usr/local/bin/somename
```You will have to put sudo before this because /usr/local/bin is owned by root, or you could put it in ~/bin/

All the above approaches will work.  You could also simply move the script to a directory in your PATH.  You can what your current PATH is with the command "echo $PATH".

---

### Post by coolguy918 on 2011-12-10
> **mutley89 said:**
> What dcstar said in more detail:

1.  Create an alias. An alias is simply a name that bash replaces with the text assigned to it. add this to the end of your ~/.bashrc, or to /etc/bashrc to make it apply to all users
```
alias somename='/usr/share/path/to/script'
```then run the following to source (reread) your bashrc:
```
. ~/.bashrc
```typing somename will then run your script

2. Extend your PATH to include the directory containing the scripts: The PATH variable is a list of directories where bash searches for a command. To add to it, add this to the end of ~/.profile:
```
PATH=$PATH:/directory/containing/yourscript
```again after sourcing .profile you can simply type the name of the script

3. Make a symlink from a directory that is already in the PATH. A symlink is a file that points to another file.  Make one as follows:
```
sudo ln -s /path/to/yourscript /usr/local/bin/somename
```You will have to put sudo before this because /usr/local/bin is owned by root, or you could put it in ~/bin/

All the above approaches will work.  You could also simply move the script to a directory in your PATH.  You can what your current PATH is with the command "echo $PATH".
Okay thanks! I'll try it!

---

