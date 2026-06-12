---
title: "Reboot Ubuntu when php/mysql server stop"
date: 2012-08-25
forum: General Help
---

### Post by icaka92 on 2012-08-25
Hello. I am using ubuntu 12.04 to host 1 site on it. I have a problem. On 2-3 days the site stop work, and i lose my internet connection to the server and I can't reboot it. Are there any way when detect that something is wrong to reboot it?

I have some ideas with ping, but I am not sure that this will help me.

Thanks !

---

### Post by 2F4U on 2012-08-25
What about monitoring applications such as Nagios or Icinga?

---

### Post by SeijiSensei on 2012-08-25
When the computer goes down, what is the problem?  Are you simply losing network connectivity?  Does the machine just hang?  Perhaps your provider has a dicey network setup or bad power?  

Yes, you could write a simple script in bash that uses ping to check network connectivity and reboots when needed.  Something like:

```

#!/bin/bash

TEST=$(ping -c 5 www.google.com | grep 'packet loss' | awk '{print $6}')

if [ "$TEST" != "0%" ]
then 
   /sbin/shutdown -r now
else 
   exit 0
fi

```

Set up a cronjob as root to run this script every few minutes.  However I'd do some experimentation first to see if there are transient network outages.  This script reboots whenever five pings fail to connect to Google.  If the provider has bad connectivity, your server might be rebooting too frequently.  You might then want to increase the count from five to, say, fifteen.

For a test, run this process on the server:
```
sudo ping -c 9999999 -i 5 www.google.com /var/log/pingtest &
```

Let it run for a couple of days, then examine /var/log/pingtest.

---

### Post by icaka92 on 2012-08-25
Hello. I don't know from where is the problem (internet connection or mysql/php server).I am newbie in ubuntu and I hear Nagios and Icinga for the first time :|

I don't know how to up a cronjob too. Now i have only remote access to the server with file zilla and putty access. I try to run:

sudo ping -c 9999999 -i 5 [www.google.com]("http://www.google.com") /var/log/pingtest &
but I receive this:

ping: unknown host /var/log/pingtest

---

### Post by SeijiSensei on 2012-08-26
Oops, I forgot to "pipe" the results to the file.  Use this instead:

```
sudo ping -c 9999999 -i 5 www.google.com > /var/log/pingtest &
```

The ">" tells the shell to send the output of the ping command to the file /var/log/pingtest.  The "&" at the end of the line tells the shell to run the job "in the background."  It will start the ping job, then return you to the shell prompt while the job continues running.  You can watch the job progress by running "**sudo tail -f /var/log/pingtest**".

As for running a cron job, read this: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by icaka92 on 2012-08-28
Now the server stop work again. I try to run :

```
sudo ping -c 9999999 -i 5 [www.google.com]("http://www.google.com/") > /var/log/pingtest &
```in putty and i receive:

```
ico@ico-desktop:~$ sudo ping -c 9999999 -i 5 www.google.com > /var/log/pingtest &
[1] 2264
ico@ico-desktop:~$ -bash: /var/log/pingtest: Permission denied

[1]+  Exit 1                  sudo ping -c 9999999 -i 5 www.google.com > /var/log/pingtest

```

Where is the problem? Must I create this file, before try to view log ?

Thanks !

---

### Post by sid0972 on 2012-08-28
permission is denied
maybe sudo has to be replaced with gksudo

---

### Post by icaka92 on 2012-08-28
The same: "Permission denied" :???:

---

### Post by SeijiSensei on 2012-08-28
Oh, I see what's wrong.  If you haven't used sudo before running this command, then you don't have the opportunity to enter your password and get root privileges.  Try this instead:

```

$ sudo su -
[enter your password]
# ping -c 9999999 -i 5 www.google.com > /var/log/pingtest &
# exit

```

Alternatively, you can avoid sudo entirely by piping the results to a file in your own home directory:

```
$ ping -c 9999999 -i 5 www.google.com > ~/pingtest &
```

will create the file pingtest in your home directory and avoid the permissions problem.  That's the better solution, to be honest.  (Just to avoid confusion, don't type the "#" or "$" characters.  They're the prompts you'll see in the shell; the hash prompt means you are running as root.)

Have you asked the hosting company why this is happening?  Did they report any problems right before your system went away?

---

### Post by icaka92 on 2012-08-29
Thanks ! I run sudo su and after that i run:

```
ping -c 9999999 -i 5 www.google.com > /var/log/pingtest &
```and now work. I see file pingtest. 

I host site on my own server :)

Now when the server stop again i will see that write on log file and will comment it here to help me.

Thanks again !

---

### Post by Mr.Dee on 2012-08-29
I guess if the internet goes down the machine will be continuosly restarting until the internet is back up.

---

### Post by SeijiSensei on 2012-08-29
Are you talking about my original [script]("http://ubuntuforums.org/showpost.php?p=12195344&postcount=3")?  I suggested he run it from cron on a regular schedule like every five or ten minutes.  It will run when invoked and either reboot the machine or do nothing until invoked again.  It doesn't loop, if that is what you mean.  The frequency of retries depends entirely on the configuration in crontab.

The reason I suggested he first run the ping job was to get some idea about the frequency of network drops, if that is the problem.  If the network has brief interruptions, say less than a minute every now and then, then setting a relatively high frequency in crontab like every five or ten minutes makes sense.  If the network goes away for hours at a time, you might want to run the script every 30 or 60 minutes.

The problem may have absolutely nothing to do with network connectivity at all.  If it's a hardware fault, like bad memory, it might show up in /var/log/syslog.

