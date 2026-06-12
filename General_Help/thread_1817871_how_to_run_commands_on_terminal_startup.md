---
title: "how to run commands on terminal startup"
date: 2011-08-03
forum: General Help
---

### Post by cyberjar09 on 2011-08-03
Hi, 

I have a question regarding terminal. I try to launch it from the "Startup Applications" by entering a script ```
sh -c '/usr/bin/gnome-terminal' 
``` but it does not start.

Also, when it does start I would like it to auto run certain commands:

navigate to my project folder 
run "play test" 
open a new tab
run "top"

how can I achieve this?

thanks in advance.

---

### Post by jwbrase on 2011-08-03
> **cyberjar09 said:**
> Hi, 

I have a question regarding terminal. I try to launch it from the "Startup Applications" by entering a script ```
sh -c '/usr/bin/gnome-terminal' 
``` but it does not start.

I'm not sure why you need to invoke sh -c there. Just gnome-terminal should work.

> 
Also, when it does start I would like it to auto run certain commands:

navigate to my project folder 
run "play test" 
open a new tab
run "top"

how can I achieve this?

thanks in advance.

Well, I'd personally do it with gnome-terminal profiles and --tab-with-profile.

You can create a profile by opening gnome-terminal and going to Edit -> Profiles, and clicking on the new button. You'll then get a dialog asking for the name of the profile and the profile you want to base it on. Fill that out and hit "Create". You'll then get a dialog with various options. In the "Title and Command" tab of that dialog, you can set what command the profile runs when it starts up.

The command I'd run set to run in the "Startup Applications" dialog would be something like this:

```
gnome-terminal --tab-with-profile=$NAME_OF_PLAY_PROFILE --tab-with-profile=$NAME_OF_TOP_PROFILE
```

Where the play profile runs a shell script along the lines of:

```
cd $PROJECTFOLDER
play test
exec $YOUR_PREFERRED_SHELL
```

And the top profile either runs top directly (in which case the tab will close when you quit top) or else, if you still want a shell when you exit top, something like the following:

```
#If you don't want to be in your home directory when top exits:
#cd $THE_DIRECTORY_YOU_WANT_TO_BE_IN_WHEN_TOP_EXITS
top
exec $YOUR_PREFERRED_SHELL
```

---

### Post by cyberjar09 on 2011-08-04
Wow, thanks a lot jwbrase, I am facing a problem though. 

I created the "top" profile and it functions as expected when I run the command ```
gnome-terminal --tab-with-profile=Top
``` it behaves as expected but when I run the command ```
gnome-terminal --tab-with-profile=Play
``` to test it, I get an error in the newly created terminal :

"There was an error creating the child process for this terminal" and 
"Failed to execute child process "cd" (No such file or directory)". 
These lines of text appear in a red box on top of the window, along with two buttons "Profile Preferences" and "Relaunch". 

I have set the command to ```
cd /home/****/development/projects/iq***/ && play test
```

I also tried ```
cd development/projects/iq***/ && play test
``` and also 

```
"cd development/projects/iq***/ && play test"
```

anything wrong I am doing here?

---

### Post by fdrake on 2011-08-05
```
"cd development/projects/iq***/ && play test"
```

anything wrong I am doing here?[/QUOTE]

try 
```
cd "/development/projects/iq**" && play test
```

1.by the way there is no dev* folder on the / folder!!
what path are you exactly looking for? open the folder  and right click inside the folder > open terminal> look at the address in the terminal

2. play is not a command in bash that i know

---

### Post by cyberjar09 on 2011-08-05
> > **fdrake said:**
> ```
"cd development/projects/iq***/ && play test"
```

anything wrong I am doing here?

try 
```
cd "/development/projects/iq**" && play test
```

1.by the way there is no dev* folder on the / folder!!
what path are you exactly looking for? open the folder  and right click inside the folder > open terminal> look at the address in the terminal

2. play is not a command in bash that i know

I tried ```
cd "development/projects/iq**/" && play test
``` as well as ```
cd "/home/****/development/projects/iq**/" && play test
``` but I get the same error again. 

