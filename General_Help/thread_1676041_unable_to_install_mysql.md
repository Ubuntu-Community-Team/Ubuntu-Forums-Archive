---
title: "unable to install mysql"
date: 2011-01-26
forum: General Help
---

### Post by nikhil_me on 2011-01-26
hellooooo!!!!!
i am using ubuntu 10.10 . i am not able to install mysql. it gives message titled functional dependency can not be resolved. anybody have any idea????

---

### Post by Smart Viking on 2011-01-26
Hello.

tl;dr

We need more information.
Post terminal output.

---

### Post by nikhil_me on 2011-01-26
thanx for replying. i typed the command sudo apt-get install mysql-server and the output of terminal is

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mysql-server : Depends: mysql-server-5.1 but it is not going to be installed
E: Broken packages

how can i install mysql???
note: i am using vmware and my system's os is mac os x 10.6

---

### Post by Smart Viking on 2011-01-26
Try
```
sudo apt-get install mysql-server-5.1
```

EDIT: This will probably work, "mysql" is a metapackage depending on the latest version, maybe something was wrong with it.

---

### Post by nikhil_me on 2011-01-26
i tried and got 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mysql-server-5.1 : Depends: mysql-client-5.1 (>= 5.1.49-1ubuntu8.1) but it is not going to be installed
                    Depends: libdbi-perl but it is not installable
                    Recommends: libhtml-template-perl but it is not installable
E: Broken packages

---

### Post by Smart Viking on 2011-01-26
Seems like something is wrong with your package manager to me.

Try
```
sudo apt-get install libdbi-perl mysql-client-5.1 mysql-server-5.1
```

---

### Post by nikhil_me on 2011-01-26
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdbi-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libdbi-perl' has no installation candidate

---

### Post by Smart Viking on 2011-01-26
My ubuntu 10.10 system have libdbi-perl in it's repos, try unchecking all the repos in sources.list and try again.

---

### Post by nikhil_me on 2011-01-26
am i supposed to uncheck all boxes in 
System > Administration > Synaptic Package Manager : >> Settings >> Repositories.
[i am new to ubuntu]

---

### Post by Smart Viking on 2011-01-26
No, to check them, so you get more repositories and more packages available, if it can't download it after that then something is wrong.

---

### Post by nikhil_me on 2011-01-26
sorry couldn't get u .what am i actually suppose to do . am i suppose to go to
  System > Administration > Synaptic Package Manager : >> Settings >> Repositories.

---

### Post by Smart Viking on 2011-01-26
Just run this.
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup && sudo cat /etc/apt/sources.list 's/#deb/deb/g' > /etc/apt/sources.list && sudo apt-get update && sudo apt-get install libdbi-perl mysql-client-5.1 mysql-server-5.1
```

---

### Post by nikhil_me on 2011-01-26
cat: /etc/apt/sources.list: input file is output file
cat: s/#deb/deb/g: No such file or directory

---

### Post by Smart Viking on 2011-01-26
Wow.. made a typo..
Try again.
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup && sudo cat /etc/apt/sources.list | sed 's/#deb/deb/g' > /etc/apt/sources.list && sudo apt-get update && sudo apt-get install libdbi-perl mysql-client-5.1 mysql-server-5.1
```'
I think it's right now.

---

### Post by nikhil_me on 2011-01-26
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libdbi-perl
E: Unable to locate package mysql-client-5.1
E: Couldn't find any package by regex 'mysql-client-5.1'
E: Unable to locate package mysql-server-5.1
E: Couldn't find any package by regex 'mysql-server-5.1'

---

