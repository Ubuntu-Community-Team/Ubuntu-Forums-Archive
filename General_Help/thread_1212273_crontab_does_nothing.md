---
title: "crontab does nothing"
date: 2009-07-13
forum: General Help
---

### Post by castawaybcn on 2009-07-13
Hi,
I have looked in the forums for this but nothing I tried seems to work at all.
I am trying to run a script with cron but it does not seem to honour my request although running the script from the command line works as expected. Perhaps some of you can tell me what I am doing wrong.

My crontab is as follows:
```
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
40 19 * * * /home/francesc/Desktop/missatge.sh
55 20 * * * /home/francesc/Custom_Scripts/missatge.sh >> /tmp/command-output.txt

```
I keep on changing the times to check for modifications, but nothing happens at the expected times, and the text file is not created at all.

The crontab for my user exists, when I try
```
crontab -l
```
I get
```
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
40 19 * * * /home/francesc/Desktop/missatge.sh
55 20 * * * /home/francesc/Custom_Scripts/missatge.sh >> /tmp/command-output.txt
```

However, when I check if the cron daemon is running:
```
ps -ef | grep [c]ron
```
it returns this:
```
francesc  5981  4734  0 20:26 pts/1    00:00:00 crontab -e
francesc  5982  5981  0 20:26 pts/1    00:00:00 /bin/sh -c /usr/bin/sensible-editor /tmp/crontab.UL8ar0/crontab
francesc  5983  5982  0 20:26 pts/1    00:00:00 /bin/sh /usr/bin/sensible-editor /tmp/crontab.UL8ar0/crontab
francesc  5984  5983  0 20:26 pts/1    00:00:00 /bin/nano /tmp/crontab.UL8ar0/crontab
francesc  6229  4734  0 20:36 pts/1    00:00:00 crontab -e
francesc  6230  6229  0 20:36 pts/1    00:00:00 /bin/sh -c /usr/bin/sensible-editor /tmp/crontab.gyv1W1/crontab
francesc  6231  6230  0 20:37 pts/1    00:00:00 /bin/sh /usr/bin/sensible-editor /tmp/crontab.gyv1W1/crontab
francesc  6232  6231  0 20:37 pts/1    00:00:00 /bin/nano /tmp/crontab.gyv1W1/crontab
francesc  6233  4734  0 20:37 pts/1    00:00:00 crontab -e
francesc  6234  6233  0 20:37 pts/1    00:00:00 /bin/sh -c /usr/bin/sensible-editor /tmp/crontab.JwPSq9/crontab
francesc  6235  6234  0 20:37 pts/1    00:00:00 /bin/sh /usr/bin/sensible-editor /tmp/crontab.JwPSq9/crontab
francesc  6236  6235  0 20:37 pts/1    00:00:00 /bin/nano /tmp/crontab.JwPSq9/crontab
francesc  6237  4734  0 20:37 pts/1    00:00:00 crontab -e
francesc  6238  6237  0 20:37 pts/1    00:00:00 /bin/sh -c /usr/bin/sensible-editor /tmp/crontab.WXPdM3/crontab
francesc  6239  6238  0 20:37 pts/1    00:00:00 /bin/sh /usr/bin/sensible-editor /tmp/crontab.WXPdM3/crontab
francesc  6240  6239  0 20:37 pts/1    00:00:00 /bin/nano /tmp/crontab.WXPdM3/crontab
root      6812     1  0 21:04 ?        00:00:00 /usr/sbin/cron
```

It seems like there is way too many entries to me. Perhaps I have been playing around with it for too long...

Any help will be highly appreciated

---

### Post by HotForLinux on 2009-07-13
Is missatge.sh executable (has it got the +x flag in the permissions)?

You should post the output of

ls -l /*<el_seu_directori>*/missages.sh

You should probably start over again. Either log out or kill all those processes. Maybe you are not saving ok after editing your crontab.

For debugging purposes you will probably like to execute the following in a separate terminal:
> 
watch -n  10 -d cat  /tmp/command-output.display
It will constantly display the contents of the output file (reloading  every 10 secs) until you interrupt it (Ctrl-C)

Also, when you edit your crontab file, you can use:

> 0-59 19     * * *     ...... lo que sigui .....to run it every minute from 19 to 20 hrs. So you don't have to be changing the stub every time you modify something and want to try it.

---

