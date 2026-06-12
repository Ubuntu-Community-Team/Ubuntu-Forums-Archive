---
title: "How do I add a new BASH command?"
date: 2012-02-25
forum: General Help
---

### Post by Orcris on 2012-02-25
For example, if I want to make the command foo launch /usr/local/foo, how would I make this work? I'm pretty sure I have to modify my .bashrc, but how do I do it?

---

### Post by imachavel on 2012-02-25
[http://justlinux.com/forum/archive/index.php/t-63262.html](http://justlinux.com/forum/archive/index.php/t-63262.html)

so you want to modify the tags then?? I hope you've done something very similar before, linux is the opposite of windows. Windows = more gui stable. Linux = more terminal interface stable. Once you modify that, if you can't modify it back, then if god can help you, let me know I'm going to ask him for some help ):P

---

### Post by Bonster on 2012-02-25
add something like this to ur bashrc

> alias foo='xdg-open /usr/local/abcd'

---

### Post by whatthefunk on 2012-02-26
> **Orcris said:**
> For example, if I want to make the command foo launch /usr/local/foo, how would I make this work? I'm pretty sure I have to modify my .bashrc, but how do I do it?

To edit your bashrc file, go to a terminal and do this in your home directory:
```
sudo nano .bashrc
```

That will call up the basic nano editer.  Scroll down to the bottom of the file and youll find aliases and you can add your command there.  To save and exit, hit control + x.

---

### Post by The Cog on 2012-02-26
It might be easier to simply put foo in /usr/local/bin instead, where your normal command search will find it. To see which directories are searched for a command when you enter it, use the command:
**echo $PATH**

---

### Post by auroraa9420 on 2012-02-26
i think this only works for binary files and probably with sh and other scripts

just put the file in /bin/ and it should do the trick

---

### Post by efflandt on 2012-02-26
Personal scripts or binaries can be put in a **bin** directory you create in your home directory (ie, ~/bin).  The next time you login (or if you log out and log back in) that personal bin directory will automatically be in your $PATH so you can call the script or binary by name.

If it needs certain parameters always set or something set in the ENV it would be best to put a script to launch it in your ~/bin.

Otherwise if it is a system wide command (program or script), as mentioned, use sudo to put it in one of the system bin directories that would automatically be in your $PATH.

---

