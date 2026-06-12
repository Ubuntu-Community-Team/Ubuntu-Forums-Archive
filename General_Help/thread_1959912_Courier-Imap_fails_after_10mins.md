---
title: "Courier-Imap fails after 10mins"
date: 2012-04-16
forum: General Help
---

### Post by jongers on 2012-04-16
Hi guys, I was wondering if someone could kindly help or point me in the correct direction.  I have recently virtualised my mail server running postfix, courier etc.  I have been running 10.04 64-bit for....well almost 2 years without a single issue.  Infact 120 Days uptime... since migrating to 12.04alpha 32-bit I am getting some strange issues with, what I think to be the Imap authentication.

I am currently always receiving emails, but after I reboot the machine I can only login to imap for 10mins or so.... I think it's been an hour or two also.  I then just can't authenticate with courier-imap.

There is absolutely no clue in the log, not even a message at the time the server fails, I've checked,  syslog, mail.log, mail.error dmesg and mysql.log.

I'm really stumped, 

Just a quick not more, if i reboot the server..... it's fine again for that short amount of time.  Imap-authentication would never activate correctly again, even if I restart the services..... when i do I get no errors from the services.:confused:


Thank you in advance for any help / pointers someone can give me, I guess the only issue might be the simple copy paste, I've done to convert the 10.04=64 to 12.04=32.  That shouldn't matter right?!?!

Thank you

---

### Post by ginoputrino on 2012-04-16
Hi,
   I'm not going to be of any help, except to say that this exact thing is also happening to me. imap works for a while (sometimes 10mins, sometimes a few hours), then stops responding.
I upgraded from 64-bit 11.10 to 64-bit 12.04 beta2.

Similar to you, there are no log messages, restarting the courier-imap services does not resolve the problem or create any log entries, there are no seg faults I can see in dmesg or any other log files, and the only way to "fix" the problem is to reboot the server.

I am using postfix as the email server if it makes any difference.

Anyone have any ideas?

---

### Post by jongers on 2012-04-17
Thank you for your addition, I will keep you updated if I get anywhere with this, I'm using postfix for the mail delivery also.  It's my understanding that courier is the access server, providing the imap service and authentication.

This is why i *think* the issue lies with that.   Because we are both using 12.04, perhaps there is in issue with the courier-imap that's in the repos.  I've been trying the trace any bugs, but to no avail im afraid.
I don't know if should file a bug report as I have no more information on the problem.

If anyone could provide some insight, or ideas on where to get some additional verbose information, I would be very greatfull.

---

### Post by jongers on 2012-04-18
UPDATE:  I think I have found the cause, or at least I've managed to keep the service from dying. 
It appears that when I use the roundcube config I've copied over the imap-service suffers issues.  If I only use IMAP clients, iphones, outlook, thunderbird etc. This doesn't happen any more it's been 24 hours a long enough test period to presume IMHO.


ginoputrino, are you using a web-client to access your email server?
I haven't had time to look into it, but I've noticed previously that roundcube authenticates a load of times during sessions, other clients only state a connection when they are downloading sending or updating mail.  

Perhaps there is a connection limit  imposed on the local interface? however this should be logged.  Local firewall connection limits might also be to blame.

I am going to reinstall and reconfigure roundcube to see if I get an improvement, I will post my results.




[]("http://ubuntuforums.org/member.php?u=1616283")

---

### Post by jongers on 2012-04-18
.

---

### Post by ginoputrino on 2012-04-18
Hey Jongers,
    I do have squirrelmail on the server. However, it hardly ever gets used.

Having said that, I've given it a go, and attempting to use the squirrelmail web client definitely does crash imap straight away. So squirrelmail doesn't work at all

But I'm not sure that the other times imap has crashed for me corresponds with squirrelmail being used.

But I think we can say that whatever the problem is, it seems to be aggravated by web clients.

I'll play around with my squirrelmail set up and post here if I notice anything else.

---

### Post by ginoputrino on 2012-04-18
OK,
  I went through my logs, and it does seem to fail every time squirrelmail is used. 

The times that I thought it wasn't was due to search engine crawls triggering squirrelmail.

So web clients are definitely exercising some new bug in 12.04.

This is going to be a serious problem, and really needs to get fixed before 12.04 goes live. But I can't find any error logs to raise an issue with.

---

### Post by jongers on 2012-04-19
I don't think it's safe to say there is definitely a bug, however it does appear that way.  Because of the multiple requests they require, web clients might be exhausting the number of connections? or the server might be failing to start a new process once they have been exhausted?.

Pure speculation I must add.
Going to get onto Google and see, with the 12.04 final deadline looming........ better file a possible bug report.

J

---

### Post by ginoputrino on 2012-04-24
Hey Jongers,

Someone may have found the solution to this.
See here: [https://bugs.launchpad.net/ubuntu/+source/courier/+bug/890756](https://bugs.launchpad.net/ubuntu/+source/courier/+bug/890756)

I'm going to give this a try, and see if the problem remains.

---

### Post by ginoputrino on 2012-04-26
Can confirm that this solves the problem.

sudo apt-get install fam 
sudo apt-get install courier-imap courier-imap-ssl

(second command might not be necessary if courier-imap isn't uninstalled by the first command.)

---

### Post by jongers on 2012-05-04
> **ginoputrino said:**
> Can confirm that this solves the problem.

sudo apt-get install fam 
sudo apt-get install courier-imap courier-imap-ssl

(second command might not be necessary if courier-imap isn't uninstalled by the first command.)


Thanks for posting your fix, I will give it a go, I already had the courier services installed but not fam,

Ill post the results.

J

---

### Post by jongers on 2012-05-04
> **jongers said:**
> Thanks for posting your fix, I will give it a go, I already had the courier services installed but not fam,

Ill post the results.

J


Great,
Looks like it's worked a charm, Thanks for the Heads up.   I was on my way to a complicated rebuild.  However I probably would have come across the same issues.  

FAM is something I have never knowingly used,

From the [http://packages.ubuntu.com/hardy/fam](http://packages.ubuntu.com/hardy/fam)

FAM monitors files and directories, notifying interested applications of changes.  This package provides a server that can monitor a given list of files and notify applications through a socket.  If the kernel supports dnotify (kernels >= 2.4.x) FAM is notified directly by the kernel. Otherwise it has to poll the files' status.  FAM can also provide an RPC service for monitoring remote files (such as on a mounted NFS filesystem). 	  

Thanks
Again:)

---