### Post by castawaybcn on 2009-07-13
I think it does have the x flag... your code returns
```
-rwxr-xr-x 1 francesc francesc 67 2009-07-12 13:56 /home/francesc/Desktop/missatge.sh

```
I also changed my crontab following your instructions (I should have thought about the every minute option myself...) Unfortunately no file is created, and I am assuming it is cron not running. The message displayed is:
```
cat: /tmp/command-output.display: No such file or directory

```
I noticed something which was a bit odd though, I installed gcrontab (don't ask why) but when I run it the path to the bash file shows strange characters instead of the actual path. Could ext4 have something to do with this? Perhaps having my home in an encrypted partition is the cause of this? Tomorrow I will change the script's location and tell you about it.

Thanks a lot for you time

PS It's funny how far one goes to find help and how close it happens to be ;) salut

---

### Post by HotForLinux on 2009-07-13
I can't believe *cron* is not running.

I don't think ext4 has anything to do with the problem. But if the partition is encrypted I don't know. Maybe that hides the path to the files. It sounds reasonable, but I don't see why the jobs in your crontab should not be done.

I can tell you a few things that should work:

If you execute
```

ps aux|grep cron

```in the output you should see a line showing cron's process
```

[COLOR=Red]root      6610  0.0  0.0   2104   892 ?        Ss   Jul14   0:00 /usr/sbin/cron[/COLOR]
usuari   23296  0.0  0.0   3008   776 pts/2    S+   02:09   0:00 grep cron
 


```EPA! I see you already posted a line that shows cron running

Anyway,
This crontab should work without any problem

```

***crontab -l***
# m h  dom mon dow   command
0-59 17-21  * * * /home/usuari/MISSATGE.SH

```using this script:

```

***dir MISSATGE.SH ***
-rwxr-xr-x 1 usuari admin 48 2009-07-13 22:40 MISSATGE.SH

``````

***cat MISSATGE.SH ***
#!/bin/bash
echo "$(date) - MISSATGE.SH ha escrit aixó" >> /tmp/MISSATGE.LOG

```Just change "usuari" and  "0-59 17-21" according to your case and needs and watch the output of your changes in a separate terminal with:

```
[I][B]
watch -d cat /tmp/MISSATGE.LOG[/B][/I]

```[B]

Note:[/B] _The man pages suggest that you leave a blank line at the end of your crontab file._


....a St. Gervasi/Gràcia, noi!

---

### Post by t4thfavor on 2009-07-13
to edit the crontab did you type "crontab -e" 

If the scripts need root then you will have to sudo su.

I don't have any of the PATH stuff, and my crontabs still work. I just write out the full path in my crontab. Also if you redirect output of your command to a text file you can watch tail -n 50 mylog.log and  check your output.

---

### Post by castawaybcn on 2009-07-14
no luck still...
I created the script and modified the crontab as you suggested (I believe). Here's what I have so far:

Check that cron is running:
```

**ps aux|grep cron**
root      2933  0.0  0.0   3480   884 ?        Ss   19:08   0:00 /usr/sbin/cron
francesc  6988  0.0  0.0   3336   780 pts/0    D+   19:55   0:00 grep cron
```

your script (contents):
```
**cat MISSATGE.SH**
#!/bin/bash
echo "$(date) - MISSATGE.SH ha escrit aixó" >> /tmp/MISSATGE.LOG
```

your script (x flag):
```
**ls -l MISSATGE.SH** 
-rwxr-xr-x 1 francesc francesc 78 2009-07-14 19:32 MISSATGE.SH
```

the crontab pointing to your script (added a blank line as suggested, did not need to change the hours):
```

**crontab -l**
# m h  dom mon dow   command
0-59 17-21  * * * /home/francesc/MISSATGE.SH
```

finally check for changes in the log file
```
**watch -d cat /tmp/MISSATGE.LOG**
cat: /tmp/MISSATGE.LOG: No such file or directory

```
And it stays like this for no matter how long I wait, so it seems cron is not running after all.

Will try moving the script out of the encrypted partition and see if it helps. Checked, it does not make any difference at all :(

...Poble Sec!

---

### Post by castawaybcn on 2009-07-14
> **t4thfavor said:**
> to edit the crontab did you type "crontab -e"
yes, what else could I have done?  

> If the scripts need root then you will have to sudo su.
Good point, but they don't need to be run as root, I was just testing with some dummy script to check if cron worked

> I don't have any of the PATH stuff, and my crontabs still work. I just write out the full path in my crontab. Also if you redirect output of your command to a text file you can watch tail -n 50 mylog.log and  check your output.
Neither did I before, but since in Jaunty cron no longer worked for me (clean install) I tried many things, this was just one of them.

---

### Post by HotForLinux on 2009-07-14
> And it stays like this for no matter how long I wait, so it seems cron is not running after all.Nooo! [FONT=monospace]c[/FONT]ron IS running, according to the output of

```
ps aux|grep cron
``` that you posted.
The test I suggested is very simple. So it seems that you are right and something (but something else) is not working ok. It seems that you understand well what you are doing but just to be more sure:

i) Try creating the empty  file /tmp/MISSATGE.LOG
```
touch /tmp/MISSATGE.LOG
```and then execute ***watch***. SO that you don't see the screen flooded with "file doesn't exist" messages that might hide somehting.

ii) 
```
0-59 17-21  * * *  .... el que sigui ....
```in your crontab means the script will be executed every minute from 17 to 21 hrs
Are you sure your sytem was running during that period of time and that you watched the contents of MISSATGES.LOG during or after that period of time?

I really don't know if there can be a problem with the encryption. I don't know if cron can't read your script (I suppose that the encrypted partition is only your /home partition) but that sounds very strange to me.

You can also check if there are any error messages sent to the standard error when executing the crontab line by redirecting them to the same MISSATGE.LOG file.

```
0-59 17-21  * * * /home/francesc/MISSATGE.SH **2> MISSATGE.LOG**
```P.S.
Com han canviat les coses!
Quin bon nivell d'anglès al Poble Sec!!
Jo anava molt pel carrer Rosal i tal... i no era així, ni de bon tros.


[COLOR=Red]**Edit:**[/COLOR] You can also see the last footprints CRON left in syslog ***/var/log/syslog*** and/or ***/var/log/syslog.0*** when reloading your crontabs after editing them and when trying to execute the commands in there right on time.

Per exemple:
```
***cat /var/log/syslog | grep -i cron***
[COLOR=Gray]*... sripped ...*[/COLOR]
Jul 15 11:49:31 elmeupc anacron[6261]: Will run job `cron.daily' in 5 min.
Jul 15 11:49:31 elmeupc anacron[6261]: Jobs will be executed sequentially
[COLOR=Gray]*... sripped ...*[/COLOR]
Jul 15 11:49:32 elmeupc /usr/sbin/cron[6298]: (CRON) INFO (Running @reboot jobs)
Jul 15 11:54:31 elmeupc anacron[6261]: Job `cron.daily' started
Jul 15 11:54:31 elmeupc anacron[6826]: Updated timestamp for job `cron.daily' to 2009-07-15
[COLOR=Gray]*... sripped ...*[/COLOR]
Jul 15 12:15:28 elmeupc crontab[7879]: (usuari) LIST (usuari)
Jul 15 12:17:01 elmeupc /USR/SBIN/CRON[7905]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 15 12:17:20 elmeupc crontab[7912]: (usuari) BEGIN EDIT (usuari)
Jul 15 12:19:22 elmeupc crontab[7912]: (usuari) REPLACE (usuari)
Jul 15 12:19:22 elmeupc crontab[7912]: (usuari) END EDIT (usuari)
Jul 15 12:19:27 elmeupc crontab[8029]: (usuari) LIST (usuari)
Jul 15 12:20:01 elmeupc /usr/sbin/cron[6298]: (usuari) RELOAD (crontabs/usuari)
Jul 15 12:20:02 elmeupc /USR/SBIN/CRON[8051]: (usuari) CMD (/home/usuari/MISSATGE.SH)
* [COLOR=Gray]... sripped ...[/COLOR]*
Jul 15 12:41:01 elmeupc /USR/SBIN/CRON[9805]: (usuari) CMD (/home/usuari/MISSATGE.SH)
Jul 15 12:42:01 elmeupc /USR/SBIN/CRON[9887]: (usuari) CMD (/home/usuari/MISSATGE.SH)
Jul 15 12:43:01 elmeupc /USR/SBIN/CRON[9984]: (usuari) CMD (/home/usuari/MISSATGE.SH)
Jul 15 12:44:01 elmeupc /USR/SBIN/CRON[10063]: (usuari) CMD (/home/usuari/MISSATGE.SH)
Jul 15 12:45:01 elmeupc /USR/SBIN/CRON[10150]: (usuari) CMD (/home/usuari/MISSATGE.SH)

