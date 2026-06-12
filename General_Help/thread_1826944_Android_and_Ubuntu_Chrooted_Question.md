---
title: "Android and Ubuntu Chrooted Question"
date: 2011-08-17
forum: General Help
---

### Post by justinshafer on 2011-08-17
Hi... I dont know where to post this yet.. So I thought I would try you guys...

I have a droid phone, and I have ubuntu 9 running on it. This is done by chrooting since the phone runs a linux kernel. And it works...

I have a question though.

tightvncserver does work, and its able to listen on 127.0.0.1.. Its how you view your X session. So you chroot to Ubuntu, then start vncserver. Then switch back to android and login to ubuntu via vnc client.

but apache, mysql, and postgresql do not work. Well. They dont seem too.. except for mysql. Mysql will start but only if you tell it not to use networking by saying skip-networking in my.cnf

Mysql says:
mysqld cant create ip socket permission denied

Apache2 says it can find 127.0.0.1 but doesnt actually run

same with postgresql...

All seem to be compiled with arm architecture.

**So why does tightvncwork?** Why is it so special? How can it listen on the loop back (127.0.0.1) when nothing else can...

I have /proc and /dev bind to the chroot side. I can run ifconfig okay, and I can run /etc/init.d/networking start okay.. But apache2, mysql, etc have problems binding.

I have removed apparmor even though technically its not running, but I removed it and its configuration files, just because I thought perhaps mysql looks at apparmor, but I doubted it. 

Any ideas? Its all to run metasploit 4 with autopwn. I need a database to save too since metasploit 4 no longer supports sqlite3.

---

### Post by justinshafer on 2011-08-18
Chrooted enviroment but the only app that can use networking is vncserver. Bump for today. I have used nmap to port scan my phones wifi ip address and can see vnc listening.. and vnc is running on the chrooted side.

---

### Post by bnight on 2012-02-29
I found this old thread. 

However I also try to run mysql on Android. 

And since we have problem binding we can use mysql without networking.

I just add to /etc/mysql/my.cnf

skip-networking 

And mysql start ok.

---

### Post by justinshafer on 2012-02-29
Oh yeah.. I did get mysql-server running on Android.. cant remember how...

Hmmm...... It did have a setting in my.cnf that needs to be changed. Pretty sure it was something to do with what address it could talk on. 

Try telling to to only talk on the loopback, and see if that gets it to start.

---

### Post by justinshafer on 2012-02-29
I also got apache working.. Man that bugs me now.

---

### Post by justinshafer on 2012-03-01
Okay.. if you edit my.cnf and change the listening address to the ip addres of your wifi, it will start.

But you have to run mysqld manually, and when you do it wont take you back to console, you will have to open a new window

I ran nmap and port 3306 was open. Could connect to it from my pc once I set the permissions to allow it.

-J

Why it wont listen on 127.0.0.1???? I wish I knew. this was with Karmac, I have noticed some newer ubuntu images are out...

---

### Post by MikiBroki on 2012-06-07
Hi justin, I have downloaded a Ubuntu image for my android tablet and I have correctly installed Apache+PHP.

But... I have no way to start MySQL from my VNC client (mysqld cant create ip socket permission denied).

I have the 'skip-networking' option in /etc/mysql/my.cnf... but MySQL doesn't start... did you do any other config to start it ?

---

### Post by Odogwuu on 2012-09-02
go to the my.cnf configuration, could be in /etc/mysql/my.cnf

under
[mysqld]
user = mysql

back it up by commenting it out
#user = mysql

and add user = root, so it will look like this
user = root

bind-address can be 127.0.0.1 or commented out to run on all interfaces

then try starting up mysql sever in chroot and it will start with no errors, hope this helps, this is my first post..
:P

---

### Post by Freol on 2013-05-11
There is a solution for MySQL - you just must add mysql user to android_inet group (I'm using LinuxOnAndroid Ubuntu 12.04 image). Default user can't bind socket that is why "Permission denied".
# addgroup mysql android_inet

---

