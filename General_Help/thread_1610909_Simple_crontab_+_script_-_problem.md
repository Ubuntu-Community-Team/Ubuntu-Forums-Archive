---
title: "Simple crontab + script - problem"
date: 2010-11-01
forum: General Help
---

### Post by tobytoby on 2010-11-01
Hello,
I am trying to get a folder with mp3:s being played every 2 minutes.
I am using crontab which starts a simple script. However, even though I get the script to run when i start the script from terminal, it starts with crontab every 2 minutes, but no songs get played (I know it gets started since the first line of the script  kills the vlc application and if I have any open vlc apps when the crontab starts, it closes down (but no songs are being played :(

I assume it is a really simple mistake I am doing. Anyway, here is the code:
(I start off by killing vlc in the script since otherwise I get a binding socket error the second time it runns. I assume there is another better/smoother way of doing it - pls suggest if so!)

Crontab:
*/2 * * * * /home/user1/folder/2min.sh

and the script 2min.sh:
#!/bin/bash
killall vlc
vlc /home/user1/folder2

---

### Post by Wobblybob on 2010-11-01
> **tobytoby said:**
> 
Crontab:
*/2 * * * * /home/user1/folder/2min.sh


Can't see anything obvious but you could add error checking to he end of the crontab to see what if anything it produces,


*/2 * * * * /home/user1/folder/2min.sh 2> /home/user1/folder/error.log

good luck

---

### Post by matt_symes on 2010-11-01
Hi

Your not running the job as root user are you?

Kind regards

---

### Post by efflandt on 2010-11-01
You have to understand that cron does not have your user environment, so it would not necessarily have your $PATH to find programs nor any clue where to display vlc.  So your script needs to use full paths or set any env variables itself.  Assuming that the crontab entry is your personal crontab and NOT root's crontab, try:

#!/bin/bash
 export DISPLAY=:0.0
killall vlc
/usr/bin/vlc /home/user1/folder2

---

### Post by tobytoby on 2010-11-01
Thanks that solved it!

---

### Post by tobytoby on 2010-11-01
Now, the 'killall vlc' command that used to work before is not working anymore. I suppose I somehow need to translate the discussion regarding environment to that command too?
Thanks in advance

---

### Post by gsgleason on 2010-11-01
try this:
kill `pidof vlc`

or:
if [[ x`pidof vlc` != "x" ]]; then
  kill `pidof vlc`
fi

---

### Post by DaithiF on 2010-11-01
> **tobytoby said:**
> 
(I start off by killing vlc in the script since otherwise I get a binding socket error the second time it runns. I assume there is another better/smoother way of doing it - pls suggest if so!)

There is indeed a better way -- the vlc developers went to the trouble of developing all kinds of interfaces to allow you to control the program in many ways -- command line included.

Take a look at this post for an example python script:
[http://ubuntuforums.org/showthread.php?t=1371622](http://ubuntuforums.org/showthread.php?t=1371622)

assuming you call it pyvlc, then you could call 
pyvlc next
or
pyvlc get_title
or
pyvlc is_playing
etc

You need to enable the RC (remote control) interface in the VLC preferences:  Tools -> preferences -> switch to 'Show All', then click on interface -> Main Interfaces -> RC, and check the 'Fake TTY' checkbox and enter a path to a socket (e.g. /tmp/vlc.sock) in the 'Unix socket command input' box.

---

### Post by roop_s on 2010-11-03
i was working on this for days and am glad i found this thread. my shell script worked fine from a terminal but it would not run from cron.

here's the crontab entry:

00 05 * * * bash /usr/local/bin/enc.sh > /dev/null 2&1
explanation here: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto) - bash is supposed to be infront of the script and the script should be in /usr/local/bin

next the script itself:

#!/bin/bash
for file in /home/user/rawfile/*.ts ; do /usr/local/bin/ffmpeg -i "$file" -vf crop=in_w-240:in_h:119:1080 -s 960:720 -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre medium -b 2000k -bufsize 3500k -maxrate 3000k -threads 0 ${file%.*}.mkv ; done

of course the input directory should be a full path but the program to run (ffmpeg) needs to be full path as well.

after all of this, crontab scheduling works!

---

