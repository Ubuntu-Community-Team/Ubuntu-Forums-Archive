---
title: "Anacron doesn't know I changed computer's name"
date: 2009-10-23
forum: General Help
---

### Post by t0p on 2009-10-23
I changed my computer's name from ubunty to phobos.  Now, every day I receive this Delivery Failure Notification (it's sent to my gmail account because I've set up exim4 to send mail to the gmail account):

> This is an automatically generated Delivery Status Notification

Delivery to the following recipient failed permanently:

     root@ubunty

Technical details of permanent failure: 
DNS Error: Domain name not found

   ----- Original message -----

Received: by 10.103.126.12 with SMTP id d12mr4647203mun.40.1256293044313;
        Fri, 23 Oct 2009 03:17:24 -0700 (PDT)
Return-Path: <xxxxxxxx@googlemail.com>
Received: from phobos (xxxx.xxxxx.co.uk [xx.xx.xx.xx])
        by mx.google.com with ESMTPS id j10sm4105413mue.6.2009.10.23.03.17.21
        (version=TLSv1/SSLv3 cipher=RC4-MD5);
        Fri, 23 Oct 2009 03:17:23 -0700 (PDT)
Received: from root by phobos with local (Exim 4.69)
        (envelope-from <root@ubunty>)
        id 1N1HDb-0002oE-1t
        for root@ubunty; Fri, 23 Oct 2009 11:17:59 +0100
From: Anacron <xxxxxxxx@googlemail.com>
To: root@ubunty
Subject: Anacron job 'cron.daily' on phobos
Message-Id: <E1N1HDb-0002oE-1t@phobos>
Date: Fri, 23 Oct 2009 11:17:59 +0100

etc/cron.daily/debtags:
/etc/cron.daily/debtags: 4: debtags: not found
run-parts: /etc/cron.daily/debtags exited with return code 127
So, 2 problems here I'd like help with:

1. How do I tell anacron about the name change, so it will send its mail to root@phobos instead of root@ubunty;

2. Every day anacron sends me the message:

> From: Anacron <xxxxxxxx@googlemail.com>
To: root@ubunty
Subject: Anacron job 'cron.daily' on phobos
Message-Id: <E1N1HDb-0002oE-1t@phobos>
Date: Fri, 23 Oct 2009 11:17:59 +0100

/etc/cron.daily/debtags:
/etc/cron.daily/debtags: 4: debtags: not found
run-parts: /etc/cron.daily/debtags exited with return code 127
What's up with this "debtags" thing?  How do I fix it?

---

### Post by kbielefe on 2009-10-23
On the first one, check out your /etc/aliases and        /etc/email-addresses[FONT=monospace] and /etc/anacrontab files to see if they might have references to your old hostname.  On the second one, run "dpkg-query -S debtags" to see what package installed that cron job.  Either uninstall that package if you don't really need it, install debtags, or just "sudo rm /etc/cron.daily/debtags" won't hurt anything, although it might pop up again if the package that put it there updates.
[/FONT]

---

### Post by t0p on 2009-10-26
> **kbielefe said:**
> On the first one, check out your /etc/aliases and        /etc/email-addresses[FONT=monospace] and /etc/anacrontab files to see if they might have references to your old hostname.  On the second one, run "dpkg-query -S debtags" to see what package installed that cron job.  Either uninstall that package if you don't really need it, install debtags, or just "sudo rm /etc/cron.daily/debtags" won't hurt anything, although it might pop up again if the package that put it there updates.
[/FONT]

Thanks for the response kbielefe.  Unfortunately the old hostname "ubunty" does not appear in /etc/aliases, /etc/email-addresses or /etc/anacrontab. 

I ran the command "dpkg-query -S debtags" and got the following output:

```
t0p@phobos:~$ dpkg-query -S debtags
debtags: /etc/debtags
debtags: /etc/debtags/sources.list
debtags: /etc/bash_completion.d/debtags
debtags: /etc/debtags/sources.list.d
debtags: /var/lib/debtags
debtags: /etc/cron.daily/debtags
debtags: /etc/debtags/sources.list.d/source-example

```

I don't know what to do from there.

Any suggestions, anyone?

---

### Post by philinux on 2009-10-26
> **t0p said:**
> I changed my computer's name from ubunty to phobos.  Now, every day I receive this Delivery Failure Notification (it's sent to my gmail account because I've set up exim4 to send mail to the gmail account):

So, 2 problems here I'd like help with:

1. How do I tell anacron about the name change, so it will send its mail to root@phobos instead of root@ubunty;

2. Every day anacron sends me the message:

What's up with this "debtags" thing?  How do I fix it?

I assume you change the name in both these files.

 /etc/hostname and /etc/hosts.

---

### Post by kbielefe on 2009-10-26
Looks like the debtags package was installed at some point, then removed for some reason.  Probably because it was no longer needed as a dependency.  But, removing something will usually leave everything in /etc and such, so you don't lose your customizations in case you want to reinstall it later or something.  In synaptic, find the debtags package and mark for complete removal.  That should erase all those files that showed up on dpkg-query.  If that doesn't work, just remove that cron job manually.

If you don't find "ubunty" in /etc/hosts or /etc/hostname, try a full "sudo grep -lR ubunty /etc"  That will take a while, but will tell you any files in /etc that still reference your old hostname.  Then you can use your favorite text editor to change it.

---

### Post by t0p on 2009-10-26
> **kbielefe said:**
> Looks like the debtags package was installed at some point, then removed for some reason.  Probably because it was no longer needed as a dependency.  But, removing something will usually leave everything in /etc and such, so you don't lose your customizations in case you want to reinstall it later or something.  In synaptic, find the debtags package and mark for complete removal.  That should erase all those files that showed up on dpkg-query.  If that doesn't work, just remove that cron job manually.

If you don't find "ubunty" in /etc/hosts or /etc/hostname, try a full "sudo grep -lR ubunty /etc"  That will take a while, but will tell you any files in /etc that still reference your old hostname.  Then you can use your favorite text editor to change it.

I found the package debtags in Synaptic.  It wasn't marked as installed, but I could mark it for complete removal; so I did so.  Hopefully that did the trick, eh!

I ran the grep command you suggested and found a few files that still contained the name "ubunty":

```
t0p@phobos:~$ sudo grep -lR ubunty /etc
[sudo] password for t0p: 
grep: /etc/cfs/supervise: No such file or directory
/etc/ssh/ssh_host_rsa_key.pub
/etc/ssh/ssh_host_dsa_key.pub
/etc/nxserver/users.id_dsa.pub
grep: /etc/alternatives/epiphany-browser.1.gz: No such file or directory
grep: /etc/alternatives/gnome-www-browser.1.gz: No such file or directory
/etc/mailname
/etc/exim4/email-addresses
/etc/exim4/.passwd-client.swp

```

Some of them I don't think I want to mess with.  One at least comes out all garbled when I cat it: Drokk knows how grep found "ubunty".  But I think the only relevant files for this problem are /etc/mailname and /etc/exim4/email-addresses. I shall edit those 2, and hopefully that will be an end to the problem.

Thanks!

---