Also fdrake, the development folder is in my home folder, not in root. 

Play is a command I have added to my path since I develop a lot within the framework.

---

### Post by fdrake on 2011-08-05
> **cyberjar09 said:**
> I tried ```
cd "development/projects/iq**/" && play test
``` as well as ```
cd "/home/****/development/projects/iq**/" && play test
``` but I get the same error again. 

Also fdrake, the development folder is in my home folder, not in root. 

Play is a command I have added to my path since I develop a lot within the framework.

```
cd "/home/****/development/projects/iq**/" ; play test
```
i was taken by the play command that i foprgot that you don't need to put cd in the background (&&)

---

### Post by cyberjar09 on 2011-08-05
> **fdrake said:**
> ```
cd "/home/****/development/projects/iq**/" ; play test
```
i was taken by the play command that i foprgot that you don't need to put cd in the background (&&)

I tried what you suggested, still no joy. The problem lies in the "cd" command I believe.

---

### Post by fdrake on 2011-08-05
> **cyberjar09 said:**
> I tried what you suggested, still no joy. The problem lies in the "cd" command I believe.

can you post here the error message? copy and paste.

---

### Post by cyberjar09 on 2011-08-05
> **fdrake said:**
> can you post here the error message? copy and paste.

The error is the same as I posted before :

>  "There was an error creating the child process for this terminal" and 
"Failed to execute child process "cd" (No such file or directory)". 
These lines of text appear in a red box on top of the window, along with two buttons "Profile Preferences" and "Relaunch". 

Also, please find attached screenshot for your reference.

---

### Post by fdrake on 2011-08-05
> **cyberjar09 said:**
> The error is the same as I posted before :



Also, please find attached screenshot for your reference.

yes but the problem is "play" not cd. when you send the command play the termian does not know what to do ..

run 

```
which play
``` 
if it's a commant you should have the path of the file
like ```
which cat ; which less
```

---

### Post by cyberjar09 on 2011-08-05
fdrake, 

the first screenshot I attached was a mistake, I edited my post. please see the screenshot again.

---

### Post by jwbrase on 2011-08-05
> **cyberjar09 said:**
> Wow, thanks a lot jwbrase, I am facing a problem though. 

I created the "top" profile and it functions as expected when I run the command ```
gnome-terminal --tab-with-profile=Top
``` it behaves as expected but when I run the command ```
gnome-terminal --tab-with-profile=Play
``` to test it, I get an error in the newly created terminal :

"There was an error creating the child process for this terminal" and 
"Failed to execute child process "cd" (No such file or directory)". 
These lines of text appear in a red box on top of the window, along with two buttons "Profile Preferences" and "Relaunch". 

I have set the command to ```
cd /home/****/development/projects/iq***/ && play test
```

I also tried ```
cd development/projects/iq***/ && play test
``` and also 

```
"cd development/projects/iq***/ && play test"
```

anything wrong I am doing here?

I should have mentioned: When you enter a command line in a normal terminal session, it's interpreted by a shell and then passed to any relevant programs. When you enter it into a text field in a graphical window (like the "custom command" field for a gnome-terminal profile) it is generally *not* interpreted by a shell: The first word is taken as the name of the program to execute and the rest of the string is passed to the program as parameters. So shell syntax like "&&" doesn't get parsed, and the program you're launching dies when it finds that "&&" (or whatever the first bit of shell syntax it finds is) in its parameters. If you use something expanded by the shell in the command name itself (like ~/bin/anExecutable for /home/$USERNAME/bin/anExecutable), then gnome-terminal won't even know what program to start.

So the whole

```
cd $PROJECTFOLDER
play test
exec $YOUR_PREFERRED_SHELL
```

thing has to be done in an actual shell script. You then put the name of the script in the "custom command" field for the "Play" profile.

---

