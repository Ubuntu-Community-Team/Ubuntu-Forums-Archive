---
title: "I  m new in Ubuntu"
date: 2012-02-05
forum: General Help
---

### Post by warrior_king on 2012-02-05
Hello,

I m new in ubuntu. i want to know some subject that's blew :


1) Which Version is Running now latest Ubuntu?
2) Which Version is Running now Apach Server?
3) How does install Apache Server?
4) How does configure Apache Server?

Please tell me total solution above subject. 


Thanks

---

### Post by aasdfasdfg on 2012-02-05
The answers to your questions can be found by running the following in a terminal:
1) ```
lsb_release -a
```2) ```
apt-cache show apache2
```3) ```
apt-get install apache2
```4) The configuration direction for apache is ```
/etc/apache2/conf.d
```Of course, you need to obtain the requisite permissions to run some of these commands.

---

### Post by warrior_king on 2012-02-05
When i install then show :


zelthost@ubuntu:~$ apt-get install apache2
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
zelthost@ubuntu:~$ sudo apt-get install apache2
[sudo] password for zelthost: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apache2 : Depends: apache2-mpm-worker (= 2.2.17-1ubuntu1.4) but it is not going to be installed or
                    apache2-mpm-prefork (= 2.2.17-1ubuntu1.4) but it is not going to be installed or
                    apache2-mpm-event (= 2.2.17-1ubuntu1.4) but it is not going to be installed or
                    apache2-mpm-itk (= 2.2.17-1ubuntu1.4) but it is not going to be installed
           Depends: apache2.2-common (= 2.2.17-1ubuntu1.4) but it is not going to be installed
E: Broken packages
zelthost@ubuntu:~$

---

### Post by aasdfasdfg on 2012-02-05
Verify that you apt repository is not broken. You may need to run ```
dpkg --configure -a
``` to do this.

Another way to install the entire LAMP stack is as follows:
```

apt-get install tasksel
tasksel install lamp-server
```

---

### Post by warrior_king on 2012-02-06
Thanks for your instruction. 

Now tell me how to configure apache2 web server and host a web page. Tell me details and simple. coz i m in new.  


Thanks.:)

---

### Post by aasdfasdfg on 2012-02-06
For a walkthrough, see [here]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by warrior_king on 2012-02-06
Thanks ur more information [aasdfasdfg]("http://ubuntuforums.org/member.php?u=870551")

---

### Post by philinux on 2012-02-06
The above commands omitted the prefix sudo.

E.g.

```
sudo apt-get install Packagename

```
and to edit a system file would be,

```
gksudo gedit /path to file
```

---

### Post by warrior_king on 2012-02-06
Now i want know how will do uninstall lamp-server or other soft and application ?

---

### Post by aasdfasdfg on 2012-02-07
> **philinux said:**
> The above commands omitted the prefix sudo.

E.g.

```
sudo apt-get install Packagename

```and to edit a system file would be,

```
gksudo gedit /path to file
```

When I post commands here, I like to post just the commands and not the permissions handling. This way, they do not get the impression that "sudo" is part of the command they are running. I usually mention something like "execute with proper permissions".

I do this because there are several ways to ensure proper permissions for things, and I don't want to steer people down a single path. For instance, if someone needs to execute a string of commands requiring super user permissions, I would prefer they enter a su session to run the commands, rather than running a string of commands each preceded by sudo. This way, you are more likely to realize the magnitude of your actions while running commands as super user, rather than just copy pasting some code from a forum that has a mistake and causes you to do harm as a super user.

My general philosophy is I prefer a mistake to occur from not having enough permissions, than a mistake to occur while having too much permission.

Thanks for reading, please explain if this is a misleading or incorrect philosophy.

---

