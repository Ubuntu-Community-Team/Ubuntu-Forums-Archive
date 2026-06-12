---
title: "terminal doesn't accept any command"
date: 2010-07-06
forum: General Help
---

### Post by braveheart2 on 2010-07-06
was just working the other day, now no command, even cd.. wont work...how can I fix this?

---

### Post by lisati on 2010-07-06
Are you able to copy and paste any error messages that might help us provide troubleshooting suggestions?

---

### Post by WorMzy on 2010-07-06
Have you recently modified your ~/.bash_profile?

---

### Post by braveheart2 on 2010-07-06
> **WorMzy said:**
> Have you recently modified your ~/.bash_profile?

no, the only thing I've done since install is download and install Kompozer and all of drupals dependencies.

here is a image of my problem as well...even copying simple commands from tutorials doesn't work..I've already missed the deadline for installing drupal on a clients website, really pissed right now :) please help.

---

### Post by wojox on 2010-07-06
Why don't you try 

```
cd /.
```

And 

```
ls
```

and post the results

---

### Post by WorMzy on 2010-07-06
Unless you have a directory in your home folder called home (/home/luke/home), then that command won't work. If you want to cd to the home directory, use 'cd **/**home'.

---

### Post by braveheart2 on 2010-07-06
still not working, ok can you just give me the command to change directory to a specific download? I'll see if that works.

---

### Post by WorMzy on 2010-07-06
What happens when you run 'cd /home'? Do you get the same error message? Same with 'ls /'? Take a screenshot/post the output of both here.

---

### Post by akelsall on 2010-07-06
Not understanding what you mean when you say "give me the command to change directory to a specific download?". Can you explain what you mean/what you're trying to do?

You didn't indicate what your current directory is when you try to enter the command **cd home/** As someone mentioned, unless you have a directory named **home** in that directory, you won't be able to "cd home/".

To move to your home directory, all you have to enter is:

          cd <enter>  

That's it. Just enter the letters "cd" and press ENTER.

---

### Post by braveheart2 on 2010-07-06
I don't get why nothing is working, all I need to do is convert a .bin into an executable, but no commands work.

what Im attempting to do is chmod 755 bitnami-drupal-6.17-0-linux-installer.bin/

---

### Post by Samulus on 2010-07-06
Your commands work fine.  The second command you issued in that picture doesn't work because:

downloads is not the same as "Downloads". The folders are case sensitive. You're trying to navigate into a folder that doesn't exsist, "downloads". "Downloads" (with a uppercase D) does exsist however. And that's the folder you want.

The third command you issued "ls/home" didn't work because.

ls is the command for listing the files in a given directory. You typed "ls/home" ls/home is not a command. The command you wanted was just ls.

EDIT: Also just as a note when you're navigating through your system in the terminal, you'll probably want to use auto completion. To avoid mistakes like this and to speed up using it. For example, if you want to navigate to your Downloads directry you could just type "cd /home/Dow" and hit tab and it would auto complete your directory. (You could also use cd ~/Dow and hit tab too)

---

### Post by WRDN on 2010-07-06
The commands are printing error messages because you are trying to change into a directory that does not exist.

For file paths, "/" at the start is referring to the root of the file system. From here, you define where you want to go. For example, given a user "bob", to change directory into his home folder, you would use the command:

```
cd /home/bob
```

The folder "home" is located at the root of the file system, as indicated by "/home" (go to the root of the file system, then change to the home folder). Bobs home folder exists in home, so you go one level deeper - to find the number of levels, just count the number of forward-slashes. In this case, bobs home folder is 2 levels deep into the file system, from the root.

In Linux, "~" can be used as a shortcut to get to your personal home folder, so, if bob was logged in, he could type "cd ~" to get back to his home folder, instead of the command stated above.

In your case, you want to be in ~/downloads, so type:

```
cd ~/downloads
```

If you are already in your home folder, you can just type:

```
cd downloads
```

Note the lack of "/" at the start of the file path in the command above. Instead, "./" will be inserted for you. The period "." is used to denote the current directory, so you go from the current directory, down a level into downloads. It is the same as the command, "cd ./downloads" when you are in your home folder.

---

### Post by efflandt on 2010-07-06
So far you have not hardly typed anything correctly.  Your home dir is not /home, it is **/home/luke**.  Or if you just do **cd** with nothing else you end up in your home directory.  But you are also already in your home directory when you open the terminal.  You can find out what directory you are in with **pwd** command.

