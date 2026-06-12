---
title: "Please help I'm about to go back to windows!"
date: 2011-01-13
forum: General Help
---

### Post by d_link on 2011-01-13
Well my windows 2000 pro (used as my server) hard drive crashed about 2 weeks ago. I was so excited I figured now is the time to ditch Microsoft and go to Ubuntu. I installed Ubuntu 10.10 gui eddition because I'm not fimaler enough with linux to use the server eddition via command lines. Heres the problem, I have run into nothing but problems one after another. I really don't want to give up, but stuff just is not working. Big problems that I'm currently facing right now are as follows:
 
1.
Problem:
I have a 1TB Seagate Desk FreeAgent USB external backup drive that I need to backup my 1TB seagate internal drive. I hooked it up but can't get Wine to run the setup. If I change the allow excute it just unchecks it and I can not excute the external drives software.  I can access the drive and move stuff to and from it.
 
Question:
Do I need to move the seagate software to my home folder on the internal drive to excute it or is there away I can allow excution from a USB drive or CD rom drive?
 
2.
Problem:
The other major thing I run is vibe streamer for my mp3's. I was able to get it to run via wine and set it up but ran into some snags. First if I change the ip or port to anything other then 0.0.0.0 on 8081 I can not start vibestreamer. Vibe streamer works on the default setting and I can access from firefox page but only using the local machine [http://127.0.0.1:8081](http://127.0.0.1:8081).
 
Question:
What is causing vibe streamer not to execpt anything other then it's default? I would like to change the IP to 192.168.0.2 (or local host) on port 83.
 
3.
Problem:
I could not get the remote desktop feature working so I unistalled it and set up .X11VNC server and have to check off java to get it to work via a web browser.
 
Question:
I was able to get this to work but can not figure out a way to get it to load on boot up and would like it to have the same setting every time it opens.
 
So if anyone can help I'm willing to try and stick with it but it seems like eveytime I try to do something in ubuntu I have to start doing research for hours and then give some commands that used to work back in 2006 but does not work with ubuntu 10.10.  Please help this noob, thanks.

---

### Post by davidmohammed on 2011-01-13
re 1:

why do you need to install the seagate software in wine - just plug in your external drive and ubuntu should just automatically see it - have a look in your places menu.

---

### Post by davidmohammed on 2011-01-13
re 2: ... and in general, you'll often find equivalent or sometimes better native linux applications that are equivalent to windows programs.  For mp3/radio streaming etc - suggest use icecast2 

to install

sudo apt-get install icecast2

more info from the icecast [website]("http://www.icecast.org/").

---

### Post by Mark Phelps on 2011-01-13
> **d_link said:**
> .. now is the time to ditch Microsoft and go to Ubuntu...

You're NOT ditching Microsoft if you're trying to load MS software using Wine.  IF you're that dependent on MS SW to do stuff, you've made the wrong decision to switch to Linux.

---

### Post by davidmohammed on 2011-01-13
... agree with Mark


re 3 - there are a number of threads on howto autostart xvnc

