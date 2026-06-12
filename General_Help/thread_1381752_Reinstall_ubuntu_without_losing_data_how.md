---
title: "Reinstall ubuntu without losing data how?"
date: 2010-01-15
forum: General Help
---

### Post by hockey97 on 2010-01-15
Hi, I have issues with updates and installing any package. The installer gives errors that avoids installing anything anymore.

I want to use the ubuntu live cd to reinstall all ubuntu system files.

Is their a way where I can keep my own files that is not part of the system files... and keep my video and sound drivers.

I just want some easy way to fix the the dpkg installer. cuz it has error issues and I did posted before about this problem but I had people tell me to try this and that and nothing worked. So I assume I need to reinstall.

I just don't want to have the pain again to reinstall everything. 

I want my database mysql and apache to be exactly the same. i use webmin as a interface to my apache and mysql.

any Ideas what I can do. 

thank you for your time.

---

### Post by plusnplus on 2010-01-15
interesting topic ! I also want to know :)

---

### Post by houseworkshy on 2010-01-15
It would help people to help you if you could post your error output. It may be something to do with software sources or broken packages but that is only guessing.

---

### Post by kahlil88 on 2010-01-15
You should definitely try to sort out whatever problem your system is having before resorting to a complete re-install. To answer your question though, what I usually do is boot the Live CD and create a folder in the root directory called OLD and move my home folder and anything else important into it, then do a clean install (without formatting of course). Then when the system is up and running again, put what you still need back in its proper place and delete the /OLD directory.

---

### Post by Mighty_Joe on 2010-01-15
Unless you have a full offline backup of your system, it is only a matter of time until you lose data, no matter what operating system you have. 
Personally, I just copy the files I want to keep onto a 1TB external USB hard drive.  Really important files, like pictures of my boys, go on DVD and are stored offsite.  
[mysqldump]("http://dev.mysql.com/doc/refman/5.1/en/mysqldump.html") makes backing up MySql databases easy.  
Backing up Apache can be as easy as just copying your http root directory.
I don't bother to back up applications or drivers.  That's Ubuntu's job.

---

### Post by ushills on 2010-01-15
The best way is to use a live CD, create a partition for the OS and a home partition for your settings, documents etc.

You can then reinstall ubuntu to the os partition as often as you want but keep all your settings and docs.

See the guide here

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

IMHO you should always set up like this.

---

### Post by ushills on 2010-01-15
You should also do this to keep a record of your installed applications.

[http://www.ushills.co.uk/2008/02/backup-and-restore-installed.html](http://www.ushills.co.uk/2008/02/backup-and-restore-installed.html)

I have the following in a daily cron job as part of my backup.

```
dpkg --get-selections "*" > applications
```

---

### Post by hockey97 on 2010-10-11
The reason I ask is that I am currently setting up servers. I setup one computer as the server to just develop the websites on while I waited for the server parts to be shipped to me. 

My main question is really about whats the best way to reinstall a system without losing your own data. I know you do backup important files. I know system admins people that own servers they have a efficiant way. I have seen websites down due to hacks. Hackers uploaded a shell script in php to a website and deleted all files of that servers system.  Yet in a matter of 10 min they got everything backup with no data loss.

I want to know if there is some way to reinstall just the system files.

Currently I am in a jam. I used the terminal to install some programs on ubuntu but after running the terminal to install programs I found out it deleted my home folder and user.

So currently I got a ubuntu system that works but I can't log in as my own user and everything in my user home folder is all gone.  Thank god I backed my websites from my user folder and all important files.

What I am trying to say is that it takes alot of time to reinstall everything.

If I have a server and use apache, mysql and many other apps like gimp.  How can I efficiently recover from disaster.

In the business world time is money. I  want to just one time setup everything and that is it. I need a setup that if my server or computer goes crazy or gets errors and crashes. I want to be able to quickly press a button or something that would grab backed up data and send it to the proper places after a clean reinstall.

Right now I am woundering with the live cd if I can recreate a home folder and user. I know I can make a new user but  don't know how to make a brand new user home folder and have it work.

---

### Post by Kyentei on 2010-10-11
Just a little word of advice, create a seperate /home partition in your next installation. Get yourself a / partition with the size of 10-20GB, keep the rest for /home. That way, if you ever re-install, all you have to do is set the correct mount-point to your largest partition. =)

---