### Post by cyberjar09 on 2011-08-05
> **jwbrase said:**
> I should have mentioned: When you enter a command line in a normal terminal session, it's interpreted by a shell and then passed to any relevant programs. When you enter it into a text field in a graphical window (like the "custom command" field for a gnome-terminal profile) it is generally *not* interpreted by a shell: The first word is taken as the name of the program to execute and the rest of the string is passed to the program as parameters. So shell syntax like "&&" doesn't get parsed, and the program you're launching dies when it finds that "&&" (or whatever the first bit of shell syntax it finds is) in its parameters. If you use something expanded by the shell in the command name itself (like ~/bin/anExecutable for /home/$USERNAME/bin/anExecutable), then gnome-terminal won't even know what program to start.

So the whole

```
cd $PROJECTFOLDER
play test
exec $YOUR_PREFERRED_SHELL
```

thing has to be done in an actual shell script. You then put the name of the script in the "custom command" field for the "Play" profile.
thanks again jwbrase, though now I have 2 questions

1. what does the exec command do? the man page states that it executes a command, is it mandatory to put exec "$YOUR_PREFERRED_SHELL" in the script? and if so, what would replace $YOUR_PREFERRED_SHELL"?

2. In the "Custom command" field, I tried entering just the path to the shell script (it's on my Desktop) but I am still encountering the same error.

---

### Post by jwbrase on 2011-08-05
> **cyberjar09 said:**
> thanks again jwbrase, though now I have 2 questions

1. what does the exec command do? the man page states that it executes a command, is it mandatory to put exec "$YOUR_PREFERRED_SHELL" in the script? and if so, what would replace $YOUR_PREFERRED_SHELL"?

The exec command replaces the currently running shell with whatever command you type after exec. In this case, it replaces the shell instance running the script with one that will take commands from the user. If you just put

```
$YOUR_PREFERRED_SHELL
```

on that line, the user would see pretty much the same thing, but the shell instance running the script, even though it would already be done, wouldn't exit until the user exited the new shell, so doing it that way is a bit sloppy.

As to whether that line is mandatory, it depends on what you want. If it's OK for the tab to close as soon as "play test" is done, you don't need the exec line. If not, you need it so that you'll get a command line after the script is done.

$YOUR_PREFERRED_SHELL can be replaced with whatever shell you like best. The default for user interaction on Ubuntu is bash (the default script shell is dash). I personally like zsh better. If you don't know enough about the various shells to have a favorite, use bash.

> 
2. In the "Custom command" field, I tried entering just the path to the shell script (it's on my Desktop) but I am still encountering the same error.

What exactly did you type for the path?

Oh, and did you make sure to set the executable bit on the script? Either right click on the file, go to properties, go to the Permissions tab, and make sure the "Allow executing file as program" box is checked, or else open a terminal, navigate to your desktop, and type "chmod 755 $NAME_OF_SCRIPT".

---

### Post by cyberjar09 on 2011-08-08
Excellent! thanks a lot again jwbrase, it worked like a charm. Is there any way of launching the terminal as a new tab within the current window instead of launching a new terminal window?

---

### Post by jwbrase on 2011-08-08
> **cyberjar09 said:**
> Excellent! thanks a lot again jwbrase, it worked like a charm. Is there any way of launching the terminal as a new tab within the current window instead of launching a new terminal window?

The directions I gave should do exactly that.

I do notice that you said the following in post #3:

> **cyberjar09 said:**
> ... when I run the command ```
gnome-terminal --tab-with-profile=Top
``` it behaves as expected but when I run the command ```
gnome-terminal --tab-with-profile=Play
``` to test it ...

If you're doing this with two separate commands:

```
gnome-terminal --tab-with-profile=abc 
gnome-terminal --tab-with-profile=xyz
```

You will get two separate windows. If you do it as one command:

```
gnome-terminal --tab-with-profile=abc --tab-with-profile=xyz
```

You should get one window with two tabs.

---

### Post by cyberjar09 on 2011-08-09
great! thanks a lot buddy. im a bit of a n00b so im really grateful for all the help from the forum. I only recently switched over from the windows ecosystem to open source.

---

