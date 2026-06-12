---
title: "/etc/hosts - No Internet"
date: 2006-05-27
forum: General Help
---

### Post by evandec on 2006-05-27
First off, let me say that this is my first return to linux after a 7 year hiatus (sp) and I really like ubuntu and I want to make the full switch away from windows, I am however having some problems.

whenever I boot I get an error message saying that I should add ubuntu to the /etc/hosts file because it can not resolve the network that I am on. When I try to edit the file I can not, I assume because I am not logged in as the root user. 


Thanks
Evan

---

### Post by orlox on 2006-05-27
to ran a command as root, simply type sudo from the terminal. Fro example, you can use gedit to modify /etc/hosts

sudo gedit /etc/hosts

---

### Post by evandec on 2006-05-27
[QUOTE=orlox]to ran a command as root, simply type sudo from the terminal. Fro example, you can use gedit to modify /etc/hosts

sudo gedit /etc/hosts[/QUOTE]


unfortunatley I can not do that. When I try to i get this error.

> unable to lookup ubuntu via gethostname()

Whats the next step?

---

### Post by Mustard on 2006-05-27
**How to edit the /etc/hosts file (troubleshooting guide)**

To edit the /etc/hosts file, you would need to get to a root prompt (as your sudo command will not be working with a misconfigured hosts file). The easiest way to do this is to use the **recovery mode** option from the **grub menu** at bootup.

When you get to a root prompt,
**1. Making a backup of misconfigured file**
If you really have no idea what you are doing then first make a backup of the file just in case you really muck things up.  A misconfigured file is at least a reference you can work from.
```
#make a backup
cp /etc/hosts /etc/hosts_backup
```

**2. Editing the misconfigured file**
Open up the /etc/hosts file with this command.
```

#this will open the hosts file in a command line text editor
nano /etc/hosts 
```

(To save files in in nano use ctrl + o and to exit from nano use ctrl + x)

The /etc/hosts file normally looks something like this...

```
127.0.0.1       localhost.localdomain   localhost       slave

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

What you need to do is to edit the first line so that it contains a hostname for your computer.  Mine is called 'slave' as you can see above.  You can choose any name you like.  The current hostname can be found by using the 'hostname' command. By default ubuntu uses the hostname 'ubuntu'.

The first line should look something like this if you were using the hostname, 'ubuntu' for example..

```
127.0.0.1       localhost.localdomain   localhost       ubuntu
```

**Additional problems that may be present**
An additional issue you might need to look into in some cases, is whether a file exists in the /etc/ folder called 'hostname'.  For various reasons, usually related to user intervention, it will sometimes not exist at all, or exists but is a blank file.  Normally the /etc/hostname will look like this (using my own host file as an example)..

```
slave
```

If it is absent then you should create a file in /etc/ folder called *hostname* and edit it to include your chosen hostname.

**Command relating to the hostname (I've included this for informational purposes)**
An additional command you can look at with regards to hostnames is this command below.
```
hostname
#returns the current hostname
hostname <hostname>
#sets the hostname according to the value entered for <hostname>

```

---