---

### Post by icaka92 on 2012-08-30
The server go down now. I reboot it manual, but in pingtest log file there are nothing interesting.

```
64 bytes from muc03s02-in-f19.1e100.net (173.194.35.179): icmp_req=2721 ttl=4 time=42.5 ms
```Nothing else.

The interesting is that i can't connect vie putty..

Any ideas ?

---

### Post by icaka92 on 2012-08-30
This is my syslog:

```
Aug 30 07:56:32 ico-desktop rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="782" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Aug 30 07:56:47 ico-desktop anacron[15948]: Job `cron.daily' terminated
Aug 30 07:56:47 ico-desktop anacron[15948]: Normal exit (1 job run)
Aug 30 08:09:01 ico-desktop CRON[16359]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Aug 30 08:09:01 ico-desktop CRON[16358]: (CRON) info (No MTA installed, discarding output)
Aug 30 08:17:01 ico-desktop CRON[16415]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 30 08:39:01 ico-desktop CRON[16523]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Aug 30 08:39:01 ico-desktop CRON[16522]: (CRON) info (No MTA installed, discarding output)
Aug 30 09:09:01 ico-desktop CRON[16684]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Aug 30 09:09:01 ico-desktop CRON[16683]: (CRON) info (No MTA installed, discarding output)
```And I am thinking that the server is down about 8-9 am.

---

### Post by icaka92 on 2012-08-31
The server again go down. This is my syslog:

```
Aug 31 08:00:39 ico-desktop anacron[6994]: Job `cron.daily' terminated
Aug 31 08:00:39 ico-desktop anacron[6994]: Normal exit (1 job run)
Aug 31 08:09:01 ico-desktop CRON[7412]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Aug 31 08:09:01 ico-desktop CRON[7411]: (CRON) info (No MTA installed, discarding output)
Aug 31 08:17:01 ico-desktop CRON[7449]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 31 08:39:01 ico-desktop CRON[7580]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Aug 31 08:39:01 ico-desktop CRON[7579]: (CRON) info (No MTA installed, discarding output)
Aug 31 09:09:01 ico-desktop CRON[7723]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Aug 31 09:09:02 ico-desktop CRON[7722]: (CRON) info (No MTA installed, discarding output)
Aug 31 09:17:01 ico-desktop CRON[7780]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 31 09:39:01 ico-desktop CRON[7890]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Aug 31 09:39:01 ico-desktop CRON[7889]: (CRON) info (No MTA installed, discarding output)
Aug 31 10:09:01 ico-desktop CRON[8055]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Aug 31 10:09:01 ico-desktop CRON[8054]: (CRON) info (No MTA installed, discarding output)
Aug 31 10:17:01 ico-desktop CRON[8112]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 31 10:39:01 ico-desktop CRON[8221]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Aug 31 10:39:01 ico-desktop CRON[8220]: (CRON) info (No MTA installed, discarding output)
Aug 31 11:09:01 ico-desktop CRON[8385]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Aug 31 11:09:01 ico-desktop CRON[8384]: (CRON) info (No MTA installed, discarding output)
Aug 31 11:17:01 ico-desktop CRON[8421]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 31 11:39:01 ico-desktop CRON[8552]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Aug 31 11:39:01 ico-desktop CRON[8551]: (CRON) info (No MTA installed, discarding output)
Aug 31 12:09:01 ico-desktop CRON[8739]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Aug 31 12:09:01 ico-desktop CRON[8738]: (CRON) info (No MTA installed, discarding output)
Aug 31 12:17:01 ico-desktop CRON[8775]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

---

### Post by SeijiSensei on 2012-08-31
It's pretty hard to tell from that, though I'd suggest you fix that problem with maxlifetime.  Either remove the job from cron, pipe the command's output to a file, or install an MTA like postfix or sendmail, 

If you have physical access to the machine, you should run memtest.  Random hangs like this often arise from faulty memory.

---

### Post by icaka92 on 2012-08-31
I will have physical access after a week. I have other idea. How to reboot the machine every hour ? It is not the decision, but for now i don't have other idea.

---

### Post by icaka92 on 2012-09-02
How can reboot my serve every 2 hours, because the reboot continuous about 2 minutes and it's not a problem for now.

---

### Post by SeijiSensei on 2012-09-02
Edit root's crontab like this:

```

sudo su -
[enter your password]
export EDITOR=nano
crontab -e

```

Now enter the line

```
0 */2 * * * /sbin/shutdown -r now
```

Make sure to terminate the line with a return, then hit Ctrl-S to tell nano to save the file and Ctrl-X to exit.  The crontab program should report that you have updated the file for root.  Type "exit" at the "#" prompt to return to your user session.

The first entry represents the top of the hour.  The second matches any hour divisible by two.  So the server will reboot at 00:00, 02:00, etc.

Read this for more details: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by icaka92 on 2012-09-07
Hello,

Now i have physical access. How to run memtest.

Thanks !

---

### Post by sid0972 on 2012-09-09
in the GRUB menu, where the OS list comes
select memtest86+
it is recommended that you run it for 6+ hours (opinions differ from person to person), but 2 complete passes are good i think

---

### Post by icaka92 on 2012-09-14
Is there a way to run it, when the machine work and on it is hosted 1 site, and if i run it the site will be down.

---

### Post by icaka92 on 2012-09-23
Is it possible ?

---

### Post by icaka92 on 2012-09-24
How to reconnect my internet connection with cron every hour ?

---

