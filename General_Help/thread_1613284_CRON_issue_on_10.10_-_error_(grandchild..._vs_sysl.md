---
title: "CRON issue on 10.10 - error (grandchild... vs syslog"
date: 2010-11-04
forum: General Help
---

### Post by SiO-Buntu on 2010-11-04
Hi all,
Ive been all over this forum and saw a few similar issue, but not quite what i'm experiencing and no clear fix.

Since 10.10, a scripts that ive been using for many disto just ain't being launched anymore.

1) Cron is up and running at boot.

2) The script that ain't loading is the following in crontab:
[COLOR="Red"]6 9 * * * /home/User/Duplicity/Scripts/Duplicity-Automated-CRON-Script-V2.sh[/COLOR]

3) In SYSLOG I get this message:
[COLOR="Red"]Nov  4 09:06:01 Computer CRON[1892]: (root) CMD (/home/User/Duplicity/Scripts/Duplicity-Automated-CRON-Script-V2.sh          
Nov  4 09:06:01 Computer CRON[1890]: **(CRON) error (grandchild #1892 failed with exit status 127)**
[/COLOR]

Tried uninstalling/re-installing CRON as suggested in one tread, didn't work. Tried a few other suggestions I read on this forum with no luck.

Thanx alot for your help cause i'm out of ideas now...

Thx!

---

### Post by Hippytaff on 2010-11-04
I think Code 127 indicates a 'command not found error'. So is there a command in the script that is mistyped or something?
 
does it run outside of cron ok?

---

### Post by SiO-Buntu on 2010-11-04
Hi, thx for the quick reply.

Yes the script works fine if run by itself.
It dosen't even seems to start trough Cron tought.

(that that you tell me the CODE 127 is a command not found, I will create a simple script, "hello world" and see if the cron runs it OK)

Could this be a PERMISSION issue even tought this is run as ROOT?

Thx
BRB.

---

### Post by CharlesA on 2010-11-04
Redirect the output to a file and check it for errors:

```
6 9 * * * /home/user/Duplicity/Scripts/Duplicity-Automated-CRON-Script-V2.sh > /home/user/somefile 2>&1
```

See list of exit codes [here]("http://tldp.org/LDP/abs/html/exitcodes.html").

It's probably a matter of not having the full path to each command. Cron doesn't share the same environment as your user account.

---

### Post by Hippytaff on 2010-11-04
What does the script do? and has it ever worked with cron?
 
Don't think it's security, it's just getting confused about something :-)

---

### Post by SiO-Buntu on 2010-11-04
Hi,
I did a simple test, I set a simple CRON Job:
[COLOR="Red"]
49 9 * * * touch /home/User/Desktop/cron-test.txt #Cron test[/COLOR]

It didn't work. Got this message in the syslog:
[COLOR="Red"]
Nov  4 09:49:01 Computer CRON[1883]: (root) CMD (touch /home/User/Desktop/cron-test.txt #Cron test)
Nov  4 09:49:01 Computer CRON[1881]: (CRON) error (grandchild #1883 failed with exit status 1)[/COLOR]

Here are a few other info:

1) This seems happens only when the computer was rebooted without anyone signed in: Eg: I had the same "touch" cron job scheduled to be lauched while my User was logged in. It worked!  (the touch file appeared on my desktop!)  It only seem to fail when there are no users logged in.

Here's the log to prove my point:

[COLOR="SeaGreen"]Nov  4 09:56:01 Computer cron[1229]: (root) RELOAD (crontabs/root)
Nov  4 09:56:01 Computer CRON[4783]: (root) CMD (touch /home/User/Desktop/cron-test.txt  #Cron test)[/COLOR]

No errors...  
If no user is logged in, I got the grandchild error...

Does this help?
hummm....

Thx alot! Can't wait to hear from you.

---

### Post by CharlesA on 2010-11-04
Take out the comment.

Also, use the full path to the program you want to run.

---

### Post by SiO-Buntu on 2010-11-04
I removed the comment: Still got the issue:

1) 
[COLOR="Red"]Nov  4 10:04:01 Computer CRON[1799]: (root) CMD (touch /home/User/Desktop/cron-test.txt)
Nov  4 10:04:01 Computer CRON[1718]: (CRON) error (grandchild #1799 failed with exit status 1)
[/COLOR]

2) And there ain't no script anymore, I'm using a simple TOUCH command...
Ill try using the complete patch to touch (/usr/bin/touch).

Trying, brb.

---

### Post by CharlesA on 2010-11-04
FYI: Linux is case sensitive - User =|= user

---

### Post by SiO-Buntu on 2010-11-04
Bad news.
Even with the full path, I still get the error.

Cron job = 14 10 * * * /usr/bin/touch /home/User/Desktop/cron-test2.txt

syslog =  [COLOR="Red"]Nov  4 10:14:01 Computer CRON[1846]: (root) CMD (/usr/bin/touch /home/User/Desktop/cron-test2.txt)
Nov  4 10:14:01 Computer CRON[1844]: (CRON) error (grandchild #1846 failed with exit status 1)[/COLOR]

Works ony if my "User" is logged in and the cron job is due...
But I need this to run even if no user is logged in, like after a reboot.

Keep the suggestions coming. Thx for your help...

---

### Post by SiO-Buntu on 2010-11-04
No problem with case sensitive.
This was a Typo on my part. The user is always the same. I copy paste.

Thx.

---

### Post by CharlesA on 2010-11-04
Ok.

Do you have an ecrypted home directory?

---

### Post by SiO-Buntu on 2010-11-04
Yes!! I do!
I do have an encrypted home directory!
It's brand new in fact. Never had an encrypted directory before 10.10 !

You are on to something I believe...
How could this affect my cron?

---

### Post by CharlesA on 2010-11-04
It cannot access yer home directory if it's encrypted.

When you login, yer home directory is decrypted and accessible.

---

### Post by SiO-Buntu on 2010-11-04
I tried running the cron job as my "User" instead of root.
Didn't work.

What would be the fix for that?
The only thing I can think of, is to use the "login automatically" for my User... but I don't really want to do that.

Is there a way to "inform" the root about my encryption key for my /home/User so that root can access it ?

---

### Post by CharlesA on 2010-11-04
I don't know.

Only thing I know is that it's decrypted silently when you login.

---

### Post by elgordo123 on 2010-11-24
I know I'm way late to this - it sounds like you are running a script that is located in your home directory (or writing to your home directory).  Since you are not logged in and your home directory is encrypted it will not run nor will it read or write to that directory.   
One thing you could do is to put your script somewhere else, have it write somewhere else and setup a cron job as root.   

It's working as designed - you nor anyone else can read/write/access that encrypted directory unless you login.

---

### Post by WilliamVallance on 2012-01-28
[SIZE=3][FONT=Calibri]I just wanted to thank everyone who responded to this post. I found this topic by running a google search on the error. Your responses helped me to find the problem.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]If anyone wanted to know this was my problem. I set up a bash script to check if a particular program was running and if not then the command would run [/FONT][/SIZE]
```
invoke-rc.d myapp start
```
[SIZE=3][FONT=Calibri]After reading this topic I ran [/FONT][/SIZE]```
sudo find / -name “invoke-rc.d”
```[SIZE=3][FONT=Calibri] and then changed the script to reflect the location.[/FONT][/SIZE]
```
/usr/sbin/invoke-rc.d myapp start
```
 
[SIZE=3][FONT=Calibri]Thanks again to the awesome help that everyone gives on this forum.[/FONT][/SIZE]
[FONT=Calibri][FONT=Calibri][SIZE=3]-[/SIZE][/FONT] [/FONT][SIZE=3][FONT=Calibri]William[/FONT][/SIZE]

---

### Post by oldos2er on 2012-01-28
Closed, necromancy.

---

