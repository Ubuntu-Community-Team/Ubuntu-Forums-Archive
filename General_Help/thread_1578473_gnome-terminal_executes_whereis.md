---
title: "gnome-terminal executes whereis"
date: 2010-09-20
forum: General Help
---

### Post by cjaramilu on 2010-09-20
When I open a terminal it doesn't show the usual prompt because it is running 
the command "whereis python" which BTW doesn't finish. 
How can I eliminate that other than entering Ctrl-C every time?

---

### Post by papibe on 2010-09-20
It looks like the shell is being called with parameters.

If you're calling your own icon (not the one in Applications -> Accessories -> Terminal):
[INDENT]Right click on the icon.
Select Properties.
The command field should say "gnome-terminal". If there's more in that field delete it (like "-e ...").
[/INDENT]

If it is the one on the menu:

[INDENT]Right click on the Ubuntu symbol (upper right, in the panel).
Select Edit Mens.
In the right column select Applications, and then Accessories.
Go to the left column and look for "Terminal".
Follow the procedure above (it should just say gnome-terminal)
[/INDENT]

Good Luck.

---

### Post by cjaramilu on 2010-09-20
I use the Application menu and the command for Terminal is 
just "gnome-terminal". I was wondering if "whereis python" is
an implicit thing  and for some reason it hangs, because when I 
enter "whereis python" it hangs too.

---

### Post by papibe on 2010-09-20
By any chance did you customize your bashrc?

There's 2 places where you can preset things up for bash: ~/.bashrc and /etc/bash.bashrc

Check if there's any reference to whereis or python in those files.

Regards.

---

### Post by cjaramilu on 2010-09-20
~/.bashrc and /etc/bash.bashrc are in their original state
and without the word "whereis"

---

### Post by papibe on 2010-09-20
OK, there's 2 things going on here: the auto-executing of a command, and the weird behavior of "whereis". First let's try to separate bash from gnome-terminal.

what happens when yu call bash inside the gnome-terminal?
```
$ bash
```
Does it call "whereis python"?, if it does, then it is actually a bash problem and it has to do one of their config files:
```

      /bin/bash
              The bash executable
       /etc/profile
              The systemwide initialization file, executed for login shells
       /etc/bash.bashrc
              The systemwide per-interactive-shell startup file
       /etc/bash.bash.logout
              The systemwide login shell cleanup file, executed when  a  login
              shell exits
       ~/.bash_profile
              The personal initialization file, executed for login shells
       ~/.bashrc
              The individual per-interactive-shell startup file
       ~/.bash_logout
              The  individual  login shell cleanup file, executed when a login
              shell exits
       ~/.inputrc
              Individual readline initialization file

```

---

### Post by cjaramilu on 2010-09-20
Yes, the problem is in /bin/bash.

I enter 
grep whereis /etc/bash* /etc/prof* ~/.bash* ~/.inpu*
and the only "whereis" I get is in
~/.bash_history

I have examined the process "whereis" and it opens 149 files
but must of them are the same file (directory)  "/opt"... and it is 
also using a lot of cpu.

---

### Post by papibe on 2010-09-20
I'm really puzzled. If were you, I'd try brute force.

One bash config file after another I would:
```
$ mv .bashrc .bashrc.old
$ bash
$ mv .bashrc.old .bashrc
```

If you stop getting the error after one of the tries, then you have the file that is producing the error. You'd have to use sudo for the files at /etc. Be VERY careful with mv because it can overwrite the destiny.

---

### Post by junapp on 2010-09-20
I wonder if when you do find the solution you could post it here. 

This fellow was having a somewhat similar issue - some command running when he started the terminal.
[http://ubuntuforums.org/showthread.php?t=1564489](http://ubuntuforums.org/showthread.php?t=1564489)

---

### Post by cjaramilu on 2010-09-20
I narrowed the problem to /etc/bash_completion which is
called from  ~/.bashrc

---

### Post by papibe on 2010-09-20
If you want us to take a look at them. Post'em here (or better use [pastebin.com]("pastebin.com")).

---

### Post by cjaramilu on 2010-09-20
I found the "whereis python" in 
/etc/bash_completion.d/django_bash_completion
and confirmed that it really runs when starting bash.

So the problem is /usr/bin/whereis.

I reistalled the package util-linux which has the
program /usr/bin/whereis, but the problem persists.

---

### Post by papibe on 2010-09-21
Ok, at least we're narrowing the problem.

'whereis' looks for files in:
```
/{bin,sbin,etc}

/usr/{lib,bin,old,new,local,games,include,etc,src,man,sbin,X386,TeX,g++-include}

/usr/local/{X386,TeX,X11,include,lib,man,etc,bin,games,emacs}

```

Is any of those directories either not mounted, or a network share (smb or nfs)?

Also, Does whereis hangs only on python, or others searches too?

---

### Post by cjaramilu on 2010-09-21
"whereis <anything>" hangs always 
and I am not using network shares.

---

### Post by mc4man on 2010-09-21
A couple of  'curious' things from your posts, may mean nothing but thought worth mentioning.
> 
I have examined the process "whereis" and it opens 149 files
but must of them are the same file (directory) "/opt"... and it is
also using a lot of cpu. 

By default there is nothing in /opt - what do you have?

> I found the "whereis python" in
/etc/bash_completion.d/django_bash_completion

Have never seen django bash completion in any install here

---

### Post by cjaramilu on 2010-09-21
I have a big file system for all my files in /opt... 
it makes my life simpler if I have to make a clean install or move to another machine. 

I uninstalled python-django and bash start well... 
"whereis" still hangs if I run it manually.

I was wondering if my /opt has some type of circular reference.

---

### Post by papibe on 2010-09-21
> I was wondering if my /opt has some type of circular reference

Hard to say, but your use of /opt is unusual. I also have 2 file systems one mounted on / for the OS, and the big one for my files mounted on /home.

Have you try a manual search to see if it gets into a loop too?
```
$ ls /usr/bin/python
/usr/bin/python
$ sudo find / -iname python

```
So assuming python is in /usr/bin, you should be able to 'find it' using find. You'll know if something is wrong, if (1) it doesn't get found, or (2) even if found, the command find gets into a loop (not ending).

Regards.

---

### Post by cjaramilu on 2010-09-21
the command "find" works fine

---