try [-Start-x11vnc-via-Startup-Applications.html"]this one]("http://www.allquests.com/question/4288725/[ubuntu) for size - read it bottom to top!

---

### Post by 3Miro on 2011-01-13
1. For your hard drive, you should be able to just plug it an it should run. Sometimes vendors put special software on the hard-drive that restricts it to working only on Windows, but this is rare.

2. Try NFS or Samba, it looks like a better way to "stream" mp3 on a local network. Also check davidmohammed's post.

3. I don't do "remote desktop", so I don't know. Most Linux users prefer ssh. Check it out, it will also help you learn the command line.

Your problem is that you are trying to use Ubuntu as if it is Windows. Linux is not Windows. Things work different on almost every level. You should change pretty much every program that you are using and you should not go for wine or VirtualBox unless there are no other options. 

It also seems that you are a Windows power user. If that is the case, you will have to first "unlearn" windows and then spend a period of time, where you will suffer from "diminished" productivity. There is no way, in such a short period of time, that you will be able to master everything in Ubuntu that took you years to learn under Windows.

---

### Post by akand074 on 2011-01-13
> **Mark Phelps said:**
> You're NOT ditching Microsoft if you're trying to load MS software using Wine.  IF you're that dependent on MS SW to do stuff, you've made the wrong decision to switch to Linux.

Exactly. What you are doing is completely counter intuitive. Why are you switching OS if you're just going to use Windows software. Your Seagate external drive does not need any software installed, it works just by plugging it in. Anything else, not only is there linux alternatives for it, the alternatives are likely better. Linux is used in about 97% of the server market I hear. That being said, because of this, I would assume there is likely much more/better software for servers in Linux than any other OS.

---

### Post by cmoraes on 2011-01-13
Welcome to Ubuntu.

> **d_link said:**
> I installed Ubuntu 10.10 gui eddition because I'm not fimaler enough with linux to use the server eddition via command lines.


That was the right decision.  The Ubuntu desktop edition is for normal use.  The server edition is really more suited to enterprises or small businesses.  Don't worry, any server software you require can be installed on the desktop edition also.

 > 
Do I need to move the seagate software to my home folder on the internal drive to excute it or is there away I can allow excution from a USB drive or CD rom drive?
 I'd like to suggest an alternative approach.  You don't need to use the seagate software to backup your drive.  Linux has very good backup programs and you can use any of them with your external drive.  From my own experience I usually find - simple backup software (which just mirrors your existing data, and is still readable from the external drive) to be the best. [Here]("http://www.webupd8.org/2010/05/best-linux-backup-tool-software.html") is more information about the backup options available on Linux.

> 
2.
Problem:
The other major thing I run is vibe streamer for my mp3's. I was able to get it to run via wine and set it up but ran into some snags. First if I change the ip or port to anything other then 0.0.0.0 on 8081 I can not start vibestreamer. Vibe streamer works on the default setting and I can access from firefox page but only using the local machine [http://127.0.0.1:8081](http://127.0.0.1:8081).
 
Question:
What is causing vibe streamer not to execpt anything other then it's default? I would like to change the IP to 192.168.0.2 (or local host) on port 83.
 Are there any vibestreamer logs you can inspect?  They may tell you what the startup error is.


> 
3.
Problem:
I could not get the remote desktop feature working 
 Did you try Applications > Internet > Terminal Server Client.  This is similar to the Remote Desktop you're used to with Windows.  I use this regularly to connect to Window Server 2008 boxes and it works fine.

If you want to install it again do

```
sudo apt-get install rdesktop
```

---

### Post by d_link on 2011-01-13
First i'd like to say thanks for everyones help here, good to know there is great support from people willing to help.  The only reason I'd use a windows program on ubuntu is because I could not find a good alternitive.  I'm more then willing to run Linux programs over MS programs.  As for the segate drive I can browse the drive just fine but need a good easy backup program to maybe do a complete backup every 2 weeks and only back up files that have changed.  Now as for vibe streamer I just like the program and am used to it.  I can change to something else but would like to be able to have some of the same options vibe streamer has.  Vibe streamer has it's own permissions for users, a searchable data base and can be streamed to the web easy.  I am going to check out some of the suggestions you guys gave me right now and I'll let you know how it goes.  I havn't given up hope yet, I don't want to say Bill Gates beat me LOL.

---

### Post by Elfy on 2011-01-13
Glad you are finding help with your issues.

Next time please use a sensible thread title ;)

---

### Post by davidmohammed on 2011-01-13
here is an [article]("http://www.linuxlinks.com/article/20090105114152803/Backup.html") to get you thinking about backups.

---

### Post by 3Miro on 2011-01-13
For backups, I just use rsync. You can Google it (and it is probably already installed).

---

### Post by Primefalcon on 2011-01-13
I myself just run a script through cron that tar and gzips

---

### Post by matt_symes on 2011-01-13
Hi

Have a look at 

[http://www.osalt.com/](http://www.osalt.com/)

for alternative software for Linux that works like MS software.

And please.. Stop thinking in windows.  +1 on the daft title.

Kind regards

---

### Post by d_link on 2011-01-15
OK I'm still at it and getting even more ticked off!  I can see why normal people give up on LINUX!  Been 4 days just trying to set up stupid little things and keep running into problems (maybe I the problem).  I got the vibe streamer working via WINE but it will only work on port 8081.  Next I got the X11vnc working but have not configured it to start automatically (not real worried on that).  Then I got the backup working using "Back in Time" (had issue with it getting stuck on a .bkf file so I moved it manually and then the back up ran fine).  Now I have an issue setting permissions on files using "apply permissions to enclosed files" it won't do it reclusive.  I even tried using Dolphin but it did the same thing.  Wondering if I  need to unmask the media directory because the files came off a windows  system (not sure why or how this works).
Here's what I done so far.

Took all my mp3's, pictures, movies exct.... from my seagate external backup drive and moved them to the my home/eric/public/media/ folder.  I now have 5 folders in there called Movies, Wedding, MP3, Personal and Pictures.  Of course they are all what the say except the Personal folder, in there I have a folder for each family members (Eric, Debbie, Kayla, Tori).  Now what I would like to do is share the Media folder so everyone in the house can access it from any computer (Windows or Linux) with viewing rights only.  Then I would like each person to have write access to there own personal folders with my wife and I having read write access to the kids folders.  So it should look like this.

/home/eric/public/media/*.*  -Everyone has Read and Execute
/home/eric/public/media/personal/Eric/*.*  -Eric Read, write and Execute
/home/eric/public/media/personal/Debbie/*.*  -Eric, Debbie Read, write and Execute
/home/eric/public/media/personal/Kayla/*.*  -Eric, Debbie, Kayla Read, write and Execute
/home/eric/public/media/personal/Tori/*.*  -Eric, Debbie, Tori Read, write and Execute

The reason I'm upset is I have to either get Ubuntu working or I have to revert back to Windows so I can format the orignal bad drive to send back to Seagate (they only give you 25 days and I have already been almost 2 weeks).  I really want to go Linux and convert the kids computers after I get the server done.  I just fell like I'm pulling my hair out and in a rush.  PS this is not my first time using Linux I used to use Linux for my job about 7 years ago but I forgot a lot of it.  Please help.....](*,)

---