```

---

### Post by castawaybcn on 2009-07-15
I think we are getting closer. Actually I just got home and started a post asking where I could see the cron logs when I saw your post!
The last bit of the syslog shows errors, but I don't know what they mean at all:
 ```
15 21:50:20 francesc-desktop anacron[3792]: Updated timestamp for job `cron.daily' to 2009-07-15
Jul 15 21:51:01 francesc-desktop kernel: [  357.226199] cron[3814]: segfault at 0 ip 00000000 sp bfd80b9c error 4 in cron[8048000+8000]
Jul 15 21:52:01 francesc-desktop kernel: [  417.265916] cron[3816]: segfault at 0 ip 00000000 sp bfd80b9c error 4 in cron[8048000+8000]
Jul 15 21:53:01 francesc-desktop kernel: [  477.287879] cron[3818]: segfault at 0 ip 00000000 sp bfd80b9c error 4 in cron[8048000+8000]
Jul 15 21:54:01 francesc-desktop kernel: [  537.309252] cron[3819]: segfault at 0 ip 00000000 sp bfd80b9c error 4 in cron[8048000+8000]
Jul 15 21:55:01 francesc-desktop kernel: [  597.315078] cron[3822]: segfault at 0 ip 00000000 sp bfd80b9c error 4 in cron[8048000+8000]
Jul 15 21:56:01 francesc-desktop kernel: [  657.364793] cron[3824]: segfault at 0 ip 00000000 sp bfd80b9c error 4 in cron[8048000+8000]
```

This is starting to be way over my head. Any ideas? I was thinking of installing gnome-scheduler, but it just does not seem the way to go...

Dude, thanks so much for helping me out with this!!

EDIT:
it seems the encrypted partition has something to do with this. I found [some]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=870413") [posts]("http://ubuntuforums.org/showthread.php?t=820909&page=2") through which I found this [bug]("http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg104407.html"). Fixed it as instructed in the last link and I think I got rid of the error messages in /var/log/syslog and/or /var/log/syslog.0
However, the script still does not work... Any further suggestions will be highly welcome

PS. El barri ha canviat força, però jo fa poc que hi visc. Millor t'envio un MP i ho comentem fora del fil ;)

---

### Post by HotForLinux on 2009-07-15
How long have you been using this system? Have you upgraded? When did you started to use the encrypted filesystem for that volume?? Does everything else work fine? (I suppose it does)

If you examine the syslogs do you see any other segfault messsages not related with cron?
For this, you can use:
[I][B]cat /var/log/syslog | grep -i segfault | grep -v cron

[/B][/I][COLOR=Red]EDIT[/COLOR]: 
Would it be easy for you to create a new account (with its home dir not encrypted) in order to see if all that happens with another user? 


The problem here:
[http://ubuntuforums.org/showthread.php?t=820909&page=2](http://ubuntuforums.org/showthread.php?t=820909&page=2)
doesn't seem to be your case. That guy couldn't switch from root to himself because his directory was encrypted. But he was not using the user crontab, he was editing /etc/crontab, which is the system crontab. The jobs there are executed as root. But his job should be executed as himself

But from there I read in another forum:
[I]"I recently discovered that since I changed the pam configuration to include pam_mount, none of the predefined cron jobs and no [[COLOR=blue][FONT=Verdana][FONT=Verdana]user[/FONT][/FONT][/COLOR]]("https://www.linuxquestions.org/questions/#") cron jobs were executed anymore.
---
I get error messages in /var/log/auth.log saying:

Sep  4 17:37:01 localhost CRON[6621]: pam_mount: error trying to retrieve authtok from auth code"[/I] 

Is that your case? Do you know if you are using pam_mount?
In that case it seems that you should NOT include pam_mount in some generic pam file (e.g. /etc/pam.d/common-*). You should only enable it for xdm/gdm and login config files.

---

### Post by castawaybcn on 2009-07-16
I installed the system a couple of weeks ago, and everything seems to be working fine. But to be honest I have not put it to any tough tests since I am going (slowly) step by step and dealing with every problem I come across as well as documenting all the process. You probably know this, but there isn't that much documentation in Catalan.

I am at work now and cannot test anything from here, will do so as soon as I get back home, most likely this evening. In the meanwhile:

All errors are cron related, or at least so it seems, I just took a quick look before leaving home (but I was quite asleep, so I will double check this too later on) 

I do use pam_mount, and I am not entirely sure what I should add in the configuration file, but will investigate. However, I don't think gdm needs any access to it since the partition is mounted at login, but I could be wrong.

Creating a user with a different location for its home folder sounds good, I actually wanted to create a guest user (without password) so that eventual visitors (I get a few) could use my computer safely and could safely and easily try gnu/linux for themselves. Any suggestions on where to create that folder? I was thinking some random folder in the root directory, but I also have another ext4 partition that could use.

Thanks a million for your time and support!

---

### Post by HotForLinux on 2009-07-16
I don't know if I will be able to help you much more. I'm just an average experienced user and I have never used encryption. It doesn't seem like a way to start from zero.

> "but there isn't that much documentation in Catalan."
Nope, but ....I'm sure that's not a problem for you, is it?.....or ...are you taking notes because you are planning to write documentation in Catalan?

Are you using a separate partition for /home or is all the system in the same partition?
What is encrypted: the whole partition or a directory?


I don't think that having the guests folder inside the root partition (/) is the best idea, if you have other partitions. What for? The first thing you should know is how much disk space they will need. 1GB seems more than enough. They can save a whole CD, or maybe they should be able to sava a DVD? 
But they can always use /tmp for a boot-time disposal
The decision may depend strongly on the amount of HD space you have got.

There's no need, but you could also have the guests directory in the /home even if it the whole is encrypted.

But now, for debugging and testing purposes, it doesn't matter, you can create it in / or in -tmp for one day. Do you k now how?

---

### Post by castawaybcn on 2009-07-16
> HotForLinux;7625508]I don't know if I will be able to help you much more. I'm just an average experienced user and I have never used encryption. It doesn't seem like a way to start from zero.

Dude, you've helped a lot so far! And you are right, encryption does not seem to be an easy starting point but, you know, easy does not always mean fun ;)

