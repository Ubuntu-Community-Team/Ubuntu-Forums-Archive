---
title: "&quot;cd&quot; is not a utility or what ?"
date: 2011-03-06
forum: General Help
---

### Post by anirudhtomer on 2011-03-06
```
anirudh@anirudh-Aspire-5920:~$ which cd
anirudh@anirudh-Aspire-5920:~$ cd Documents/
anirudh@anirudh-Aspire-5920:~/Documents$ cd ..
anirudh@anirudh-Aspire-5920:~$ sudo cd Documents/
[sudo] password for anirudh: 
sudo: cd: command not found
anirudh@anirudh-Aspire-5920:~$
```

So when I try to locate the command "cd" no output is shown.
Also when I try to enter a directory using "sudo cd" it says that "sudo: cd: command not found"

So it means cd is not a command. Does it mean that "cd Documents" is just parsed by bash and then bash takes the control, rather than "cd" being a utility.

---

### Post by mcduck on 2011-03-06
Yes, "cd" is a built-in functionality of Bash, not an external program.

In case you are interested, here's a list of Bash built-in commands: [http://linux.about.com/library/cmd/blcmdl1_builtin.htm]("http://linux.about.com/library/cmd/blcmdl1_builtin.htm")

---

### Post by jocko on 2011-03-06
> **anirudhtomer said:**
> ```
anirudh@anirudh-Aspire-5920:~$ which cd
anirudh@anirudh-Aspire-5920:~$ cd Documents/
anirudh@anirudh-Aspire-5920:~/Documents$ cd ..
anirudh@anirudh-Aspire-5920:~$ sudo cd Documents/
[sudo] password for anirudh: 
sudo: cd: command not found
anirudh@anirudh-Aspire-5920:~$
```So when I try to locate the command "cd" no output is shown.
Also when I try to enter a directory using "sudo cd" it says that "sudo: cd: command not found"

So it means cd is not a command. Does it mean that "cd Documents" is just parsed by bash and then bash takes the control, rather than "cd" being a utility.
cd is a built-in shell command, not a standalone executable. If you really would need root access to cd to a directory, you need to run the shell as root. Either of these commands will do it:
```
sudo su
sudo -i
sudo -s
sudo bash
```

---

### Post by asmoore82 on 2011-03-06
`cd` is always a shell *builtin*.

The current working directory concept is just a function of a process's *environment*.
In a sense, it's an imaginary concept in that no real program can physically
move you to a new working directory &#8212; that would require the program to
change the calling environment of the parent process that created it.

---

### Post by anirudhtomer on 2011-03-06
thanks a lot jocko,asmoore82 and mcduck.

---

