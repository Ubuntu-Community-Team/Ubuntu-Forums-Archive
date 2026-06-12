---
title: "ecryptfs -&gt; where is my home ?"
date: 2010-09-14
forum: General Help
---

### Post by cAroTS on 2010-09-14
Hi there, i runnuing Ubuntu 10.04 (Lucid) for several Month, without any problems...
But today i installed some Audiofeatures because i haven´t any sound  with "nx-no machine". After a restart of the machine, all home  Directorys are missing...

I searched the Internet about ecryptfs, i tried some solutions from this Forum but nothing helps.

I can login :
```

Using username "caro".
caro@ladylike.homelinux.net's password:
Linux execute 2.6.32-24-generic-pae #42-Ubuntu SMP Fri Aug 20 15:37:22 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Tue Sep 14 11:50:44 CEST 2010

  System load:  0.49                Processes:           190
  Usage of /:   48.4% of 223.26GB   Users logged in:     1
  Memory usage: 21%                 IP address for eth0: 10.6.1.1
  Swap usage:   0%                  IP address for eth1: 77.22.72.224

  => /myOwn/data2 is using 89.2% of 586.81GB
  => There are 2 zombie processes.

  Graph this data and manage this system at https://landscape.canonical.com/

Last login: Tue Sep 14 09:28:18 2010 from xyz
/usr/bin/xauth:  timeout in locking authority file /home/caro/.Xauthority
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

caro@execute:~$


```and i can find this in the homes of the Users:
```

caro@execute:~$ ls -l
insgesamt 4
lrwxrwxrwx 1 caro caro   56 2010-08-04 16:29  Access-Your-Private-Data.desktop ->  /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
drwxr-xr-x 2 root root 4096 2010-08-11 18:14 public
lrwxrwxrwx 1 caro caro   52 2010-08-04 16:29 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt
caro@execute:~$ 

```if i try to mount:
```

caro@execute:/$ cd /
caro@execute:/$ ecryptfs-mount-private
Enter your login passphrase:
Inserted auth tok with sig [--hidden--] into the user session keyring
mount: Invalid argument
caro@execute:/$

```if root try to mount:
```

caro@execute:/$ sudo ecryptfs-mount-private
[sudo] password for caro:
Enter your login passphrase:
Inserted auth tok with sig [--hidden--] into the user session keyring
fopen: No such file or directory
caro@execute:/$

```What can i do now ?

Update:

If a User log into the System, the syslog is shouting this lines:
```

Sep 14 13:25:20 execute kernel: [ 4616.076617] Unable to allocate crypto cipher with name [ecb(aes)]; rc = [-2]
Sep 14 13:25:20 execute kernel: [ 4616.076627] Error attempting to initialize key TFM cipher with name = [aes]; rc = [-2]
Sep 14 13:25:20 execute kernel: [ 4616.076634] Error attempting to initialize cipher with name = [aes] and key size = [16]; rc = [-2]
Sep 14 13:25:20 execute kernel: [ 4616.076640] Error parsing options; rc = [-22]

```

---

### Post by frede_ric on 2010-09-15
got the same problem, but no idea what caused it. :confused:

---

### Post by cAroTS on 2010-09-15
hm...
I had do a new installation of Ubuntu without ecrypt.
Don´t know why, but some trees are completely destroyed on the Harddisk, but the Harddisk itself is free of errors/damage. 
If someone need this System for debuggig, PM me. 
I changed the Harddisk with a bigger one and can make a iso-image of the whole old crashed System.

---