About the scripts you suggested:
```
cat /var/log/syslog | grep -i segfault | grep -v cron
```
returns nothing, but
```
cat /var/log/syslog | grep -i segfault

```returns
```
Jul 15 23:08:01 francesc-desktop kernel: [   66.392130] cron[3600]: segfault at 0 ip 00000000 sp bfeadccc error 4 in cron[8048000+8000]
Jul 16 08:10:01 francesc-desktop kernel: [  373.807405] cron[3614]: segfault at 0 ip 00000000 sp bf98cfac error 4 in cron[8048000+8000]
Jul 16 08:11:01 francesc-desktop kernel: [  434.450556] cron[3782]: segfault at 0 ip 00000000 sp bf98cfac error 4 in cron[8048000+8000]
Jul 16 08:12:01 francesc-desktop kernel: [  494.456219] cron[3787]: segfault at 0 ip 00000000 sp bf98cfac error 4 in cron[8048000+8000]
Jul 16 08:13:01 francesc-desktop kernel: [  554.459535] cron[3925]: segfault at 0 ip 00000000 sp bf98cfac error 4 in cron[8048000+8000]
Jul 16 19:56:01 francesc-desktop kernel: [ 1415.387585] cron[5160]: segfault at 0 ip 00000000 sp bff9ddbc error 4 in cron[8048000+8000]
Jul 16 19:57:01 francesc-desktop kernel: [ 1475.393497] cron[5239]: segfault at 0 ip 00000000 sp bff9ddbc error 4 in cron[8048000+8000]
Jul 16 19:58:01 francesc-desktop kernel: [ 1535.398901] cron[5321]: segfault at 0 ip 00000000 sp bff9ddbc error 4 in cron[8048000+8000]
Jul 16 19:59:01 francesc-desktop kernel: [ 1595.404688] cron[5382]: segfault at 0 ip 00000000 sp bff9ddbc error 4 in cron[8048000+8000]
Jul 16 20:00:01 francesc-desktop kernel: [ 1655.425362] cron[5450]: segfault at 0 ip 00000000 sp bff9ddbc error 4 in cron[8048000+8000]
Jul 16 20:01:01 francesc-desktop kernel: [ 1715.715112] cron[5724]: segfault at 0 ip 00000000 sp bff9ddbc error 4 in cron[8048000+8000]
Jul 16 20:02:02 francesc-desktop kernel: [ 1775.720612] cron[5805]: segfault at 0 ip 00000000 sp bff9ddbc error 4 in cron[8048000+8000]
Jul 16 20:03:02 francesc-desktop kernel: [ 1835.725782] cron[5888]: segfault at 0 ip 00000000 sp bff9ddbc error 4 in cron[8048000+8000]
Jul 16 20:04:02 francesc-desktop kernel: [ 1895.732934] cron[5968]: segfault at 0 ip 00000000 sp bff9ddbc error 4 in cron[8048000+8000]
Jul 16 20:05:02 francesc-desktop kernel: [ 1955.737976] cron[6038]: segfault at 0 ip 00000000 sp bff9ddbc error 4 in cron[8048000+8000]

```

Oops, I already wrote about the previous one, didn't I?

Also,
```

cat /var/log/auth.log
```
returns (stripped until the first error, which seems to happen every ten minutes)

```
Jul 16 20:30:01 francesc-desktop dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.33" (uid=1000 pid=3422 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.51" (uid=0 pid=7848 comm="/USR/SBIN/CRON "))
Jul 16 20:30:02 francesc-desktop CRON[7848]: pam_unix(cron:session): session closed for user root
Jul 16 20:31:01 francesc-desktop CRON[8061]: pam_unix(cron:session): session opened for user francesc by (uid=0)
Jul 16 20:32:01 francesc-desktop CRON[8142]: pam_unix(cron:session): session opened for user francesc by (uid=0)
Jul 16 20:33:01 francesc-desktop CRON[8188]: pam_unix(cron:session): session opened for user francesc by (uid=0)
Jul 16 20:34:01 francesc-desktop CRON[8246]: pam_unix(cron:session): session opened for user francesc by (uid=0)
Jul 16 20:35:01 francesc-desktop CRON[8292]: pam_unix(cron:session): session opened for user francesc by (uid=0)
Jul 16 20:36:01 francesc-desktop CRON[8339]: pam_unix(cron:session): session opened for user francesc by (uid=0)
Jul 16 20:37:01 francesc-desktop CRON[8385]: pam_unix(cron:session): session opened for user francesc by (uid=0)
Jul 16 20:38:01 francesc-desktop CRON[8441]: pam_unix(cron:session): session opened for user francesc by (uid=0)
Jul 16 20:39:01 francesc-desktop CRON[8488]: pam_unix(cron:session): session opened for user francesc by (uid=0)
```

so it is related with cron, but I don't understand exactly how.


For the encrypted /home partition I followed [this]("http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu") tutorial with the main differences being:
[LIST]
[*]I did not encrypt (yet) swap and tmp
[*]/home is taking an entire partition, not just a folder somewhere
[/LIST]

