---
title: "Rar and Wine installation issue on ubuntu 9.10"
date: 2010-04-15
forum: General Help
---

### Post by cancer10 on 2010-04-15
HI

Today i installed ubuntu 9.10 on my friend's lappy, I was going to install rar using this command 


```
sudo apt-get install rar
```

But getting this error

```

rabb@rabb-laptop:~$ sudo apt-get install rar
Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: Couldn't find package rar
```


I was also unable to install wine, pls check the error below:

```
rabb@rabb-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages
rabb@rabb-laptop:~$ 
```



I made sure all the checkboxes under the Software Sources are checked. So what may be the issue.

I have ubuntu 9.04 on my personal pc and everything works fine there.

Please helpe me resolve these issues.


Thanks

---

### Post by prodigy_ on 2010-04-15
First of all, do ```
sudo apt-get update
``` and see if all repositories can be reached.

---