The second time you did cd/home you were missing the space in **cd /home**, but that is not "your" home, that is just the directory containing the home directory with your username luke (ie, /home/luke).

Linux is case sensitive.  If you downloaded something with Firefox, it is likely in Downloads, not downloads.  Since ~ represents your home directory, one way to get there if you have no clue where you are would be **cd ~/Downloads** which would be the same as /home/luke/Downloads.

Is that bin file a directory or a file.  If it is a file, there would be no trailing slash.  And it would never have a leading slash unless it is in the root directory / or you included a full path to it.

---

### Post by WorMzy on 2010-07-06
Yes, as others have already said, your problem is not the commands, but the way you are using them.

Since cd has been covered substantially, I'll explain why your ls command failed. You need to have a space between the command and the argument. In this case, ls is the command and /home is the argument -- you want to list (ls) the contents of /home. So ```
ls/home
``` should be ```
ls /home
```Without the space, your shell attempts to interpret what you have entered as a single command, and since there's no such command as "ls/home", it throws an error.

---

### Post by BikeHelmet on 2010-07-06
Assuming 10.04 is the same as 9.04...

Type this into console:
```
sudo apt-get install nautilus-open-terminal
```

Reboot or logout. After you log back in, you'll have the option of opening a terminal to whatever folder you right-click on. So go into your home folder using the GUI, right-click on the downloads folder, and open a new terminal window. Type in **ls<enter>** to get a list of files in that folder. **sudo chmod 755 filenamehere<enter>** to make it executable or whatever.

---

### Post by braveheart2 on 2010-07-06
> **WRDN said:**
> The commands are printing error messages because you are trying to change into a directory that does not exist.

For file paths, "/" at the start is referring to the root of the file system. From here, you define where you want to go. For example, given a user "bob", to change directory into his home folder, you would use the command:

```
cd /home/bob
```

The folder "home" is located at the root of the file system, as indicated by "/home" (go to the root of the file system, then change to the home folder). Bobs home folder exists in home, so you go one level deeper - to find the number of levels, just count the number of forward-slashes. In this case, bobs home folder is 2 levels deep into the file system, from the root.

In Linux, "~" can be used as a shortcut to get to your personal home folder, so, if bob was logged in, he could type "cd ~" to get back to his home folder, instead of the command stated above.

In your case, you want to be in ~/downloads, so type:

```
cd ~/downloads
```

If you are already in your home folder, you can just type:

```
cd downloads
```

Note the lack of "/" at the start of the file path in the command above. Instead, "./" will be inserted for you. The period "." is used to denote the current directory, so you go from the current directory, down a level into downloads. It is the same as the command, "cd ./downloads" when you are in your home folder.
got it!

> **efflandt said:**
> So far you have not hardly typed anything correctly.  Your home dir is not /home, it is **/home/luke**.  Or if you just do **cd** with nothing else you end up in your home directory.  But you are also already in your home directory when you open the terminal.  You can find out what directory you are in with **pwd** command.

The second time you did cd/home you were missing the space in **cd /home**, but that is not "your" home, that is just the directory containing the home directory with your username luke (ie, /home/luke).

Linux is case sensitive.  If you downloaded something with Firefox, it is likely in Downloads, not downloads.  Since ~ represents your home directory, one way to get there if you have no clue where you are would be **cd ~/Downloads** which would be the same as /home/luke/Downloads.

Is that bin file a directory or a file.  If it is a file, there would be no trailing slash.  And it would never have a leading slash unless it is in the root directory / or you included a full path to it.

I really appreciate it, both of you :D I got it working...gosh I am stupid ](*,)

---

### Post by Iowan on 2010-07-06
Congrats! No one was born speaking (typing) Unix/Linux commands. [Here]("https://help.ubuntu.com/9.04/basic-commands/C/") is a list of other command line instructions. If your problem is answered, consider marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"). :)

---

### Post by Jelks on 2013-01-28
im having problems too, i just re installed ubuntu 12.04 and im getting this error when i try and download something



-

[COLOR=red][FONT=monospace][IMG]http://i1337.photobucket.com/albums/o677/Marcellus_j/help_zps14c53800.png[/IMG][/FONT][/COLOR]

---

