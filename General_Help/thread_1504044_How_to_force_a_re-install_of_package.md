---
title: "How to force a re-install of package?"
date: 2010-06-07
forum: General Help
---

### Post by leesiulung on 2010-06-07
I'm trying to re-install tomcat6 after removing it and all it's dependencies, but it got corrupt when trying to re-install. I'm on Ubuntu Sever Lucid 10.04 LTS with command line only.

I started with:

```

sudo apt-get auto-remove tomcat6

```Then I deleted the /etc/tomcat6 directory manually since it contained file settings I didn't want. I assumed it would automatically install the missing files.

Then I tried re-installing tomcat6 as follows: 

```

sudo apt-get install tomcat6

```This yielded an error:

```

Setting up tomcat6 (6.0.24-2ubuntu1) ...
chmod: cannot access `/etc/tomcat6/tomcat-users.xml': No such file or directory
dpkg: error processing tomcat6 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up authbind (1.2.0build3) ...

Errors were encountered while processing:
 tomcat6
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Any clues how to fix this?

How are you supposed to completely remove a package and re-install it normally?

---

### Post by sites on 2010-06-11
sudo apt-get --purge remove <package>

---

### Post by beckols on 2010-06-11
```
sudo apt-get purge [package]
```

This would be the best way to do it, I've had many problems when I try to just manually remove configuration files.

---

### Post by doas777 on 2010-06-11
usually to reinstallall i try it in this order:

```
sudo apt-get install <package> --reinstall
```if that doesn't work:
```
sudo apt-get remove <package> 
sudo apt-get install <package>
```and finally:
```
sudo apt-get purge <package> 
sudo apt-get install <package>
```never try to remove application parts by hand, unless you really know what you are doing. in this case, apt thinks that the file is there, because it installed it, and hasn't removed it. for future reference, never delete, but instead rename. 
```
sudo mv /etc/tomboy6 /etc/tomboy6-backup-20100611
```then when you are sure you're through the woods, you can delete it. otherwise, just run that same command again, but reverse the parameters and your all fixed.


you can probably clear your error with
```
sudo mkdir /etc/tomboy6
```

---

