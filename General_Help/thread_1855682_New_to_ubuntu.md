---
title: "New to ubuntu"
date: 2011-10-06
forum: General Help
---

### Post by acex008 on 2011-10-06
Let me preface this post with the fact that I am coming from a VERY limited background focused in Windows systems.  I have NO experience in writing code nor any programming skills.  With that said, I do have AutoCAD experience (been using it for over 12 years now) creating LISP routines which I suppose would be considered code driven...  I understand the concepts behind codes and programming language and learn things computer-oriented very quickly.  Point me in the right direction and I can usually figure things out.  The terms I use may be completely inaccurate and I may miss a concept entirely since my brain is constantly trying to "compute" the information in such a way based upon how Windows functions.  So please bear with me and hold my hand!

Alright this may be a bit premature but thought I'd post it anyhow.  I will be installing a copy of Wubi on my Windows PC this evening or soon after.  However, I would like to learn how to build my own executable scripts from the get-go.  I have one in particular that I would like help writing.

I would like the ability to archive all my media files (pictures, music and videos) for backup and after that archive is generated it will automatically be sent to an FTP server.  I'm hoping that I can create a single "app" that will periodically "run" at a configured interval and perform these tasks "silently", in the background without any future input by me.  Basically I want to write the script, run it and not have to think about it thereafter.  Hoping "it just works".

I have multiple PC's at multiple locations that I use the FTP server for "sharing" of my files.  My PC's are running Windows XP, Windows 7 and hopefully Wubi before the end of this week.  Hopefully this "background task" will help me archive and keep track of my media, as well as in crossing platforms easily with the files.  Sometimes I'm away from the PC that will have Wubi on it but I'm hoping if I leave it running it will perform the archiving and uploading on it's own.  That way I can log into the FTP server off site and get the latest files from that PC without having to locally verify that they're the latest files and that I've got the most current information.

Can this be done with one executable script without any user input?

---

### Post by jazzon on 2011-10-06
I am (unfortunately) not good enough at scripting to help you do this, but to give you an imitate answer.  Yes, easily using a script with one line in a crontab file.  So watch your post, someone will get it done.  I even know parts of it, but not all of it, and I'm fairly new to that stuff myself.  Start by researching cron, and tar.  The scrips will (I'm pretty sure) use those resources.

---

### Post by acex008 on 2011-10-06
Thanks for the quick response Jazzon.  And thank you for some information.  I'll start researching tar and cron now!  I forgot to mention I'd like to do this without the need for installing any other tools other than what comes with the "out of the box" Wubi.

Reason being is that I'd like to be able to send this script file to another machine that's about 500 miles away at my second home without the need to remember which tools or apps to get for it...

---

### Post by Derek Karpinski on 2011-10-06
Try DejaDup in the software center. Unless you are completely bent on writing a script.......
 
EDIT: sorry, I missed the part about you not wanting to install any software.

---

### Post by Frogs Hair on 2011-10-06
Here is some background information . [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by Derek Karpinski on 2011-10-06
To do it securely, you should intall ssh, and use scp instead of ftp. You could also use duplicity to do incremental and encrypted backups.
 
[http://www.go2linux.org/scp-duplicity-secure-backup](http://www.go2linux.org/scp-duplicity-secure-backup)
 
[http://duplicity.nongnu.org/duplicity.1.html](http://duplicity.nongnu.org/duplicity.1.html)
 
See the examples in the second link.
 
But this still means you're going to have to install duplicity.

---

### Post by pjd99 on 2011-10-06
A few references if you want to tinker with bash scripting.

Bash for beginners: [http://tldp.org/LDP/Bash-Beginners-Guide/html/](http://tldp.org/LDP/Bash-Beginners-Guide/html/)

Advanced Bash Guide: [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

Also, manual pages are your friend.
From the terminal:
```

man rsync
man cron
man crontab

```rsync should be able to do what you are after. It synchronises files, and is quite efficient. If you update a file, rdiff calculates the differences and only transmits what is required.
Info: [http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/)
Using with ssh and cron: [http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)

I don't bother with cron, I just use the scheduled tasks application.
sudo apt-get install gnome-schedule

If you're an advanced AutoCAD user, a bit of shell scripting will be well within your grasp.

---

### Post by acex008 on 2011-10-07
Thank you all for the great information!  I'm a research junkie so this is like candy to me!  

:popcorn:


Is there a way to configure rsync, compile it, send the program to another of my PC's, double click on the preconfigured file and it'll be installed all preconfigured without the need for terminal input?

Here's the REAL breakdown of why I'm after not installing software...  I won't be physically at my other house to be able to install and setup rsync or whatever else I decide to use for this.  My wife will be going there on business and I was hoping to have her download a file from an email that when she downloads it to a folder on the local HDD and double clicks on it, the program will be installed and the syncing will start.  I want it to function just like a typical exe in Windows that I can email to her and have it easily installed.  We have vacation pictures and a bunch of other stuff on that PC and we aren't sure when I'll be heading up there again.  Soooo I'd like to find the absolute simplest way to set this up on that PC since she doesn't understand code and I don't want her to mix up the code and have our files sent anywhere else for obvious reasons. 

Also, I'm a bit unclear as to how I can access the files here at our main house on my Windows PC.  If I use rsync, where do the files get sent?

---

### Post by Derek Karpinski on 2011-10-07
You need to first set up ssh.
 
Once you do that, you will be able to securely administer the remote computer, and install any programs you need remotely.
 
You'll probably have to sign up for a dyndns.com type service so when your ip changes on the remote computer, you'll still have access to it.
 
So, if I were you I'd go to [http://dyn.com/](http://dyn.com/) or see if your router offers a free service like it, and set up a dns name for your remote computer.
 
Then, set up ssh, [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH), client is installed, ssh server needs to be installed.
 
```
sudo apt-get update
sudo apt-get install openssh-server
```
 
Make sure port 22 open on the remote computer, make the keys, then share the keys.
 
After you get that all done, someone else will have to help you with writing an rsync script.
 
Except, if you don't have physical access, I'm not sure if you can get past the first step.

---