I think the /home partition for the guest user should be somewhere else (why not / btw? that's where /home is by default anyway...) since the entire /home directory is the encrypted partition. I could also use another partition where I store data I would not mind loosing that much.
I will give it a couple of goes and see what happens. I would create a new user the gui way (sorry) from Gnome: System>Administration>Users and Groups>Add user, but perhaps you could suggest a better way (is there a way to limit their disk usage?).

However, the [post]("https://www.linuxquestions.org/questions/debian-26/pammount-prevents-cron-from-working-debian-sarge-360100/") you mentioned seems like a reasonable think to try (although I am scared as hell to touch any config files...)

A very stupid additional question, when I do:
```
ls -l MISSATGE.SH
-rwxr-xr-x 1 francesc francesc 78 2009-07-14 19:32 MISSATGE.SH 
```
shouldn't that actually be:
```
-rwxr-xr-x 1 francesc [COLOR="Red"]root[/COLOR] 78 2009-07-14 19:32 MISSATGE.SH
```

> Nope, but ....I'm sure that's not a problem for you, is it?.....or ...are you taking notes because you are planning to write documentation in Catalan?

No it is not, but it may be for others. I am taking notes for myself, but there is some sort of a plan there, and once I have something with a certain quality I will make it public. That's one of the ways I contribute to Free Software, translating (I also test and submit bugs)

**EDIT:**
I tried sending you a Private Message, but sadly my post count is not high enough...

---

### Post by HotForLinux on 2009-07-16
> easy does not always mean funHa, ha, ha,....that's right.


If
```
at /var/log/syslog | grep -i segfault | grep -v cron 
```returns 0 lines, you know what it means, don't you?. It means that all the segfault (segmentation fault) error messages  appear only when the word cron is in the same message.

If you use your fantastic dictionary and choose the "Free on-line dictionary of computing", you will read:

> Segmentation fault
 
 An error in which a running Unix program attempts to access
 memory not allocated to it and terminates with a segmentation
 violation error and usually a core dump.which leaves you as you were before. But a program is trying to read/write in an area in memory where it shouldn't.

The **auth.log** is stripped, I understand you don't want to post all of it, so maybe you should look for some kind of errors related to your crontab activity, using ***grep*** and using what you know about the times you do the tests. In your post everything seems fine except for the first line which I don't have a clue what's about.
You can see  that every minute, cron logs the same message. It was probably doing the crontab jobs, MISSATGE.SH probably.
If you want to stop that cron job for a period of time, you don't need to delete the line, just add an # at it's  beginning.
Cron runs as root, but every time it has to do a job as a different user it starts a 'session' as that user. You can also find messages corresponding to your session in gdm (when you logged in the graphical interface) and to each time you use sudo to execute a command as the root user.

Dictionary again for PAM:
> Pluggable Authentication Module
 
 <security> (PAM) The new industry standard integrated login
 framework. PAM is used by system entry components, such as
 the Common Desktop Environment's to authenticate
 users logging into a Unix system. It provides pluggability
 for a variety of system-entry services. PAM's ability to
 stack authentication modules can be used to integrate
 login with different authentication mechanisms such as
 RSA, DCE and Kerberos, and thus unify login mechanisms.
 PAM can also integrate smart card 
 White paper ([http://www.gr.osf.org/book/psm-wppr.htm](http://www.gr.osf.org/book/psm-wppr.htm)).
 
 [OSF-RFC 86.0 V. Samar, R. Schemers, "Unified Login with
 Pluggable Authentication Modules (PAM)", Oct 1995].
 > I think the /home partition for the guest user should be somewhere else (why not / btw? that's where /home is by default anyway...) since the entire /home directory is the encrypted partition. I could also use another partition where I store data I would not mind loosing that much.No, your /home directory is not where / is. Your home directory is inside the root (/) directory in a "logical way" (the way you map it) but the way you installed Ubuntu (as I understand): home/ is one partition and / is another partition. For Linux is more or less as if they were storing their contents in different disks or volumes, but builds a map (when mounted), the whole tree, and puts them together.

You can post the output of:

```

sudo fdisk -l

[COLOR=Gray]and[/COLOR]

[COLOR=Red]**df -hT**       (edit)[/COLOR]

```to see how you have distributed the space in the disk(s)

The normal thing is to have all users' directories inside the /home directory. All in one partition. All except root who has his directory /root/ at the same level as /home/, in the tree, not inside, and most often in a different disk partition because is considered as part of the system, for many good reasons.

If you have the guest/ directory, like francesc/ inside /home/ they will both be encrypted (goes a little slower) but you will lose nothing and I suppose that you know that you can easily restrict all kind of access to each others directories.

If you want to use a new and different partition for the guest you will always save less disk space, because the free space cannot be shared. It sounds strange but it's like that. It's more or less the same principle of an assurance company (mutua). In that case I suggest that you make a directory 'guest/' inside home/ and use that new directory as the mounting point for the new partition's filesystem.

With Linux you can do almost everything. You can give disk quotes to users. But that doesn't make sense if they are not going to share partitions and, most likely,  you already made your home partition without that feature. Just make the new partition the size you want to give to your guest/ folder. Everything they save will be saved there so they won't be able to surpass that space.


> (although I am scared as hell to touch any config files...That's wht is good go little by little and you will gain confidence.
You can always make a backup of the file you want to edit. 

sudo cp file_name file_name.bkup-castawaybcn

If something goes wrong you must be able to boot with the recovery option in the grub menu and fix things. In the worst case you can boot with the live CD, mount the partition where the file is (I don't know what problems you may have if it's encrypted) and restore the backup file.

---
> A very stupid additional question, ....Come on!... questions are never stupid. Can be basic, but never stupid. Everything has it's starting point and grows


That would take too long to explain because there are many many little things related to permissions.
But don't worry that's the usual thing to do. What is important is that:

1. in the sudoers file:

/etc/sudoers

you have permission to do ALL commands as ALL users from ALL computers as long as you identify yourself with after executing 

sudo command
(and identifying yourself)

you can read the manual with

man sudo
and
man sudoers

If you were in the group root that would be almost like being root and that's dangerous. You can switch to root and do whatever you want but years of experience have proven that many many mistakes and problems can be avoided like this. Especially for non expert users.


2. You are in the groups that have special permissions to do certain things comfortably without having to ask permission to the administrator, or having to do sudo.You can see the groups you are in like this:

user@mypc:~$ **id**

---

### Post by castawaybcn on 2009-07-17
hi again, good tips on your previous post. Some I knew but some seem very handy and had never used them.

Back to my little (although quickly growing) struggle with cron and pam.
So far I have tried editing some files in /etc/pam.d but with no luck so far. I did make a backup copy of all of them so I can get the original ones in case (and just to double check I also copied them in a separate partition in case I seriously mess something up):

**common-account**
did not find anything relevant here, the only uncommented lines (with explanations) are:```

# here are the per-package modules (the "Primary" block)
account	[success=1 new_authtok_reqd=done default=ignore]	pam_unix.so 
# here's the fallback if no module succeeds
account	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
account	required			pam_permit.so
```

**common-auth**
Here I changed the original line:
```
auth	optional	pam_mount.so use_first_pass
```
for:```

auth	optional	pam_mount.so enable_pam_password
```
Since sometimes while running su I got an error like "unknown option use_first_pass".
Actually, should I just REMOVE/comment out the previous line?
The only other uncommented lines in this file are just like those in common-account

**common-pammount**
same modification as in the previous one, just to get rid of the occasional errors. The only other uncommented line here is:
```
session    optional   pam_mount.so
```

**common-password**
nothing related to pammount here

**common-session**
did not change anything in this one, uncommented lines:
```
# here are the per-package modules (the "Primary" block)
session	[default=1]			pam_permit.so
# here's the fallback if no module succeeds
session	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
session	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
session	required	pam_unix.so 
session	optional	pam_mount.so 
session	optional			pam_ck_connector.so nox11
```

Finally, in the files: login, gdm & cron I added:
```
@include common-pammount
```

as instructed in /usr/share/doc/libpam-mount/README.Debian.gz

Actually, I forgot about the cron file!!! Rebooting as you may be reading this to check if anything worked at all (just to make sure, I know probably logging out & in again would do the trick)

EDIT:
good try but no cigar... Will keep on trying :X

---

### Post by castawaybcn on 2009-07-17
Ok, it seemed to me that there are some duplicate instructions in the configuration files, so I removed (commented out, actually) the lines:

in **common-session**
```
session	optional	pam_mount.so 
```

in **common-auth**
```
auth	optional	pam_mount.so enable_pam_password
```

since those lines are already in common-pammount, which I believe is called by the necessary modules (cron, gdm, etc.) through:
```
@include common-pammount
```

I don't know if any of this makes any sense to you, but it definitely does not for my crontab which insists in not running and keeps on providing segfault errors instead ](*,)

---

### Post by HotForLinux on 2009-07-17
I'm not sure if it is very important to save the backup of the files you touch in a different partition. If something goes 'out of mother' and you can't boot the system in the normal way you will have to gain access to both partitions with an external system (live cd) or selecting the recovery option in grub's menu.
The only thing I don't know is how can you restore files  when the partition is encrypted and you are doing it from another system (like the live cd) or installing the hard disk in another pc.
I think that _you should start studying this issue_. Boot from the live cd and also boot choosing the recovery option and see how can you access your encrypted partitions. You should study how to mount manually (with the command line) and see how (if you need to give a passwd or what) you can read and write files three.

You already have the original files in /usr/share/. Just do:
> locate common-account | xargs ls -l
locate common-auth | xargs ls -l
[COLOR=DimGray]etc.[/COLOR]
----

[B]common-auth:
[/B]No idea about what you should do. But [that explanation]("http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg104407.html") suggested to chainge the value (it's a parameter passed to pam_mount.so) not to omit it.  But if you add a line, or change it, it's better to comment out the line you don't want, to explain when/why/who did it and then to add a new line as you want it and to comment that you added it,  when and why?

[B]common-pammount:
[/B]_WHY??_ 
I understand that you should make exactly the same change. 

> [COLOR=DimGray]Have:[/COLOR]
auth      optional                  pam_mount.so enable_pam_password
[COLOR=DimGray]instead of:[/COLOR]
auth   optional     pam_mount.so use_first_pass
With these two files modified you should have eliminated the following error message everytime yo su to root. Maybe when you sudo too. > pam_mount(pam_mount.c:100): unknown pam_mount option "use_first_pass"_Have you?_ You don't get that error message any more? 

**login, gdm & cron**:
I don't have that README file.

**Uy, uy, uy!,...**
I don't know but I would never delete the lines in one file just because they are in another. That's not a good reason. I don't think they would do any harm even if they were duplicated in the same configuration file.

You can always ask [Lars,]("http://blog.gnist.org/users.php?mode=profile&uid=2") the author of the guide you followed to encrypt.

---

### Post by HotForLinux on 2009-07-17
In Lars instructions thre's somehting that sounds strange to me and I think it must be wrong. I'm not sure but you should check it out:

It says:
>  # **cat /etc/fstab**
...
/dev/mapper/cryptoswap /tmp    swap   sw    0 0[FONT=monospace]
[/FONT]/dev/mapper/cryptotmp   none   ext2   defaults 0 0
...


and maybe it should be:
> 
# **cat /etc/fstab**[FONT=monospace][/FONT]
...
/dev/mapper/cryptoswap  none     swap    sw    0 0
[FONT=monospace][/FONT]/dev/mapper/cryptotmp   /tmp    ext2   defaults 0 0
...



And /dev/sda2 should be the partition you want to use for swap: /dev/sda(x) or /dev/hda(x) depending on how is called in your system.

>  **cat /etc/cryptab**

cryptoswap /dev/sda2 /dev/urandom cipher=aes-cbc-essiv:sha256,size=256,hash=sha256,swap 

- Your swap partitios should be 1.5  to 2.0 times the size of your RAM

- This for  a home of 20GB, but maybe you want a different size> lvcreate -L20G -nlv_home vg_storage

etc. There may be many things that you want to make differently. Di you follow exactly what is said or you changed it according to your system and your needs?

---

### Post by castawaybcn on 2009-07-18
**About Lars' tutorial:**
I did not encrypt swap nor tmp, just /home. And I did adjust the tutorial to fit my needs too. For instance I changed the routes, and since I used an entire partition instead of a folder
```
lvcreate -L20G -nlv_home vg_storage 
```
did not apply, so I skipped that bit
My abilities are slightly over identifying partitions in a nix system, but just slightly ;)

**About /etc/pam.d files**
Yes, I did get rid of this error:
```
pam_mount(pam_mount.c:100): unknown pam_mount option "use_first_pass"
```
So far this is the only improvement in the whole situation, but I am quite happy about it.

What I understood from the help file is that you can tell a module (cron for instance) to look into the configuration in **common-x** by adding a line in the module's config file like **@common-x**. That's what I meant with "duplicate" instructions, but I could be perfectly wrong.

I also took a look at
```
man pam_mount(8)
```
and it could be something with the order in which the parameters are passed, and perhaps pam_mount should be before any of those. I will revert some changes and give it a go. 
 
This is the contents of the help file in /usr/share/doc/libpam-mount/README.Debian.gz btw:
> Installation on a Debian system
===============================
For every application used for logging in, there is a file
of the form /etc/pam.d/xyz, for example:
/etc/pam.d/{login,xdm,gdm,kdm}.

In most cases you can add the following line at the
end of the file:
@include common-pammount
This activates the file /etc/pam.d/common-pammount which you can
customize (see the file comments for more info).
You can also add the required pam_mount module lines manually, for
example to have different options for each application.
See the pam_mount(8) man page for more info about this option.

Now edit the global configuration file /etc/security/pam_mount.conf.xml
and add the volumes you want to mount upon login.
If you enable the "luserconf" entry in /etc/security/pam_mount.conf.xml,
every user can specify their own mounts in $HOME/.pam_mount.conf.xml
User-specified volumes are mounted under the logged in user, not as root.

Some PAM modules require a mounted home directory (eg.
pam_gnome_keyring used in gdm). These modules have to be moved
after the common-pammount include if home directories are mounted.

All changes to the files /etc/security/pam_mount.conf.xml and /etc/pam.d/*
take effect on the next login. The next time a login shell is started,
any new configured volumes will be read and mounted.


Required packages for specific mount types
==========================================
All the packages below are suggested, however you might
not need all of them to successfully use libpam-mount.

Mount type			Required packages
-------------------------------------------------
Samba (smbfs)			smbfs
NetWare (ncpfs)			ncpfs
LUKS or Dm-crypt (crypt)	cryptsetup, openssl, psmisc, fuser
cryptoloop			openssl, cryptoloop-source (for 2.4 kernels)
Fuse (fuser)			fuse-utils
Truecrypt (truecrypt)		no official package available
WebDAV (davfs)			davfs2

All filesystems also require the appropriate kernel support.
See /proc/filesystems for a list of supported filesystems of the
current kernel.


Example: LUKS encrypted home partition
--------------------------------------
The LUKS disk encryption format is supported with cryptsetup >= 1.0.3.
Generate a LUKS partition with:
$ luksformat -t ext3 /dev/hda8
Then, add an entry like this:
<volume user="test" mountpoint="~" path="/dev/hda8" fstype="crypt"
 options="exec,fsck,nodev,nosuid" />


Example: dm-crypt encrypted home partition
------------------------------------------
The root user has to initialize the filesystem with mkfs before
mounting it the first time.
$ dd if=/dev/urandom bs=1c count=32 | \
  openssl enc -aes-256-ecb > /home/test.key
enter aes-256-ecb encryption password: <enter your login password>

Note: keep a backup of the .key file! All your encrypted data will
be inaccessible and therefore lost if the .key file is damaged!

The cryptsetup -s option needs bits, not bytes, ie. it has to have
32*8=256 as argument.
$ openssl enc -d -aes-256-ecb -in /home/test.key | \
  cryptsetup -c twofish -h sha512 -s 256 create _dev_hdb8 /dev/hdb8
enter aes-256-ecb decryption password: <enter your login password>

You can use any file system type; in this example it is xfs.
$ mkfs -t xfs /dev/mapper/_dev_hdb8
$ cryptsetup remove _dev_hdb8

Then add a line like this into pam_mount.conf.xml:
<volume user="test" mountpoint="~" path="/dev/hdb8" fstype="crypt"
 fskeycipher="aes-256-ecb" fskeypath="/home/test.key"
 options="exec,fsck,nodev,nosuid,fstype=xfs,cipher=twofish,hash=sha512,keysize=256"
/>

Since this mounts the users home directory, you should change the
PAM level from "optional" to "required" in /etc/pam.d/common-pammount.


Example: Loopback encrypted home partition
------------------------------------------
The root user has to initialize the filesystem with mkfs before
mounting it the first time:
$ dd if=/dev/urandom of=/home/test.img bs=1M count=<image size in MB>
$ dd if=/dev/urandom bs=1c count=32 | \
  openssl enc -aes-256-ecb > /home/test.key
enter aes-256-ecb encryption password: <enter your login password>

Note: keep a backup of the .key file! All your encrypted data will
be inaccessible and therefore lost if the .key file is damaged!

The cryptoloop module is not loaded automatically. Otherwise you
can get the infamous Unix-ish loop device error message
"ioctl:LOOP_SET_STATUS: Invalid argument".
To defeat that, load the module manually:
$ modprobe -q cryptoloop

The losetup -k option needs bits, not bytes, ie. it has to have
32*8=256 as argument.
$ openssl enc -d -aes-256-ecb -in /home/test.key | \
  losetup -e aes -k 256 -p0 /dev/loop0 /home/test.img

You can use any file system type; in this example it is ext3.
$ mkfs -t ext3 /dev/loop0
$ losetup -d /dev/loop0

Then add a line like this into /etc/security/pam_mount.conf.xml:
<volume user="test" mountpoint="~"
 path="/home/test.img" fstype="ext3"
 fskeycipher="aes-256-ecb" fskeypath="/home/test.key"
 options="exec,fsck,nodev,nosuid,loop,encryption=aes,keybits=256" />

Since this mounts the users home directory, you should change the
PAM level from "optional" to "required" in /etc/pam.d/common-pammount.


Notes and bugs
--------------
- If you use SSH, you have to adjust /etc/ssh/sshd_config like this:

  UsePAM yes
  UsePrivilegeSeparation no
  ChallengeResponseAuthentication no
  PasswordAuthentication yes

- Does not work properly with most (all?) ssh implementations
  + openssh-server and the old ssh-krb5 mount ok, but do not unmount
    see bug:
    [http://bugs.debian.org/372680](http://bugs.debian.org/372680)
  + lsh-server does not work at all; it does not use PAM

- Only works with gksu when debugging is disabled. Be sure to set
  "debug 0" in /etc/security/pam_mount.conf.xml if you use gksu.

And you are right again, I should be investigating on how to access my encrypted partition outside of the system...

An heretic thought:
Not that I am giving up on this at all but: could this be a bug or a miss-implementation of libpam? Of course I could have done something wrong when I followed Lars' tutorial (although I am positive I did not get any error messages) But the current situation does not make much sense to me, that is: I encrypt my /home and then I cannot run user crontabs :confused:

However, may this be a bug or not, I am learning a lot here. And I am certain all of it will be very helpful in times to come

PS: I did contact Lars and also left a comment on the tutorial page. No replies yet, but I don't think I should expect any yet since it's just been a few hours.

---

### Post by HotForLinux on 2009-07-18
And /? ..Is it encrypted?

Yes, you should start knowing or getting used to how you can replace a file booting from the recovery option in grub's menu and from a live cd too.  Maybe you should do that before anything else.

Now, when you boot from the recovery option, another menu is displayed and you have to choose to boot as root or something like that. You are going to find yourself as root with a root prompt in a console.

[B][COLOR=Red]_Edit_:
[/COLOR][/B][maybe you are asked for a root passwd. If you are asked for root's passwd and you don't know it, then boot normally and in the term and type:

*sudo passwd*   or   *su -c passwd*

introduce your passwd when asked (in the first case only) and then you can change root's passwd when you are prompted]

You just need to do that to be sure you can copy and replace files, edit files with nano, make dirs, unmount partitions and mount them again from the console and with the live system too. And later you should see how can you do that in the home partition (you will probably have to mount it manually with the correct options more or less like it is in the fstab.)


But if you don't have the root partition, /, encrypted then there's no additional trouble: you would work on it as always, as everybody,..in a normal way. Just do it  once to try and feel it. You can replace a file with its backup and the system should boot. The changes in the /home partition won't affect the system boot and I don't think you are doing any changes there.



Anyway:

I understood that[B]
common-pammount:
[/B]                                                 > [COLOR=DimGray]Have:[/COLOR]
 auth      optional                  pam_mount.so enable_pam_password
 [COLOR=DimGray]instead of:[/COLOR]
 auth   optional     pam_mount.so use_first_pass                      --

Your personal crontabs, edited with ***crontab -e***, are saved in the /var/ directory which I don't think you have encrypted so I don't see why the problem with the crontabs. But anyway,  If you don't have the / partition encrypted and you want to create a temporary test user in order to check if he can do crontabs without problem when he doesn't have his directory in the encrypted home partition then do:


> 
sudo useradd  [COLOR=Blue]-m[/COLOR]  [COLOR=DarkRed]--base dir /[/COLOR]  [COLOR=Blue]--home testuser[/COLOR]  [COLOR=DarkRed]testuser[/COLOR]
-------
[B][I]
/usr/share/doc/libpam-mount/README.Debian.gz[/I][/B]:

1. I don't understand this very well, but it seems important:
> 
"Some PAM modules require a mounted home directory (eg.
 pam_gnome_keyring used in gdm). These modules have to be moved
 after the common-pammount include if home directories are mounted."[U]
What did you do about it?


[/U]2.  _Are you sure you have installed the mentioned "Mount type Required packages"_?
use **dpkg -l** *package_name* to check that.
You should see a "ii" at the left.


3.
> "Then, add an entry like this:
<volume user="test" mountpoint="~" path="/dev/hda8" fstype="crypt"
 options="exec,fsck,nodev,nosuid" />"I think it means that should be in the file **pam_mount.conf.xml**
_What did you do about it?_


4. And what about this? (I don't know if it is for LUKS):

> "- Only works with gksu when debugging is disabled. Be sure to set
  "debug 0" in /etc/security/pam_mount.conf.xml if you use gksu. [U]What did you do about it?



[/U]

---

### Post by castawaybcn on 2009-07-20
Sorry for taking so long in writing back, I am rather busy at work at the moment. I will try to answer your questions the best I can

> And /? ..Is it encrypted?
no it isn't

That's right, in **common-pammount** I changed:
```
auth optional pam_mount.so use_first_pass
```
to: 
```
auth optional pam_mount.so enable_pam_password
```
About:
> "Some PAM modules require a mounted home directory (eg.
pam_gnome_keyring used in gdm). These modules have to be moved
after the common-pammount include if home directories are mounted."
I did nothing actually, a few configuration files are created: atd, chfn, chsh, common-account, common-auth, common-pammount, common-password, common-session, cron, cups, gdm, gnome-screensaver, login, other, passwd, polkit, ppp, samba, su & sudo.

Here's the contents of /etc/pam.d/cron:
```
#
# The PAM configuration file for the cron daemon
#

@include common-auth
auth       required   pam_env.so
@include common-account
@include common-session
# Sets up user limits, please define limits for cron tasks
# through /etc/security/limits.conf
session    required   pam_limits.so

```
At the end I added:
```
@include common-pammount
```

> Are you sure you have installed the mentioned "Mount type Required packages"[/U]?
use **dpkg -l** *package_name* to check that.
You should see a "ii" at the left.
No I am not, I just installed the packages Lars suggested, which package should I list?

About **pam_mount.conf.xml** you suggest this
```
<volume user="test" mountpoint="~" path="/dev/hda8" fstype="crypt"
options="exec,fsck,nodev,nosuid" />" 
```
but what I did was something closer to what Lars suggested:
```
<volume user="myusername" fstype="crypt" path="/dev/sda9" mountpoint="/home" />
```
Mount options are defined in the same file, later on:
```
<mntoptions allow="nosuid,nodev,loop,encryption,fsck,nonempty,allow_root,allow_other" />
```

About:> 
"- Only works with gksu when debugging is disabled. Be sure to set
"debug 0" in /etc/security/pam_mount.conf.xml if you use gksu. 
I do not use gksu, at least that I am aware of, so I did nothing at all.

Will try creating the user both in the encrypted partition and in / and see what happens. And also will try accessing the partition from the command line or logging in as root, but this second bit may very well be tomorrow. 

Thanks for the patience and support!

**EDIT:**
btw, I just found [this link]("https://wiki.kubuntu.org/JauntyJackalope/Beta/Kubuntu/Feedback"). It is a bit old and actually is about kubuntu, but I think this line would explain some things:
> cron segfaults reproducibly when executing user crontabs when libpam-mount is installed; as this also happens with libpam-mount 0.41, it probably is a bug in libpam.

---

### Post by HotForLinux on 2009-07-22
> # Sets up user limits, please define limits for cron tasks
# through /etc/security/limits.confWhat about the contents of these limits file? Is there a limit?

2.
> Are you sure you have installed the mentioned "Mount type Required packages"[/u]?
use **dpkg -l** *package_name* to check that.
You should see a "ii" at the left.In the README Debian file, there's a section where it says:

> Required packages for specific mount types
==========================================
All the packages below are suggested, however you might
not need all of them to successfully use libpam-mount.

Mount type            Required packages
-------------------------------------------------
Samba (smbfs)            smbfs
NetWare (ncpfs)            ncpfs
LUKS or Dm-crypt (crypt)    cryptsetup, openssl, psmisc, fuser
cryptoloop            openssl, cryptoloop-source (for 2.4 kernels)
Fuse (fuser)            fuse-utils
Truecrypt (truecrypt)        no official package available
WebDAV (davfs)            davfs2

All filesystems also require the appropriate kernel support.
See /proc/filesystems for a list of supported filesystems of the
current kernel.Therefore you should check if you have them installed with

> dpkg -l libpam-mount smbfs ncpfs cryptsetup openssl psmisc fuser openssl[COLOR=Gray]*...etc....*[/COLOR]davfs2You will see a "**ii**" code at the left of each installed package.

3. Is not my suggestion:

> Example: LUKS encrypted home partition
--------------------------------------
The LUKS disk encryption format is supported with cryptsetup >= 1.0.3.
Generate a LUKS partition with:
$ luksformat -t ext3 /dev/hda8
Then, add an entry like this:
<volume user="test" mountpoint="~" path="/dev/hda8" fstype="crypt" options="exec,fsck,nodev,nosuid" />

is on the README and I just wanted to know if you used it, and how, in your PC.
It seems important because you are using a LUKS encrypted partition.
What you did sounds ok but maybe you are missing the

> options="exec,fsck,nodev,nosuid" />"I don't know but maybe the "nosuid" option is important.


> options="exec,fsck,nodev,nosuid" />"Yes, sounds like it's the case. Have you looked if there's a web for LUKS where it explains how to use it and its bugs?
But, it's not clear if it refers to a problem in KDE only. Are you using KDE?
You can check if you are using the same version of libpam-mount with [B][I]dpkg -l

[/I][/B]I haven't read them, but maybe you would like to read them:
[http://www.saout.de/tikiwiki/tiki-index.php?page=LUKS](http://www.saout.de/tikiwiki/tiki-index.php?page=LUKS)

It has links to:
[https://help.ubuntu.com/community/EncryptedFilesystemHowto3](https://help.ubuntu.com/community/EncryptedFilesystemHowto3)
[http://oei.yungchin.nl/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/](http://oei.yungchin.nl/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/)
says that is not so simple to get access to the encrypted partition from the recovery tools.

---

