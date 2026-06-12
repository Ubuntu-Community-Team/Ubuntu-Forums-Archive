---
title: "NewB Qs - How to make the c-shell integrated in my terminal + File Sharing"
date: 2009-11-21
forum: General Help
---

### Post by IceMan68 on 2009-11-21
Hi everybody! This is my first post in the forum and my first day with ubuntu :)

I installed the c-shell (with the apt-get install csh command) and now if I want to use
the c-shell (c-shell is all I use right now- for studying) I have to write "csh" in the
terminal and get in the c-shell environment. I remember seeing in my friend's
computer (that runs ubuntu as well) that he can type csh commands right away
when opening the terminal.

Anyone know how can I do so?

Plus, I wanted to know if I can open a remote directory that's on another computer
in my LAN network. In windows I do "\\computerName\C$" then I put the comp's
password and I can travel in the directories as if it's on mine... I don't want to use
the folder sharing method...
How do I do so in Ubuntu?

Thanks a lot guys!

---

### Post by blazemore on 2009-11-21
To change your shell in Ubuntu, you need to edit the passwd file:
```
sudo nano /etc/passwd
```

Find the line that looks like this
> foo : x:1001:1001::/home/foo:/bin/sh

And change it to this
> foo : x:1001:1001::/home/foo:/bin/csh

Save (Ctrl + O, then Enter) and quit (Ctrl + X)

---

### Post by IceMan68 on 2009-11-21
thanks but I don't have this line:
foo : x:1001:1001::/home/foo:/bin/sh 			 		

I have around 20-30 others but not this one.

I am running the latest version of ubuntu (downloaded 5 days ago)

---

### Post by blazemore on 2009-11-21
Are you sure? It's usually the last one. My username is "james" so mine looks like
```
james:x:1000:1000:James Holland,,,:/home/james:/bin/bash
```

---

### Post by louieb on 2009-11-21
I use zsh.  
To change your shell in all the right places run
```
chsh
```> I can open a remote directory that's on another computer in my LAN network. Depends on what servers are installed and the OS of the host machine. Theres sshfs, cifs, nfs,  and probably a few other ways. 

Most are used in a similar way to manually mounting a partition on the same computer. 
1st you create a directory .  
then you mount your share 
nfs example Linux server and client
```
sudo mount whitebox:/media/stuff /media/wbstuff
```cifs example XP server Linux client
```
sudo mount -t cifs //blackbox/bb2 /media/bb2 -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
```Search the [Tutorials & Tips]("http://ubuntuforums.org/forumdisplay.php?f=100") section - for examples that fit your paricular situation.

---

### Post by IceMan68 on 2009-11-21
Thanks! the chsh did say that it changed from default /bin/bash to /bin/csh but i still can't perform
c-shell commands like set.

when I open the terminal and write :
"set x=wordssss
echo $x"
It just writs to the console an empty line but when I write "csh" (enter) and then those commands
it does writes to the console "wordssss".

How come? Is there a way to make it work?...

---

### Post by louieb on 2009-11-21
log out and log back on

---

### Post by IceMan68 on 2009-11-21
Thanks bro! it works now :)
though, :-\ every time one thing is fixed another is broken haha
is there a way for me to enable the up-key button to retype the last command?
when I press the up key it writes ^[[A haha

---

### Post by IceMan68 on 2009-11-21
anyone?...

---

