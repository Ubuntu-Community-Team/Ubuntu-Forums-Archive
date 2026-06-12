---
title: "init.d script not running"
date: 2010-09-29
forum: General Help
---

### Post by UncleBoarder on 2010-09-29
I don't think any init.d files are running.  I've somehow stopped this from working.

I wrote a trackball script...

```
#!/bin/sh

# Button modification for my Microsoft Trackball Explorer

imwheel -k
xmodmap -e "pointer = 1 0 8 4 5 6 7 3 9 10 11 12 13 14 15 16"

```And copied it to init.d.
Then did update-rc.d trackball.sh defaults 98 02

It's not running at boot. But  I can run it manually.  I thought I could test it by doing 'init 5'

Is that a valid test?

Anyway it's not running and I don't know why.  I know it's not running because when I try to kill imwheel after boot (as a test) it's not running.

This worked before I reinstalled.

---

### Post by CharlesA on 2010-09-29
What you can try to do instead of throw it into a crontab with the time set to @reboot:

```
@reboot /path/to/script
```

---

### Post by psusi on 2010-09-29
Your script does not have the required header describing what runlevels it should run in, so I'm not sure why you would think it should run in runlevel 5.

---

### Post by UncleBoarder on 2010-09-29
There are 3 reasons I think it should run.

1) I don't know what I'm doing
2) It ran before
3) I tried adding a mkdir line as a test and in fact it created the directory

So that seems to say the script is running.  So now my problem is why isn't imwheel executing.

I can execute it as either myself or as root after the boot is completed.

If you have a suggestion, I'll try it.

---

### Post by CharlesA on 2010-09-30
Try using the full path.

---

### Post by jason.m on 2010-09-30
You might try adding the 'enable' argument to your update-rc.d routine:
 
 
*update-rc.d trackball.sh enable defaults* 
 
Although posts abound all say update-rc.d <script.sh> defaults should do the trick as well. And as psusi stated, you might want to copy the header information from another init script :) (thats how I cheat)
 
As for the run levels, I believe Debian based distributions have their multi-user w/ graphical environment set to stop at run level 2. ([http://en.wikipedia.org/wiki/Runlevel#Debian_Linux](http://en.wikipedia.org/wiki/Runlevel#Debian_Linux)) You can check which one your at currently at by entering:
 
*runlevel*
 
 
Cheers

---

### Post by psusi on 2010-09-30
My guess is that it is actually running, but failing.  I don't know about the first program, but the second talks to the X server, so it certainly won't work in an init script.  For one, the server might not be running by the time it is executed, and for another, it won't be able to find the server since it isn't being run from a child process with the environment set up correctly.

You might try redirecting the output to a log file and see what it says.

---

### Post by UncleBoarder on 2010-09-30
I like the idea of redirecting the output... can you give me a hand with that?

I'll try the other suggestions when I get home tonight.

---

### Post by CharlesA on 2010-09-30
```
/path/to/script > /path/to/home/somefile 2>&1
```

---

### Post by UncleBoarder on 2010-09-30
Added full path - no change
Tried using "enable" - it wouldn't create the scripts
You mentioned X hasn't started yet... it has by init 5 hasn't it?

And I don't understand your redirect.  How do I apply that to the init.d script?  The script is called by Ubuntu, not by me.  When I call the script it works perfectly.  So where do I put that redirect?

Here's what I tried...

```
ed@ubuntu:/$ cat /etc/init.d/trackball+
### BEGIN INIT INFO
# Provides:          grub-common
# Required-Start:    $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Record successful boot for GRUB
# Description:       GRUB displays the boot menu at the next boot if it
#                    believes that the previous boot failed. This script
#                    informs it that the system booted successfully.
### END INIT INFO
/usr/bin/imwheel > /redirect
ed@ubuntu:/$ cat /etc/init.d/trackball+
### BEGIN INIT INFO
# Provides:          grub-common
# Required-Start:    $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Record successful boot for GRUB
# Description:       GRUB displays the boot menu at the next boot if it
#                    believes that the previous boot failed. This script
#                    informs it that the system booted successfully.
### END INIT INFO
/usr/bin/imwheel > /redirect
``` [COLOR=DarkOrange]

[COLOR=Black]The "redirect" file WAS created... so that's good news, the script is running... **but it's empty!**  :-([/COLOR]
[/COLOR]

---

### Post by CharlesA on 2010-09-30
I don't know how you set it up, but it should look something like this:

/usr/bin/imwheel >> /path/to/file/ 2>&1

One of mine looks like this:

```
rr.sh > /dev/null 2>&1
```

---

### Post by UncleBoarder on 2010-09-30
I'm sorry, I don't understand.  You seem to be saying to place that redirect in my script.  Which as I posted, I already did.  So I must not be understanding you.

But if you're saying to do that command from the terminal window then that doesn't prove anything since that does work.

Can you explain a little more?  Where exactly would you have me place that command?  Did you see that I already put it in the script?

---

### Post by CharlesA on 2010-09-30
Yeah you placed it in there. If it doesn't have any output, it won't show anything.

What I suggest doing is sticking it in a crontab with the redirect and see if it spits back and errors.

```
sudo crontab -e
```

Add it with @reboot, and reboot.

---

### Post by UncleBoarder on 2010-09-30
Got it.  Man am I sorry... you guys have been so helpful and it was my fault.

I forgot that about a month ago while learning to configure imwheel, I added it as a startup application.  What I didn't realize is that the startup applications are apparently stored in /home... which I had relocated to my second drive.

So every time I reinstalled Ubuntu, I also remapped /home via fstab and imwheel always worked.  That is, until recently when I recopied a virgin /home and overwrote the call for the startup application.

All this time I thought it was the init.d script that was running imwheel but... it was a step I'd forgotten that I'd done.

I did learn a bit from this thread so thanks...

And sorry for the mistake.

---

### Post by CharlesA on 2010-09-30
Glad you got it working. :)

---

