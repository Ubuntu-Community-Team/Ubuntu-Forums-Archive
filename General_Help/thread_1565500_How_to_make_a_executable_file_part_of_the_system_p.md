---
title: "How to make a executable file part of the system path"
date: 2010-09-01
forum: General Help
---

### Post by Ghost_Mazal on 2010-09-01
Morning all , not sure how to put this. I have a .sh executable script I use for video encoding. I want the system to be able to see it no matter where in which folder I am. I want to be able to execute that script in terminal in any folder. How can I make it part of the system path. ? Don't know if my wording is right but I think you guys know what I mean.
 
Thanx

---

### Post by Chronon on 2010-09-01
I don't quite understand.  If you want to be able to execute it anywhere then why not put it somewhere that is in your path or else add the desired location to the path variable?

---

### Post by sarin_cv on 2010-09-01
I think you can put that in .bashrc file in ur home directory. 

eg: 
open .bashrc. Add the following line at the end of the file.
PATH=$PATH:/path_of_your_exe
export PATH

---

### Post by Vishnu V on 2010-09-01
try to copy the file in
```

~/.gnome2/nautilus-scripts

```
the scripts under this directory will be available in scripts menu(right click)
and it will be available only to your login

---

### Post by sarin_cv on 2010-09-01
It will also work if you add an alias for your exe in ~/.bash_aliases I guess... not sure...

add the following line in ~/.bash_aliases and try if the above method doesn't work.

alias exename="path_of_your_exe/exename"

---

### Post by Ghost_Mazal on 2010-09-01
> **Chronon said:**
> I don't quite understand. If you want to be able to execute it anywhere then why not put it somewhere that is in your path or else add the desired location to the path variable?
 
I don't know how to do that.

---

### Post by Ghost_Mazal on 2010-09-01
> **sarin_cv said:**
> I think you can put that in .bashrc file in ur home directory. 
 
eg: 
open .bashrc. Add the following line at the end of the file.
PATH=$PATH:/path_of_your_exe
export PATH
 
I went for this first and it works 100% 
 
Thank you all :)

---

### Post by Ginsu543 on 2010-09-01
Just FYI, what Chronon was referring to was that you could have copied your executable file to the /usr/bin folder. Then your file would have been executable from anywhere.

---

### Post by niteshifter on 2010-09-01
Hi,

Start terminal and:
```
cd ~
mkdir bin

```
The first command makes sure you are in your home folder. The second creates a folder named bin there.

Next step: reboot or log out and back in. That bin folder just created will automatically be appended to $PATH (done by reading your .profile file upon login).

Put your executables there, in your bin folder.

Just dropping stuff into /usr/bin is not recommended. Can disappear by updates (rare) or by upgrades (virtually guaranteed) or get clonked by stuff from non-official-blessed-n-sanctioned repositories.

Bonus: When you back up your home folder (we all do that, right? Often, right?) your exe's that you slaved over get backed up also.

---

### Post by Ghost_Mazal on 2010-09-01
Nice tips thanx guys. I'm learning a lot :) That's what I like about Linux , you keep on learning and it's so configurable once you know how :)

---

### Post by Ginsu543 on 2010-09-01
Niteshifter, thanks for the tip. Does the folder have to be named "bin"? Or can it be named "Bin" or ".bin" (to make it hidden)?

---

### Post by niteshifter on 2010-09-02
> **Ginsu543 said:**
> Niteshifter, thanks for the tip. Does the folder have to be named "bin"? Or can it be named "Bin" or ".bin" (to make it hidden)?

With the "stock" .profile file (located in your home folder), yes it must be named bin.

Welcome to Linux: This can be easily changed if you like. Here's how:

First lets look at the stock / default .profile file:

```
dlk@dlk-lt-1420:~$ cat .profile
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f ~/.bashrc ]; then
	. ~/.bashrc
    fi
fi

[B]# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
[/B]dlk@dlk-lt-1420:~$ 

```
I've marked with bold text the part that applies. We need to make two changes:
```
if [ -d ~/bin ] ; then
```
and
```
PATH=~/bin:"${PATH}"
```
So, open Gedit (the text editor). Note that when you select Open File from Gedit's menu it may not show the .profile file (it's "hidden"), pressing Ctrl+H toggles view hidden files on/off on file open windows.

Next, change those two occurrences of "bin" to whatever folder name you like (Bin, .bin, .mysecretexes ;) ). 

Save the file.

Log out and back in or reboot for the change to be effective.

---

### Post by Ginsu543 on 2010-09-06
Perfect! This is exactly the kind of learning experience I love with Linux. Thanks for the heads up. :)

---

### Post by d3v1150m471c on 2010-09-06
```

sudo cp script.sh /usr/bin/script
sudo chmod +x /usr/bin/script

```

now you can launch the script simply by typing the name of it.

---

