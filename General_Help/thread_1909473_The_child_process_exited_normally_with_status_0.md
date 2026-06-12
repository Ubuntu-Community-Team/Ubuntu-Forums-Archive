---
title: "The child process exited normally with status 0"
date: 2012-01-15
forum: General Help
---

### Post by Raff1 on 2012-01-15
I have made a couple of scripts that cd-s to a specific directory and starts a program. When running these "Run in Terminal", everything works seemingly normally until i try closing the program. Then I get the following mesage:
```
The child process exited normally with status 0. [Relaunch]
```(Upon Relaunch, I open the program again as before.) 
While this error-message is present, I cant use the terminal. Furthermore, while running the program, I can't abort the program through the terminal by pressing ctrl+z or ctrl+x.

[COLOR=Red]Solution[/COLOR]
 This was due to a terminal setting: 
```
Edit > Profile Preferences > Title and Command > When command exits: Hold the terminal open
```Set this to "Exit the terminal". [COLOR=Red]
/Solution[/COLOR]

The main problem with this is that the scripts I open this way by using  "Run in Terminal" don't seem to invoke the .bashrc; at least ifort is  seemingly not added to path in these terminal sessions (which is done in  .bashrc) which is the core of my problem.

[COLOR=DarkGreen][COLOR=Red]EDIT[/COLOR]: This is a separate issue I am adressing[/COLOR] [COLOR=DarkGreen][COLOR=Navy][here]("http://ubuntuforums.org/showthread.php?t=1910442")[/COLOR].[/COLOR]

If I open a terminal manually (ctrl+t) and pastes the content of a script in question, everything works normally. Ifort is added to path, I can abort the program with crtl+z and when I close the program normally, the error "The child process exited normally with status 0." is not displayed.

So how can I get around this error?

---

### Post by Habitual on 2012-01-15
Post one of the scripts causing the "error" and the contents of 
Terminal > 
```
 echo $PATH
```

---

### Post by Raff1 on 2012-01-15
> **Habitual said:**
> Post one of the scripts causing the "error" and the contents of 
Terminal > 
```
 echo $PATH
```

Actually, this enables me to illustrate my problem.
```
$ echo $PATH
**/opt/intel/composerxe-2011.3.174/bin/intel64**:/home/user/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:**/opt/intel/composerxe-2011.3.174/mpirt/bin/intel64**

```I made this file and set it executable:
echoPath
```
echo $PATH
```
When run as "Run in Terminal" it gives the following output:
```
/home/user/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```Also showing the error-message:
```
The child process exited normally with status 0. [Relaunch]
```in the top of the terminal. The terminal is then unusable for other things, and the intel libriaries (ifort) are clearly not added to the $PATH environment.

Thank you so much for the help!

---

### Post by Raff1 on 2012-01-16
For the record, this is the relevant line from .bashrc:
```

# Adding ifort to path at the beginning of every terminal session
source /opt/intel/bin/compilervars.sh intel64

```

---

### Post by Raff1 on 2012-01-17
The problem with "The child process exited normally with status 0" was simply due to a setting in my terminal preferences:
```

When command exits: Hold the terminal open
```I set this back to the default: Exit the terminal.

My actual problem is independent of the problem stated in the topic, I therefore made a new thread about it [here]("http://ubuntuforums.org/showthread.php?p=11617709#post11617709"), and now mark this thread as [SOLVED].

**Habitual**: Thanks for helping me on the right track!

---

### Post by Habitual on 2012-01-17
raff:

Glad it worked out!

---

