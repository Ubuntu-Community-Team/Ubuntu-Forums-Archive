---
title: "A few cmd questions.."
date: 2009-10-25
forum: General Help
---

### Post by HAMON on 2009-10-25
Hello everyone,

A few quick questions for a linux newbie.

1 - How to I check what process is running on what port?
2 - How to I check is a process is running?

Thank You everyone

---

### Post by renkinjutsu on 2009-10-25
just a quick reply that may be useful (until someone smarter comes along)

to check what applications are using what ports, you can probably use ```
netstat
```
also, to check running processes, use ```
ps
``` you may have to read up on these

---

### Post by falconindy on 2009-10-25
`netstat -np --inet` will show any program (PID and name) that has a port open to the internet.

`ps aux | grep <prog_name>` to show if a program is running. the program name you search for doesn't have to be the whole thing. 'pidg' will find 'pidgin'.

---

### Post by mr_steve on 2009-10-25
If you want to know the actual process name that's using a specific port, try:
```
sudo netstat -tap
```To see a list of all running processes, not just the ones running under your user ID, do:
```
ps -A
```

I also recommend the program **htop** for an easy interactive list of processes. It's like the **top** command that comes pre-installed, only with color and an easier interface. If you wanna try it just:
```
sudo apt-get install htop
```

---

### Post by HAMON on 2009-10-26
netstat -np --inet

Does not seem todo anything?

btw great help so frar thank you

do the same commands work in Unix?

---

### Post by falconindy on 2009-10-28
> **HAMON said:**
> netstat -np --inet

Does not seem todo anything?

btw great help so frar thank you

do the same commands work in Unix?
Hmm, apologies. I assumed Arch used the same version of netstat as Ubuntu.

As to whether or not it will work in Unix... if a program is POSIX compliant, it will work in Unix. Beyond that its a crapshoot.

---

