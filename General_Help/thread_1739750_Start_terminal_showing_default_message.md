---
title: "Start terminal showing default message"
date: 2011-04-26
forum: General Help
---

### Post by tikamchandrakar@gmail.com on 2011-04-26
Hello Sir,

Ques-1 what is the default bashrc and how i can set path java and tomcat?
Ques -2 When I start the terminal it showing the following line ? How i cat solve this? 


Command 'lesspipe' is available in the following places
 * /bin/lesspipe
 * /usr/bin/lesspipe
The command could not be located because '/usr/bin:/bin' is not included in the PATH environment variable.
lesspipe: command not found
Command 'dircolors' is available in '/usr/bin/dircolors'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
dircolors: command not found
Command 'uname' is available in '/bin/uname'
The command could not be located because '/bin' is not included in the PATH environment variable.
uname: command not found
Command 'uname' is available in '/bin/uname'
The command could not be located because '/bin' is not included in the PATH environment variable.
uname: command not found
bash: [: !=: unary operator expected
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: =: unary operator expected
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: too many arguments
bash: [: =: unary operator expected
Command 'sed' is available in '/bin/sed'
The command could not be located because '/bin' is not included in the PATH environment variable.
sed: command not found
Command 'sort' is available in '/usr/bin/sort'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
sort: command not found
Command 'sed' is available in '/bin/sed'
The command could not be located because '/bin' is not included in the PATH environment variable.
sed: command not found
Command 'sed' is available in '/bin/sed'
The command could not be located because '/bin' is not included in the PATH environment variable.
sed: command not found
bash: /home/tikam/TikamChandrakar/Androide/android-sdk-linux_x86: No such file or directory

---

### Post by nothingspecial on 2011-04-26
1. Where are java and tomcat



2. Looks like you've messed up your .bashrc

To reset it back to the default you can do

```
cp /etc/skel/.bashrc ~/ && . ~/.bashrc
```

---

### Post by nothingspecial on 2011-04-26
Also, I'd pop over to the resolution center and ask the mods to change your username or you are going to get spammed.

---

### Post by tikamchandrakar@gmail.com on 2011-04-27
> **nothingspecial said:**
> 1. Where are java and tomcat



2. Looks like you've messed up your .bashrc

To reset it back to the default you can do

```
cp /etc/skel/.bashrc ~/ && . ~/.bashrc
```


thanks its resolve

---

