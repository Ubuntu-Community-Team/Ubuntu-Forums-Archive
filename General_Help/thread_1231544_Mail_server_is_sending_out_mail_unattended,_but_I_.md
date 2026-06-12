---
title: "Mail server is sending out mail unattended, but I can't see how?  Have I been hacked?"
date: 2009-08-04
forum: General Help
---

### Post by greavette on 2009-08-04
Hello,

We use a mail server in our office (Citadel.org).  We use Thunderbird as our front end running on our Windows XP employee PC's.  All mail in and out of our office goes through our mail server.  Our mail server connects to our ISP mail through POP.

The Mail server lives on an Ubuntu Hardy VM in VMware.  All updates have been applied to the O/S and I regularly update the O/S.  The VM runs on a Windows 2003 Host Server.  The host server also has all updates applied.

We also use a security gateway (Untangle.com) in front of our network.  All traffic goes through this gateway.

Over the weekend here in Canada we had a long weekend with no one in the office.  I regularly review my reports from our security gateway and I noticed a lot of traffic from our Mail Server to one IP on port 110.  Like I said, no one was in the office so I immediately configured a firewall rule to block this port so now whatever is being sent is being blocked at my firewall.

Here's what else I've done:
[LIST]
[*]I changed my user password on my mail server.
[*]I was stupid enough to have root access through SSH still enabled.  I've turned this off now. in my sshd_config file.
[*]I'm now using AllowUser in my sshd_config for my userid
[/LIST]

I looked at my ssh log file on my mail server and this is what I saw:
```
Aug  3 00:17:01 citadel CRON[7750]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  3 00:17:01 citadel CRON[7750]: pam_unix(cron:session): session closed for user root
```

I'm no expert, but it looks like I have a cron job running in root.  So to be sure I used the following command to look at all my users cron jobs on my server:

```
for user in $(cut -f1 -d: /etc/passwd); do crontab -u $user -l; done
```

This command shows no crotab for any user?

So then I changed my directory to /etc/cron.d/ and using the ls command I see nothing in /etc/cron.d/.

I then used sudo su to login as root and used 'crontab -e' and this does not show any cron jobs running for root.

So now I'm confused...do I have a cron job running on my mail server?  If I do, why can't I find it?  

Any advice you can give to help me figure this out would be greatly appreciated.

---

### Post by greavette on 2009-08-04
Hello,

I've been searching some more.  I've looked in my /etc/cron* folders for any cron related tasks. I finally found in root the following jobs in /etc/cron.daily:

```
apt  aptitude  bsdmainutils  logrotate  man-db  mlocate  samba  standard  sysklogd

```

I have no idea what's an Ubuntu standard cron job and what may not be?

I then looked at "nano /etc/crontab" and I see the following entries:

```

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

```

I don't think anything looks out of place there?

I do see something that sounds funny...it's under my userid (not root) and it's crontab job called "popularity-contest".  I don't know what this is and I don't know how to look at it?  How do I view a crontab file in /etc/cron.weekly?

Thanks!

---

### Post by Glyndwr on 2009-08-04
A few points (hope they help!)

1. port 110 is for pop3 (grep 110 /etc/services) so that isn;t sending mail it's reading mail. To send mail the port is 25.

2. popularity-contest is a legitimate program, it's what the devs use to see which packages are used most often on your system (or something like that). It sends an email to the devs every so foten.

3.  Inside /etc/cron.weekly the files are just shell scripts, so just cd/etc/cron.weekly and less <filename>

4.  The crontabs for all the users should be in /var/spool/cron/crontabs

---

### Post by dcstar on 2009-08-05
> **Glyndwr said:**
> A few points (hope they help!)
........

And all mail activity is usually in /var/log.

---

