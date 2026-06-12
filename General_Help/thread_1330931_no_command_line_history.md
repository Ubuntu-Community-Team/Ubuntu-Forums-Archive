---
title: "no command line history"
date: 2009-11-18
forum: General Help
---

### Post by maity on 2009-11-18
When I am using the Terminal as a user (non root), I don't get any command line history after I closed the Terminal and open it again! How can I enable to show me my last commands from previous sessions?

---

### Post by MonoDeem on 2009-11-18
```
cat ~/.bash_history | less
```

---

### Post by dcstar on 2009-11-18
> **MonoDeem said:**
> ```
cat ~/.bash_history | less
```

Or press the Up Arrow key.

---

### Post by maity on 2009-11-23
If I am root, I get all last commands with the up arrow key, everything is fine. But as a user, there is nothing there anymore after I close and reopen the Terminal. ???

---

### Post by alphaniner on 2009-11-23
Maybe your bash_history file somehow got owned by root.  Run

```
ls -la ~/.bash_history
```

---

### Post by maity on 2009-11-23
Yep! I just had the same thought!

ls -la ~/.bash_history 

and got

-rwxr-x--x 1 root root 8292 2009-11-23 13:37 /home/current user/.bash_history

I did: 
sudo chmod 777 /home/current user/.bash_history

and everything works like charm now!

Maybe somehow during installation, .bash_history became only writable by root? I saw some other blogs where people report the same problem.

---

### Post by alphaniner on 2009-11-23
Did you ever use **sudo -s** to become root?  That could have caused it.

Edit: also, you should mark your thread Solved.  Look for 'Thread Tools' above the first post on each page, on the right side.

---

### Post by maity on 2009-11-24
I usually do "sudo bash"

is there a difference between "sudo bash" and "sudo -s" ?

---

### Post by dcstar on 2009-11-25
> **maity said:**
> I usually do "sudo bash"

is there a difference between "sudo bash" and "sudo -s" ?

This launcher string starts a root terminal:

```
gnome-terminal -e "sudo -i"
```

---

