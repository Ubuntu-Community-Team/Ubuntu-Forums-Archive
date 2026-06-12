---
title: "Quick Rsync script"
date: 2011-09-11
forum: General Help
---

### Post by W@@dy on 2011-09-11
Ubuntu 10.10
Gnome terminal I doth believe

Made an rsync script to back up my home folder and everything within.

The actual script and backup works, however I want to automate it.
I originally had it on Cron, but since this is a laptop, it's very unlikely to be on at the time specified in Cron.
So I want to know if it's possible to run this script at login.

I ask 'if' because so far I've had no luck.
I've set the file to executable, added it to 'Startup Applications'
but it still wont work :l

Works fine if I call it through terminal. I thought maybe it needed a delay for the WiFi to connect, so I gave it a 60 second delay, which is quite gracious.

Here's the script
"#!/etc/sh
sleep 60
rsync -avz --delete /home/woodams/ cbot@cbot-Desktop:/home/cbot/woodams-Cr48_Backup/"

cbot is where the stuff gets stored to. dont ask why it's called cbot, I was bored.

Here's my only thought as to why it won't work, and that is that 'Startup Applications' calls all files as root.
I've noted that using this script as root (i.e. su or sudo) it will not work. It causes issues with the rsa key file locations and such. Basically it treats it as if it's being run as a different user (well it is, technically, isn't it? haha).

So gimme some help! I don't really care how it's done, I just want it automated :D

I'm putting another project on hold until this finishes, so help asap would be mucho appreciated

---

### Post by jv2112 on 2011-09-12
I would suggest Anacron. It schedules jobs based on time relative to boot up. 

[http://www.thegeekstuff.com/tag/anacron-ubuntu/]("http://www.thegeekstuff.com/tag/anacron-ubuntu/")

---

### Post by SlugSlug on 2011-09-12
> **W@@dy said:**
> Ubuntu 10.10
Gnome terminal I doth believe

Made an rsync script to back up my home folder and everything within.

The actual script and backup works, however I want to automate it.
I originally had it on Cron, but since this is a laptop, it's very unlikely to be on at the time specified in Cron.
So I want to know if it's possible to run this script at login.

I ask 'if' because so far I've had no luck.
I've set the file to executable, added it to 'Startup Applications'
but it still wont work :l

Works fine if I call it through terminal. I thought maybe it needed a delay for the WiFi to connect, so I gave it a 60 second delay, which is quite gracious.

Here's the script
"#!/etc/sh
sleep 60
rsync -avz --delete /home/woodams/ cbot@cbot-Desktop:/home/cbot/woodams-Cr48_Backup/"

cbot is where the stuff gets stored to. dont ask why it's called cbot, I was bored.

Here's my only thought as to why it won't work, and that is that 'Startup Applications' calls all files as root.
I've noted that using this script as root (i.e. su or sudo) it will not work. It causes issues with the rsa key file locations and such. Basically it treats it as if it's being run as a different user (well it is, technically, isn't it? haha).

So gimme some help! I don't really care how it's done, I just want it automated :D

I'm putting another project on hold until this finishes, so help asap would be mucho appreciated

Not sure it should be ran as root if its in your 'startup applications'

```
#!/bin/bash
sleep 60
##/bin/su  USERNAME   #try without this first then unhash if it is being ran as root
/usr/bin/rsync -avz --delete /home/woodams/ cbot@cbot-Desktop:/home/cbot/woodams-Cr48_Backup/
```

---

### Post by kjohri on 2011-09-20
You can automate the backup with anacron. There is a detailed write-up here,

[http://www.softprayog.in/tutorials/anacron](http://www.softprayog.in/tutorials/anacron)

---

### Post by Quarkrad on 2011-09-20
What happens if you make changes to a doc, download something, etc and something happens to your pc - or your pc will not boot next time?  Have you thought about automatically saving/backing up your **home** folder when your pc closes (after any changes) rather than at start up?  If you are interested let me know and will show how to do this.  (A script runs automatically when you press Shutdown and backs up **home**).

---

### Post by W@@dy on 2011-09-20
Right now I have it working with anacron. It took several days to determine if it was working or not because the remote server can only be accessed locally, and I take the laptop to college most days of the week.
So anacron would run, not be able to connect to the remote server and that was that.

It wasn't until the weekend that I discovered it had successfully backed up the PC (I turned it on while at home instead of at my college).

I've also got it working on another PC that remains at home.

Anacron uses Root on everything though, so I had to setup SSH rsa (automatic connection, no entry of password) within the root directory.

```
sudo ssh-keygen -t rsa
```

Is this something horrendously unsafe to do? (it feels like it).

Quarkrad, that actually sounds really useful. How involved is it?

Slugslug, I'll give it a shot

---

### Post by Quarkrad on 2011-09-21
I'm afraid I'm running something on my pc that has rendered it out of action for 2 days so I cannot get access to the info you need.  As soon as I can get into it I will pass on the info.  I an a newbie to Linux and not skilled at commands so I posted a request to this forum some years back.  In windoze world I had a small app that would back-up any local folder to another local folder on close down.  I had a response from this forum that allows me to do this.  I use GAdmin-rsync to set up the backup I need and it saves it in the form of a .sh file.  This is placed in the init.d folder and a small command (that I got off this forum) is run that automatically runs the rsync script in init.d every time I power down my pc.  So having set it all up - my **home** folder (actually, and others) is automatically backed up for me every time I power down.

---

### Post by Quarkrad on 2011-09-21
Hmm - had to kill what I was doing on pc so able to get to info.   Create rsync script xxxx.sh and move script to etc/init.d.   Then run this command in terminal to have script run automatically every time pc is switched off.

**sudo update-rc.d script.sh start 03 0 6 .**

It is important to copy the whole command above including the last dot and spaces between characters.

change script.sh for the **yourscriptname** of your script that you put in etc/init.d  so your command would look like

sudo update-rc.d **yourscriptname**.sh start 03 0 6 .

---

