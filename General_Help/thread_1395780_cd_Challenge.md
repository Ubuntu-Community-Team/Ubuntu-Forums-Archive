---
title: "cd Challenge"
date: 2010-02-01
forum: General Help
---

### Post by siohwito on 2010-02-01
[SIZE=2][B]Beginner with Ubuntu, yes; not new to command line though. However, I am struggling to change directories in terminal even when following the instructions and examples from this link: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Every time I try to change directories, mainly to the Downloads folder within my profile or a mounted volume, I receive the a message that the path is invalid or does not exist. I have tried the full path all at once and one directory at a time. I know it is a user error, but if someone could please point me in the right direction, I would greatly appreciate it.[/B][/SIZE]

---

### Post by skymera on 2010-02-01
If you want to change directories to Downloads then do

```
 cd ~/Downloads 
```

~/ indicates that it's your home folder, alternatively use

```
 cd /home/USER/Downloads
cd /home/USER/Desktop 
```

It'S CaSE SeNSiTiVE :)

If you are unsure, press the TAB key to auto-complete directories

---

### Post by MelDJ on 2010-02-01
firstly, post the path you are typing.
it should be ```
cd /home/user/Downloads
```

---

### Post by audiomick on 2010-02-01
When I have that sort of problem, I resort to using "ls" to see where I am and to look for the exact name of the next step. It is cumbersome, but has helped me lots of times.

```
ls
```
generates a list of the contents of the directory you are in
```
cd *name*
```
to move along a step
```
ls
```
to have another look

---

### Post by whiskeylover on 2010-02-01
Type ```
pwd
``` to see your current directory.

---

### Post by siohwito on 2010-02-01
[SIZE=2][B]Thanks for all the advice, first of all!

The command with path I was typing in terminal was:
cd /home/user/Downloads

I did try the changing the case to match only to get the same result. However, the suggestion that skymera posted about using the tildemark (~) worked. But I do not understand why using the fully qualified path does not work. 
[/B][/SIZE]

---

### Post by whiskeylover on 2010-02-01
Did you substitute "user" with your actual username?

---

### Post by siohwito on 2010-02-01
**[SIZE=2]I sure did and I left the any key alone as well.[/SIZE]** :)

---

### Post by whiskeylover on 2010-02-01
Type ```
cd /ho 
```and press the TAB key a couple of times. It should autocomplete to ```
cd /home 
```Then press the TAB key again a couple of times. It should give you all folders under /home. See if what you're typing matches the folder name under /home.

Alternatively, type ```
cd ~ 
```and then ```
pwd
```. Copy the contents of pwd and try a ```
cd 
```on that.

---

### Post by todak on 2010-02-01
If you are in your home folder, simply type ```
cd Downloads
``` and it will take you there. Here is my terminal output: ```
dave@dave-desktop:~$ cd Downloads
dave@dave-desktop:~/Downloads$ 

``` But if I want to get back to my home directory from any folder I am currently viewing, I just type ```
cd
``` and it will take me back to home folder.

---

### Post by siohwito on 2010-02-01
**[SIZE=2]Using the tab in terminal is a nice feature and it helped. Now I do not feel stuck anymore. Thanks to all that replied![/SIZE]**

---

