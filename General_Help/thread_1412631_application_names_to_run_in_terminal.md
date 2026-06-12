---
title: "application names to run in terminal"
date: 2010-02-21
forum: General Help
---

### Post by dpwilson on 2010-02-21
I have two quick questions:

1) What is the easiest way to find an applications name so that I can run it in terminal rather than from the apps menu?  I have installed programs before and tried to run them using the terminal and couldnt for not knowing the name to put in terminal

2) Does Clam AV automatically update when update manager is run?  I sometimes get an "update failed" message when I try to run it from the GUI.

Thanks

---

### Post by rnerwein on 2010-02-21
hi
1. at end of your ~/.bashrc   ( i assume you are using /bin/bash as your login shell )
    insert following line: PATH=~/bin:$PATH
    export PATH
2. create a directory ~/bin
3. install (or move if they are already installed to your ~/bin
4. open a new terminal to activate your new PATH setting ( or type in the terminal: . ~/.bashrc
5. cd ~/bin
6. type the first character of the command you are looking for ( hope you know at minimum the first   character of it) and hit TAB twice. (e.g. you got a command: my_script and you type: 
 m TAB TAB  --> you get: my_script
have fun
ciao

---

### Post by mechro on 2010-02-21
If it's in the apps menu right-click the main menu button, select Edit Menus, find the application, right-click and select Properties.

---

### Post by dpwilson on 2010-02-21
Thanks, that helps a lot.

---

### Post by gadolinio on 2010-02-21
> **mechro said:**
> if it's in the apps menu right-click the main menu button, select edit menus, find the application, right-click and select properties.

+1

---

### Post by 3rdalbum on 2010-02-21
If there's no icon in the Applications menu, then you can always check the contents of the package - see the screencast in my signature for more details.

ClamAV's update mechanism is different. Assuming you're using KlamAV as the front-end, you need to start it as root ("gksudo klamav" in the terminal) and then update the definitions. Linux doesn't get viruses anyway, so unless you're specifically checking for Windows viruses you won't need Clam anyway.

---

### Post by d3v1150m471c on 2010-02-21
> **3rdalbum said:**
> Linux doesn't get viruses anyway, so unless you're specifically checking for Windows viruses you won't need Clam anyway.

Linux can get viruses. I don't mean this to be offensive but we shouldn't go around telling people linux is virus free and then wind up like macintosh. Linux viruses are far and few but they are out there. IE: Bliss A and Bliss B to name two. Best thing you can do as the user is only use trusted sources and never give unknown executable files root privileges.

---

### Post by jenaniston on 2010-02-21
> **mechro said:**
> If it's in the apps menu right-click the main menu button, select Edit Menus, find the application, right-click and select Properties.

That's niiiice . . .
 I have searched in the directory /usr/bin looking for command names  . . . uggh.

---

### Post by dpwilson on 2010-02-26
> Linux doesn't get viruses anyway, so unless you're specifically checking for Windows viruses you won't need Clam anyway

I am not so worried about getting a virus as I am sending one out or downloading an infected file at home and taking it to work on stick and causing problems there.  Although there antivirus should catch it, I don't want to take that risk.  Thanks for the info on how to update 


> I have searched in the directory /usr/bin looking for command names . . . uggh.

I hear your uggh and that's why I wanted to post that question.  I did the same thing.;)

---

