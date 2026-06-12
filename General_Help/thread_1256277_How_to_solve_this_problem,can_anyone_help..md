---
title: "How to solve this problem,can anyone help."
date: 2009-09-02
forum: General Help
---

### Post by Josa on 2009-09-02
when i try to update tihis message appers what should I do...
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
Can someone help me please.I am newbies in ubuntu stuffs............:confused:
Please explain step by step

---

### Post by sisco311 on 2009-09-02
Hi and welcome to the forums!

Open a terminal (Applications -> Accessories -> Terminal)
and type:
```
sudo dpkg --configure -a
```

---

### Post by Josa on 2009-09-02
> **sisco311 said:**
> Hi and welcome to the forums!

Open a terminal (Applications -> Accessories -> Terminal)
and type:
```
sudo dpkg --configure -a
```

Already done.
josa@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for josa: 
Setting up java-common (0.30ubuntu4) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
josa@ubuntu:~$ E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
bash: E:: command not found
josa@ubuntu:~$ E: _cache->open() failed, please report.
bash: syntax error near unexpected token `('
josa@ubuntu:~$ 


This is what written in the terminal.Is it ok for all....
Anyway Thanks sisco311

---

