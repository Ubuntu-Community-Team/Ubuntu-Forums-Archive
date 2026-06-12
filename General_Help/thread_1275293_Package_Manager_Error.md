---
title: "Package Manager Error"
date: 2009-09-25
forum: General Help
---

### Post by captcadaver on 2009-09-25
So I was trying to install Eclipse for coding using the terminal. There was some sort of failure and the error message is: "Error: BrokenCount > 0". I think there was also a message about insufficient space.

When I try to sudo apt-get install something else, this is what happens:

atl@Liechtenstein:~$ ls
Desktop  Documents  examples.desktop  Music  Pictures  Public  Templates  Videos
atl@Liechtenstein:~$ sudo apt-get install python-django
[sudo] password for atl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  eclipse-gcj: Depends: eclipse-jdt-gcj but it is not going to be installed
               Depends: eclipse-platform-gcj but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
atl@Liechtenstein:~$ 

How can I kill Eclipse (might take too much room) so I can install more stuff?

Also, any tips on space management using the terminal? I was surprised that I'm apparently out of room. I don't know the commands.

---

### Post by Liolikas on 2009-09-25
Really just try 'apt-get -f install'

---

### Post by prem1er on 2009-09-25
```
df -h
```

Will show you how much HD space you have used/remaining.

---

