---
title: "Motion daemon write permission"
date: 2012-07-01
forum: General Help
---

### Post by ricsenior on 2012-07-01
I'm running Ubuntu 10.04 with Motion 3.2.12

When I start motion from the command line using 
    sudo motion
All is good
    [0] Processing thread 0 - config file /usr/local/etc/motion.conf
    [0] Motion 3.2.12 Started
    [0]  Motion going to daemon mode

When I auto start motion at startup and do
  tail -f  /var/log/syslog 
I can see the error message
   motion: [1] ffopen_open error creating (new) file [/media/d9a465a2-df61-429d-9494-f76a12aa69f4/motion/01-20120701162955]: 

If I change the drive motion is writing to, to /tmp it works

I've tried setting drive owner/group permissions
ls /media/d9a465a2-df61-429d-9494-f76a12aa69f4/motion -al 
total 361557960
drwxrwxrwx  3 root    root        499712 2012-07-01 16:32 .
drwxrwxrwx 13 motion  motion        4096 2012-06-29 07:36 ..

I think the mount command is correct

/dev/sdc1 on /media/d9a465a2-df61-429d-9494-f76a12aa69f4 type ext4 (rw,noexec,nosuid,nodev)


What am I missing, does the daemon have different permissions when its autostarted vs using sudo motion?

Thanks

---

### Post by matt_symes on 2012-07-01
Hi

> When I auto start motion at startup and do...

How are you auto starting it ?

Writing to /media requires evelated privileges. 

Running the command using sudo will give it elevated privileges. 

Writing to /tmp will work as that directory has world write privilages.

```
[matthew@matthew-aspire7450 ~]$ ls -ld /tmp
drwxrwxrwt. 25 root root 4096 Jul  2 00:47 /tmp
[matthew@matthew-aspire7450 ~]$ 
```

Can you post the output of

```
ls -ld /media/d9a465a2-df61-429d-9494-f76a12aa69f4/motion
```

Note the -d switch. 

Is there any reason such a crazy name is being used for the mount point ?

Kind regards

---

### Post by ricsenior on 2012-07-01
I think it is being auto started from

-rwxrwxrwx 1 root root 2357 2012-06-19 23:05 /etc/init.d/motion

ls -ld /media/d9a465a2-df61-429d-9494-f76a12aa69f4/motion

drwxrwxrwx 3 root root 499712 2012-07-01 16:32 /media/d9a465a2-df61-429d-9494-f76a12aa69f4/motion

Crazy name, never got around to changing it :-)
Thanks

---

### Post by ricsenior on 2012-07-01
Quick update, so I tried this

sudo chown motion:motion /media/d9a465a2-df61-429d-9494-f76a12aa69f4/motion

ls -ld /media/d9a465a2-df61-429d-9494-f76a12aa69f4/motion

drwxrwxrwx 3 motion motion 499712 2012-07-01 16:32 /media/d9a465a2-df61-429d-9494-f76a12aa69f4/motion

but I'm still getting 
motion: [1] ffopen_open error creating (new) file [/media/d9a465a2-df61-429d-9494-f76a12aa69f4/motion/01-20120701173205]: 

When motion is autostarted
ps -ef |grep motion
motion    1389     1  4 17:28 ?        00:00:05 /usr/bin/motion

---

### Post by matt_symes on 2012-07-02
Hi> 

I think it is being auto started from

-rwxrwxrwx 1 root root 2357 2012-06-19 23:05 /etc/init.d/motionIf you starting it from here then it should be started as root.
> 
ls -ld /media/d9a465a2-df61-429d-9494-f76a12aa69f4/motion

drwxrwx**rwx** 3 root root 499712 2012-07-01 16:32 /media/d9a465a2-df61-429d-9494-f76a12aa69f4/motionThis should also be world writeable. 

Can we test some thing. After it has booted up and when motion is not running, open a terminal and type

```
sudo /etc/init.d/motion start
```Does it start ?

If it does then stop it with

```
sudo /etc/init.d/motion stop
```Then type

```
sudo service motion start
```Does that start motion ?

If it does then type 

```
sudo service motion stop
```Post back resullts.

Kind regards

---

