---
title: "don't type ./"
date: 2009-09-08
forum: General Help
---

### Post by sombrancelha on 2009-09-08
Hi,

When I'm running a script or program through Terminal, I have to type ./ and then it's name. How can I configure Terminal just to let me type the name of the program?

thanks

---

### Post by *malagant* on 2009-09-08
```
PATH=$PATH:/path-to-script
```

You can add this line to your /home/<name>/.bashrc file, so it's active all the time.

---

### Post by Copernicus1234 on 2009-09-08
If you always want to have the directory you are standing in as part of your path (which I think is what you want), add this:

```
PATH=$PATH:.
```

---

### Post by DaithiF on 2009-09-08
Hi,
the PATH environment variables defines the list of directories that the shell will search through when looking for a command that you enter when you don't provide an explicit path to that command.  You are asking how you can add the current directory to that PATH.  Its not generally recommended that you do this, as its considered a security risk -- in theory you could end up running a command that you did not intend, so for example if someone placed a script called 'ls' in your home directory, that script would get called rather than the shell built-in command 'ls' whenever you try to run ls.

If there are particular directories that contain scripts you run frequently you could add those directories to your PATH variable instead.

But if you really want to add the current directory to your path, then the way you would do it is to have a line like this in your .bashrc file
```
export PATH=.:$PATH
```

---

### Post by Copernicus1234 on 2009-09-08
> **DaithiF said:**
> Hi,
the PATH environment variables defines the list of directories that the shell will search through when looking for a command that you enter when you don't provide an explicit path to that command.  You are asking how you can add the current directory to that PATH.  Its not generally recommended that you do this, as its considered a security risk -- in theory you could end up running a command that you did not intend, so for example if someone placed a script called 'ls' in your home directory, that script would get called rather than the shell built-in command 'ls' whenever you try to run ls.

If there are particular directories that contain scripts you run frequently you could add those directories to your PATH variable instead.

But if you really want to add the current directory to your path, then the way you would do it is to have a line like this in your .bashrc file
```
export PATH=.:$PATH
```

Its not good to add the . to the beginning of the path string. Ubuntu searches the path from left to right. If you have a file named "ls" in the directory you are standing in and type "ls", the system will use that file and not the ls command in /bin/ls. This is of course true for all commands.

I therefore recommend adding the "." to the end of the path to avoid these problems. That way the system commands are found first.

---

### Post by Simian Man on 2009-09-08
It's much better to add "." to the *end* of your PATH, as Copernicus1234 showed, rather than the *beginning* of your PATH as DaithiF showed.  This way there is no chance of scripts taking precedence over built-in commands in /usr/bin.

---

### Post by Vaphell on 2009-09-08
[http://www.linuxforums.org/forum/misc/27942-linux-doesnt-automatically-add-current-directory-path.html](http://www.linuxforums.org/forum/misc/27942-linux-doesnt-automatically-add-current-directory-path.html)

---

### Post by DaithiF on 2009-09-08
best practice is not to add the current directory anywhere in the path, but yes the other posters are correct to point out that adding at the end is better than at the beginning as I showed.

the reason why adding at the end is not good practice either though is that it still leaves open the possibility of command typos resulting in commands being run by placing scripts with those names in a directory -- eixt, sl, ehco for example ... slim likelihood perhaps, but enough for me to prefer to add the ./ to a command i want to execute from the current directory.

---

### Post by cariboo on 2009-09-08
Why not move your script to /usr/local/bin, then you don't have to adjust the path. In usr/local/bin the script will be available to all users.

---

### Post by DaithiF on 2009-09-08
or if the scripts are specifically yours, then its common practice also to have a /home/yourname/bin directory to put them in, and then you add that directory to your path.

---

### Post by sombrancelha on 2009-09-08
Actually, I don't use many scripts (I used my first last week). The main reason I want to change this is for the C programs I have to do for university.

I added
```
export PATH=.:$PATH
```
and it's working. Thanks.

---

