---
title: "No /etc/inittab in 11.04 where to put?"
date: 2011-12-30
forum: General Help
---

### Post by thomo2710 on 2011-12-30
Hi all,

Im following a guide on setting up 2 way text messaging through MYSQL and Nagios.

However i have come a little unstuck and my newb linux knowledge has run out!

[COLOR=Red]Guide states:

Now we need to start the daemon.  This daemon controls storing the  messages in the backend database, as well as sending the message.

Ideally we want the SMS Daemon to restart whenever it stops.   We can  accomplish this by using an entry in the /etc/inittab.  Here is what my  entry reads:[/COLOR][LEFT]
[LIST=1]
[*][FONT=Courier New][COLOR=Red]# Setup the SMS Daemon[/COLOR][/FONT]
[*][FONT=Courier New][COLOR=Red]sm:345:respawn:/usr/local/bin/smsd.sh[/COLOR][/FONT]
[/LIST]
[COLOR=Red]Now the contents of the [/usr/local/bin/smsd.sh script]("http://matt.bottrell.com.au/plugin/dlfile_7") are as follows:[/COLOR]
[LEFT]
[LIST=1]
[*][FONT=Courier New][COLOR=Red][COLOR=#808080]*#!/bin/sh*[/COLOR][/COLOR][/FONT]
[*][FONT=Courier New][COLOR=Red][COLOR=#000066]export[/COLOR] [COLOR=#0000ff]LANG=[/COLOR]en_US[/COLOR][/FONT]
[*][FONT=Courier New][COLOR=Red]/usr/bin/gammu smsd MYSQL /etc/smsdrc [/COLOR][/FONT]
[/LIST]


[/LEFT]
[COLOR=Black]Now i dont have the /etc/inittab directory in Ubuntu 11.04[/COLOR]


[COLOR=Black]It then goes on to say:[/COLOR]


[COLOR=Red]If you don't have an /etc/inittab file you may be running upstart.  If  that's the case, you can create a file (say smsd) and place it in the  /etc/event.d/ directory.

It would look like:[/COLOR] 
[LEFT]
[LIST=1]
[*][FONT=Courier New][COLOR=Blue]# smsd[/COLOR][/FONT]
[*][FONT=Courier New][COLOR=Blue]#[/COLOR][/FONT]
[*][FONT=Courier New][COLOR=Blue]# This service maintains the SMS Daemon from the point the system is[/COLOR][/FONT]
[*][FONT=Courier New][COLOR=Blue]# started until it is shut down again.[/COLOR][/FONT]
[*][FONT=Courier New][COLOR=Blue] [/COLOR][/FONT]
[*][FONT=Courier New][COLOR=Blue]start on runlevel 3[/COLOR][/FONT]
[*][FONT=Courier New][COLOR=Blue]start on runlevel 4[/COLOR][/FONT]
[*][FONT=Courier New][COLOR=Blue]start on runlevel 5[/COLOR][/FONT]
[*][FONT=Courier New][COLOR=Blue] [/COLOR][/FONT]
[*][FONT=Courier New][COLOR=Blue]stop on runlevel 0[/COLOR][/FONT]
[*][FONT=Courier New][COLOR=Blue]stop on runlevel 1[/COLOR][/FONT]
[*][FONT=Courier New][COLOR=Blue]stop on runlevel 2[/COLOR][/FONT]
[*][FONT=Courier New][COLOR=Blue]stop on runlevel 6[/COLOR][/FONT]
[*][FONT=Courier New][COLOR=Blue] [/COLOR][/FONT]
[*][FONT=Courier New][COLOR=Blue]respawn[/COLOR][/FONT]
[*][FONT=Courier New][COLOR=Blue]exec /usr/local/bin/smsd.sh [/COLOR][/FONT]
[/LIST]
Now i dont have an event.d directory either!


So i found this link
[https://help.ubuntu.com/community/UpstartHowto](https://help.ubuntu.com/community/UpstartHowto)


And put the script in /usr/local/bin and entered the info in as in the script above.


Then i put the above text in blue into a file called smsd and put that into /etc/init.d


However when i try to start the Daemon using the command in the guide
Those using upstart can use **sudo /sbin/initctl start smsd** to control the SMS deamon. Check it's running using **sudo /sbin/initctl status smsd**.


it throws and output of - initctl: Unknown job: smsd


I have noticed that most other files in the init.d directory are shell scritps where as mine just shows up as a text document!?



Can anybody tell me where i am going wrong and give me my linux lesson for the day?


Thankyou in advance for any time given.

[/LEFT]
[COLOR=Red]
[/COLOR]
[COLOR=Red][/COLOR]

[/LEFT]

---

### Post by thomo2710 on 2011-12-30
ok progress

following this thread on here
[http://ubuntuforums.org/showthread.php?t=1320803](http://ubuntuforums.org/showthread.php?t=1320803)

I am now in the same situation as the OP started in

My job now starts but upon running **sudo /sbin/initctl status smsd** gives me :
smsd stop/waiting

Is this designed behaviour as i dont really follow from the end of the post if it is or not?

---

