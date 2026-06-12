---
title: "installing CAPT driver (gs-esp dependency)"
date: 2011-05-17
forum: General Help
---

### Post by ayeritsian on 2011-05-17
Hello,
I am new in linux.
I want to install a canon printer driver.
When I type in console 
sudo dpkg -i cndrvcups-common_2.20-1_i386.deb

it will print

dpkg: dependency problems prevent configuration of cndrvcups-common:
 cndrvcups-common depends on gs-esp; however:
  Package gs-esp is not installed.

Thanks for your answers.

---

### Post by enimeizoo on 2011-05-17
That means the driver you want to install needs another package to work. ("gs-esp")

You can try to install it from the standard repositories with the command :
```
sudo apt-get install gs-esp
```
If that worked, you should be able to install your driver with your command.
As a general rule, when you search a package, one of the firsts place to search is that one.
```
sudo apt-get install [package]
```

---

### Post by Baldone on 2011-11-11
Hi, I cannot get that gs-esp from anywhere. When i try your way it gives me: 

derekmax@derekmax-G41T-M13:~$ sudo apt-get install gs-esp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gs-esp is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gs-esp' has no installation candidate

Where can one obtain this package from?
Its all to connect a Canon MF4400 series printer which looks more and more impossible to me.....

---

