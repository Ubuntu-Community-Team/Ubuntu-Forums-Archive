---
title: "step by step instuctions for thttpd"
date: 2010-12-18
forum: General Help
---

### Post by 3rr0r on 2010-12-18
Hello all.  I am trying to setup thttpd on my ubuntu 10.04 system.  I run ubuntu in a vm and would like to be able to turn on and off a simple web server as I please.  I have been having lots of trouble trying to find a guide on how to setup and run thttpd.

I have looked at the author of thttpd's [homepage]("http://www.acme.com/software/thttpd/notes.html") as well as [this guide]("http://radagast.bglug.ca/howto_build_a_server/howto_build_a_server_part1.html"), and yet I cannot get it to work.

Can someone please help?  Basically I have it installed and don't know how to start or configure it so that it starts.

Current code
```
user@ubuntu:~$ sudo apt-get install thttpd
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
thttpd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
user@ubuntu:~$ myip
192.168.1.3
```

I navigate in firefox to [http://192.168.1.3](http://192.168.1.3) and get "unable to connect" error.

---

### Post by 3rr0r on 2010-12-18
For anyone looking for a solution, I will post it here (hate when people say, "I got it working!!" but don't post the solution).

1. Install thttpd
```
sudo apt-get -y install thttpd
```

2. Backup then edit a config file
```
sudo cp /etc/defualt/thttpd /etc/defualt/thttpd.backup
sudo nano /etc/defualt/thttpd
*[INDENT]find and change ENABLED=no to ENABLED=yes[/INDENT]*
```

3. Start/stop thttpd (I recommend creating an alias for this)
```
sudo /etc/init.d/thttpd start
sudo /etc/init.d/thttpd stop
```

---

