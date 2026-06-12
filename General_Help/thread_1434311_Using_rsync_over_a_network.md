---
title: "Using rsync over a network"
date: 2010-03-20
forum: General Help
---

### Post by ChrisML123 on 2010-03-20
Hi,

I'm using rsync to backup an XP pc to an ubuntu desktop. My problem is that cygwin rsync seems to cut out every 10-30 minutes. I'm not sure why, it says 'peer refused connection'. So maybe its my network being a bit of a fail.

My question is: how do I set rsync, on the ubuntu box, to do a backup every hour, of the windows pc, unless there's already one running, and if the connection fails, just to wait until it comes back?

I'm a newbie at this, so tell me what to type in steps would be very cool.

Bless,
[Chris](http://allaboutchris.co.uk)

---

### Post by HermanAB on 2010-03-20
Howdy,

Try using the bw parameter of rsync to throttle things a bit, then it should keep going.

---

### Post by jrssystemsnet on 2010-03-20
1. definitely sounds like your network is failing hard.  are you using wireless?  if so... try *not* using wireless. :)

2. try not using cygwin and rsync... there's a prepackaging of rsync server for windows that usually works a little better.  Google cwrsyncserver.  Find, install, configure.

3. simple shell script... name it "rsyncbackupscript.sh", for reasons that should be readily apparent:

```
#!/bin/sh
[ $(ps waux | grep rsyncbackupscript | grep -v grep | wc -l) -eq 0 ] && /usr/bin/rsync -har --delete your.xp.machines.ip::rsyncshare /path/to/your/backup/folder/
```

Now make it executable:

```
you@box:~$ sudo chmod 755 /home/you/rsyncbackupscript.sh
```

Now add a crontab to run it every hour, using **sudo crontab -e** (to put it in root's crontab... you can leave off the sudo, if you'd rather have the process run as you).  NOTE: if you don't like vi, you might want to do **EDITOR=/usr/bin/nano** and **export EDITOR** before you try doing the **crontab -e**!

```
# m h  dom mon dow   command
  0 * * * * * /home/you/rsyncbackupscript.sh
```

That oughta do it.

---

### Post by ChrisML123 on 2010-03-20
I need to get an extra box for my router. only got one ethernet port at the moment. Then I can ditch the wifi.

the shell script is to go on the ubuntu machine yeh? The cwrsyncserver can just work as a client despite the name?

Will attempt this tonight, after i've bought a ethernet box

---

### Post by ChrisML123 on 2010-03-20
wow, installed cwrsyncserver. its tiny!

[Chris]("http://allaboutchris.co.uk")

---

### Post by ChrisML123 on 2010-03-20
Should /path/to/your/backup/folder/ be the path on my pc i want backed up: Ie E drive, or the place I want files saved to on the linux machine.

If the later, where do I say where I want files actually saved?
[URL="http://allaboutchris.co.uk"]
Chris[/URL]

---

### Post by ChrisML123 on 2010-03-21
Ok, so i am still with cygwin, having had not much help in moving away from it.

My current code to run rsync reads
C:\cygwin\bin\rsync.exe -qrtz --password-file=/secret > --delete "/cygdrive/e" boss@192.168.1.10::bossbackup 

I am getting told that permission is being denied to E:/System Volume Information/ 

However, even with --exclude "/cygdrive/e/System Volume Information"  I am still getting the same issues.

Any ideas?
[Chris]("http://allaboutchris.co.uk")

---

