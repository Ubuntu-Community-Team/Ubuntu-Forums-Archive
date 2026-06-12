---
title: "Problem running script"
date: 2009-09-23
forum: General Help
---

### Post by A_randomguy on 2009-09-23
Hi.  I'm new to the forum and pretty new to ubuntu.  I have 9.04 (64-bit) installed.  I've used this OS sporadically for Internet, word processing, etc and now I'm starting to get into some heavier stuff.

I'm trying to install a Fortran compiler but am getting an error message.  I've unzipped the install packages into a temporary folder, and I'm following the install instructions provided by the software producer.  can you tell me why this won't work?


```
pete@pete-desktop:~/Temp$ ls
fl22.tar  fll6i22dcl.tar  in.html  install.sh  mk22_doc.tar  un.html
pete@pete-desktop:~/Temp$ ./install.sh
bash: ./install.sh: Permission denied
pete@pete-desktop:~/Temp$ sudo ./install.sh
[sudo] password for pete: 
sudo: ./install.sh: command not found
pete@pete-desktop:~/Temp$ 
```

---

### Post by DaithiF on 2009-09-23
Hi, make the script executable first, then try running it:
```
chmod +x install.sh
```

---

### Post by A_randomguy on 2009-09-23
Thanks for the quick reply -- that worked.  I'll have to read up on this.

---

