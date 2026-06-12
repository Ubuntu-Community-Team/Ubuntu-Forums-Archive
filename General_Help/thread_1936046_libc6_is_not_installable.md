---
title: "libc6 is not installable"
date: 2012-03-05
forum: General Help
---

### Post by elliotn on 2012-03-05
I am trying to install libc6 using Gdebi but its not installable, the install button is greyed out, Gdebi doesn't show any error at all or unmet dependencies.

when I use the command 

sudo dpkg -i libc6.deb the system get broken.

I have downloaded it 4 times from packages.ubuntu.com 


any ideas

---

### Post by elliotn on 2012-03-05
bumping desperate for answer

---

### Post by elliotn on 2012-03-06
help needed here

---

### Post by matt_symes on 2012-03-06
Hi

libc6 should be installed by default in Linux. It's integral to the operation of your system.

```
matthew@matthew-Aspire-7540:~$ dpkg -l | grep libc6
ii  libc6                                                       2.15-0ubuntu4                                    Embedded GNU C Library: Shared libraries
ii  libc6:i386                                                  2.15-0ubuntu4                                    Embedded GNU C Library: Shared libraries
ii  libc6-dev                                                   2.15-0ubuntu4                                    Embedded GNU C Library: Development Libraries and Header Files
matthew@matthew-Aspire-7540:~$ 
```

Why are you trying to install it ? Has you installed software that is trying to reference it but cannot find it ? If so then create a symlink.

Kind regards

---

### Post by raja.genupula on 2012-03-06
hi please give us the terminal output of what you did and what you got , that can help us to understand your problem  . 

one more thing is you please do this in terminal 
```
sudo apt-get install -f
```  

let us know what you got . thank you .

---

