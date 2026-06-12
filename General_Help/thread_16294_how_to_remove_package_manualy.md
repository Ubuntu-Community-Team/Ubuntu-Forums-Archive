---
title: "how to remove package manualy"
date: 2005-02-20
forum: General Help
---

### Post by valter on 2005-02-20
Hi everybody, I am new to Ubuntu (new to Great Linux world also) and this is my first post in this forum.

My problem is that I installed a java (sdk) 1.42 from repositor [ftp://neacm.fe.up.pt/pub/ubuntu-java/](ftp://neacm.fe.up.pt/pub/ubuntu-java/) whith synaptic and i can't remove it - says: 

Removing sun-j2sdk1.4.2 ...
rm: cannot remove `/usr/bin/idlj': No such file or directory
dpkg: error processing sun-j2sdk1.4.2 (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 sun-j2sdk1.4.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
I think i have installed a package that is not right to Ubuntu and now I don't know a way to remove it. Can somebody wiser help me?

---

### Post by kassetra on 2005-02-20
Ok, it looks like that package was most likely converted from another package ... so you need to setup some stuff before it will remove correctly (I'm pretty sure)
 
 So try this:
 1. Exit from Synaptic.
 2. Open a terminal: Applications->System Tools->Terminal
 3. Type in the following command:
  ```
sudo ln -s /usr/lib/java/sun-j2se1.4-sdk/bin/idlj /usr/bin/idlj
``` 
 4. restart Synaptic. 
 5. try to remove the package again.
 
 Let me know if that works.

---

### Post by valter on 2005-02-20
thanks, almost helped - there was more such files that it didn't find and I wrote : 

sudo ln -s /usr/lib/sun-j2sdk1.4.2/bin/* /usr/bin

Somehow still an error, says: 

Removing sun-j2sdk1.4.2 ...
rm: cannot remove `/usr/bin/policytool': No such file or directory
dpkg: error processing sun-j2sdk1.4.2 (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 sun-j2sdk1.4.2
E: Sub-process /usr/bin/dpkg returned an error code (1)

I looked the policytool link was in /usr/bin folder - strange
Any suggestions?

---

### Post by kassetra on 2005-02-20
Ok, I need some more information here, 
 type this in a terminal window:
  ```
sudo dpkg -l sun-j2sdk1.4.2
``` 
 
 and then tell me what it says.

---

### Post by valter on 2005-02-21
[QUOTE=kassetra]Ok, I need some more information here, 
 type this in a terminal window:
  ```
sudo dpkg -l sun-j2sdk1.4.2
``` 
 
 and then tell me what it says.[/QUOTE]
 Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ri  sun-j2sdk1.4.2 07-1           Complete Java(TM) 2 Development Kit

Sorry that it took so long

---

### Post by kassetra on 2005-02-22
[QUOTE=valter]Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ri  sun-j2sdk1.4.2 07-1           Complete Java(TM) 2 Development Kit

Sorry that it took so long[/QUOTE]

no worries!
ok, what happens if you type:
 ```
sudo aptitude purge sun-j2sdk1.4.2
``` 

(I know it will most likely give you an error, but I want to see if it gives you a different error... I'm hoping it's not what I think it is!!)

---

### Post by valter on 2005-02-23
```
Reading Package Lists... Done
Building Dependency Tree
Reading extended state information
Initializing package states... Done
The following packages will be REMOVED:
  sun-j2sdk1.4.2
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 97.4MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 66182 files and directories currently installed.)
Removing sun-j2sdk1.4.2 ...
rm: cannot remove `/usr/bin/idlj': No such file or directory
dpkg: error processing sun-j2sdk1.4.2 (--purge):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 sun-j2sdk1.4.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ack!  Something bad happened while installing packages.  Trying to recover:
Reading Package Lists... Done
Building Dependency Tree
Reading extended state information
Initializing package states... Done
``` 
 :|

---

### Post by valter on 2005-02-27
Someone  [-o<

---

### Post by valter on 2005-03-05
[QUOTE=valter]Someone  [-o<[/QUOTE]
 The repositor updated the package and no problem now

Thanx Kassetra

---

### Post by kassetra on 2005-03-05
[QUOTE=valter]The repositor updated the package and no problem now

Thanx Kassetra[/QUOTE]

You're welcome.  Sorry it took so long to get things fixed.
And yes, it was exactly what I thought it was (slightly mungled), which is why the upgraded package fixed it.  I'm so happy it's fixed for you now!

---

