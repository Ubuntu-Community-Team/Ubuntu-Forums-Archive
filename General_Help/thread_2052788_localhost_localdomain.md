---
title: "localhost localdomain"
date: 2012-09-04
forum: General Help
---

### Post by cigtoxdoc on 2012-09-04
i forgot my password and had to go into root by using recovery mode on boot and reset my password.  Now instead of my pc being called a600n it calls itself localhost.localdomain.  How do i fix this?

OS= 12.04 32-bit

john

---

### Post by duncan12 on 2012-09-04
What is the output of:

```
cat /etc/hostname
```

---

### Post by cigtoxdoc on 2012-09-04
john@localhost:~$ cat /etc/hostname
localhost.localdomain

---

### Post by NikTh on 2012-09-04
Hello , 
you can change the names is two files . 

1st , the file that @ducan12 mentioned 

2nd , the file /etc/hosts. 

Be careful to write the SAME name exactly. 

e.g : 

I want to change the name of computer to MyComputer.  

I do 

```
gksudo gedit /etc/hostname
``` 
and write 
```
MyComputer
``` 

Then I do 
```
gksudo gedit /etc/hosts
``` 

and change the 2nd line next to 127.0.1.1 (the first line is localhost) with MyComputer . 
So the contents of the file /etc/hosts will be 
```
127.0.0.1    localhost
**127.0.1.1    MyComputer**

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
``` 

Reboot for the changes take effect. 

Thanks

---

