---
title: "Act upon the existence of a new file?"
date: 2011-06-27
forum: General Help
---

### Post by Kissell on 2011-06-27
I have a cron job running to act upon files if they exist in a folder...  the problem is the nature of those new files.  New files aren't put there very often, the server isn't used much (most of the time) so I would like to not check every minute to see if a new file is there and allow the disks to spin down and go to sleep.  However, when a new file does exist there, it needs to be acted upon ASAP.

So currently I'm handling that with a cron job...  it works...  but what would work much better is the ability to act upon the event of a new file being present.  Is there a way to trigger action upon new file system activity in a certain path?  or just keep doing what I'm doing and have the system check all the time and keep the disks awake just in case something shows up?

---

### Post by Ozymandias_117 on 2011-06-28
Don't know how involved you want to get, but inotify sounds like what you're wanting.  Here's some information about it: [http://www.ibm.com/developerworks/linux/library/l-ubuntu-inotify/index.html](http://www.ibm.com/developerworks/linux/library/l-ubuntu-inotify/index.html)

---

### Post by Kissell on 2011-06-28
Wow, thats perfect.  I wasn't expecting to find anything.  

Well, maybe perfect isn't quite the right word, I was hoping for a simple command, not to program an application...  but it shouldn't be too hard with their examples.

---

### Post by Ozymandias_117 on 2011-06-28
If you want to be able to access it from a script, you should be able to install inotify-tools and use the command ```
inotifywatch
``` from it.

---

### Post by Kissell on 2011-06-28
I added inotify-tools
> 
sudo apt-get install inotify-tools


Nothing quite did what I wanted.  But googling it I found something called "incron" so I installed it.
> 
sudo apt-get install incron


Incron adds the command "incrontab" which is exactly like "crontab" except it operates based on file system events instead of time based events.  This is exactly what I wanted.

Had to edit a file and add "root" before it would work.
> 
vi /etc/incron.allow 


Then did a 
> 
incrontab -e

to setup events just like using cron.

You will need to  
> 
man incrontab

to get a list of the event symbols and figure out how the syntax of the incrontab program works, obviously syntax is different than crontab because you aren't doing time based events, and unfortunately there are no comments in the default job like there are in crontab.

Thanks!  I never would have found incron without hearing about inotify.

---

### Post by Kissell on 2011-06-28
Argh...  I tried to do a simple port of my cron jobs to incron, and that doesn't work well for all of them.  A few jobs went okay...  but things that I can normally run from a command line or from cron will lock the server when running from incron. 

My guess is that because it is constantly monitoring the folder, if you do something like rename a file that probably initiates an endless loop.  Whatever it is, it is locking up the server so the keyboard doesn't even respond to input, the only thing I can do is reboot.  I looked at it and though I fixed it, but no, it locked up again upon the test.  Time for bed.  Thank god the software raid didn't have to start over on its resync (the whole reason I was playing with this server anyway), it was almost finished with the rebuild when I locked it up, luckily the new version of mdadm lets it continue where it left off after reboot, I was pleasantly surprised with that.

---

### Post by otaviofcs on 2011-07-31
Hi Kissel, have you been able to use incron in production mode? Or are you still in test fase? 

I've tryie it now and it definitely need different approach of your scripts (comparing to cron). But it looks nice. Nowaday I have a bunch of scripts on cron, each one scanning directories from time to time, looking for files arrival. So we are looking for a much cleaver way to do this and incron seems to be exactly what we need, if it is an stable tool.

It would be nice if you, or any other, can send further comments.

Best Regards,

Otávio Sampaio

---

### Post by Kissell on 2011-07-31
incrontab works great.  It is exactly what I needed and sounds perfect for your needs too.  

It is a little difficult to use.  You can easily lock up your server while testing it.  The key is to use a parameter called "IN_NO_LOOP" without that I kept getting into infinite loops and having to reboot my server, but now it works great.  I have implemented incrontab on lots of servers in production.

Here is some sample code that works for me:
> 
$HOME/Dropbox/NewFile IN_CREATE,IN_NO_LOOP $HOME/update


IN_CREATE only runs the update script after a new file has been created in the NewFile folder.

---

### Post by otaviofcs on 2011-08-01
Hi Kissel,

Nice to hear from you! Great tip. It's perfect for newcomers like myself :). Well, I have already implemented it at one of our development servers. Works like a charm.

I'll give IN_NO_LOOP a try.

Best Regards,

Otávio

---

### Post by Kissell on 2011-08-01
If its working, then you don't need IN_NO_LOOP.

I think what was happening, is I would copy a big file to a monitored folder, and was using IN_WRITE, and the computer doesn't save the whole file at once, it has to write small parts then write some more, so each time it created a new part of the file it would run my script again, the script would do something processor intensive that would take a long time, like copy the file to another volume, and because it was told to do that over and over again it effectively created a denial of service.  Perhaps it wasn't an infinite loop, that if I waited long enough the server would have started to respond, but I just rebooted and could not figure it out for a long time.  I had an idea about why it was doing it, but took awhile to find the command IN_NO_LOOP which fixed it.  

I have a problem on a Ubuntu 10.10 server, incrontab doesn't work after I reboot, I have no idea how to fix that, I think it is just a bug, so I have to edit incrontab everytime I reboot, if I don't then incrontab doesn't work until I edit and save the incrontab script/settings.  Later this month I'm going to upgrade the RAM in that server and reinstall the operating system, put 64-bit ubuntu on it...  so I'm assuming the problem will be fixed when I do that...  although version 11.10 is almost out, I might wait to do the upgrade until it comes out so I can do a fresh install.

---

