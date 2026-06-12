---
title: "network interfaces ,PHPMYADMIN"
date: 2010-07-15
forum: General Help
---

### Post by miko5054 on 2010-07-15
i edit this file...
```
 /etc/network/interfaces
```
now it looks like that

```
  auto eth0
iface eth0 inet dhcp 
```
after the change I cant enter to local host with the browser 
and unable to log to PHPMYADMIN

what i need to change to solve it????

---

### Post by QLee on 2010-07-15
> **miko5054 said:**
> i edit this file...
```
 /etc/network/interfaces
```now it looks like that

```
  auto eth0
iface eth0 inet dhcp 
```after the change I cant enter to local host with the browser 
and unable to log to PHPMYADMIN

what i need to change to solve it????

Well, did it work before you "edited" it?

It's always a good idea to save a copy of a file before you edit it so that in the event of a problem, you can compare the before and after edit files.

You probably edited out the,

auto lo
iface lo inet loopback

, part of the file that is the section that sets the loopback interface for localhost.

---

### Post by endotherm on 2010-07-15
another thing to check, is that 'localhost' and your 'hostname' appear in /etc/hosts like so
```
$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    Lucid

```

---

### Post by miko5054 on 2010-07-15
the PHPADMIN worked well b4
i change it to that
```
 
auto lo
iface lo inet loopback 
```

but the result is the same...

no PHPADMIN

---

### Post by miko5054 on 2010-07-15
Google Chrome could not connect to localhost....

---

### Post by endotherm on 2010-07-15
did you reboot or restart networking after editing the file? also did you check your hosts file? also what port does the phpadmin run on? is it port 80, or an app specific port?

you can restart networking with
```
sudo /etc/init.d/networking restart
```

---

### Post by miko5054 on 2010-07-15
this is my localhost
```
 127.0.0.1	localhost
127.0.1.1	mikmik-desktop
```

i dont know on which port the PHPADMIN is on?...
and i restart it couple  of Tims

---

### Post by endotherm on 2010-07-15
> **miko5054 said:**
> this is my localhost
```
 127.0.0.1    localhost
127.0.1.1    mikmik-desktop
```i dont know on which port the PHPADMIN is on?...
and i restart it couple  of Tims

```
netstat -l
``` will give you a listing of listening ports.

what happens if you try to ping localhost? do you get replies? if so then your issue is not with naming. 
this is what you should see:
```
$ ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=4.04 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.070 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.055 ms

```

also can you connect to the phpadmin by using '127.0.0.1' in place of 'localhost'?

---

### Post by miko5054 on 2010-07-15
that`s the result of the firs command
```
  mikmik@mikmik-desktop:~$ netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0      0 *:17500                 *:*                     LISTEN     
tcp        0      0 localhost:37729         *:*                     LISTEN     
tcp        0      0 *:mysql                 *:*                     LISTEN     
tcp        0      0 localhost:5037          *:*                     LISTEN 
``` 


and that`s the result of the ping

```
 mikmik@mikmik-desktop:~$  ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.052 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.044 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.043 ms
64 bytes from localhost (127.0.0.1): icmp_seq=4 ttl=64 time=0.037 ms
64 bytes from localhost (127.0.0.1): icmp_seq=5 ttl=64 time=0.045 ms
 
```

i tried to run it on a different browser,  and reinstal phpmy admin  steel same result

---

### Post by endotherm on 2010-07-16
ok, well from your ping results, the issue is not with the local host interface. 127.0.0.1 is alive and maps to localhost.

so there are two things I would troubleshoot next. first is the port you are supposed to access to connect to the service, and the second is whether the service is running. 

Update:
[https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)

I've just looked at the community docs for phpmyadmin and it looks like it runs on port 80, so my guess is the service isn;t running, since your netstat doesnt show a listener on 80. 
furthermore it runs on top of apache so lets try this:
```

ps -ef | grep apache
```if you get no output, then the service is not running. you should be albe to start it with
```

sudo service apache2 start

```then try again. hopefully that will do it.

edit:
I've just reread the thread, and I notice that your eth0 interface is currently set to DHCP. I am wondering if that is conflicting with the apache listener configuration. was the interface previously statically assigned?
I'm not really an apache guy, but I wouldn't be suprised if it was configured to attach to a specific ip address.

---

### Post by endotherm on 2010-07-16
oh BTW, you may want to rename your thread, or start a new one indicating a problem with phpMyadmin. It may attract folks that know much more about this specific package than I do.

---

### Post by miko5054 on 2010-07-16
that solved it!!!
thanks 

```

ps -ef | grep apache
```if you get no output, then the service is not running. you should be albe to start it with
```

sudo service apache2 start

```then try again. hopefully that will do it.

---

### Post by Iowan on 2010-07-16
I can help with the thread title. I could also mark it [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), but (by following the link) so can you :)

---

