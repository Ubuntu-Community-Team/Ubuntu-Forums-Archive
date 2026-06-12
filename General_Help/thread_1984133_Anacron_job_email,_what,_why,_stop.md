---
title: "Anacron job email, what, why, stop?"
date: 2012-05-21
forum: General Help
---

### Post by gencon on 2012-05-21
Using: Ubuntu Lucid

Over the last week or so I've been receiving an email every morning from my root account. The IP is consistent with it having been sent from my PC, as is the computer name, and (not local) mail server.

I have no idea why I am getting these emails, am unsure exactly what they mean, and -most importantly- how I go about stopping them !?

I have no jobs running in my user crontab, nor in my root's crontab, which I can see might be the cause. The reference to 'cron.daily' suggests it is deeper within the OS than the normal user/root crontabs.

Thanks all.

Here's the key section of the email:

```

From: Anacron <root>
To: root
Subject: Anacron job 'cron.daily' on ubuntupc

/etc/cron.daily/man-db:
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 29964 package 'handbrake-gtk':
 error in Version string 'svn3295ppa1~lucid1': version number does not start with digit
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 34964 package 'mac-3.99-u4':
 error in Version string 'b3-1': version number does not start with digit
dpkg-query: warning: parsing file '/var/lib/dpkg/available' near line 30585 package 'handbrake-gtk':
 error in Version string 'svn3295ppa1~lucid1': version number does not start with digit
dpkg-query: warning: parsing file '/var/lib/dpkg/available' near line 35463 package 'mac-3.99-u4':
 error in Version string 'b3-1': version number does not start with digit


```

---

### Post by phaemon on 2012-05-21
Hi,

There's no real "deeper" to cron. There's no magic to Linux. ;-)

This particular set or jobs are in /etc/crontab. Just view it and edit it with your normal text editor.

You can clear those warnings with "sudo dpkg --clear-avail"

---

### Post by gencon on 2012-05-21
Many thanks for your help.

 I suppose the file "/etc/crontab" - which I did not know about and as opposed to the command "crontab -e user" - is what I meant as "deeper within the OS".

Will the command "sudo dpkg --clear-avail" clear those warnings permanently?

Cheers.

---

### Post by phaemon on 2012-05-21
Fair enough. I just didn't want you to get the impression that Linux had hidden, secret kind of stuff that ordinary users should not ken of. It's just another kind of crontab file.

Those warnings should be for stale entries, as newer packages should be fixed, so yes, it should remove the warnings for good.

---

### Post by gencon on 2012-05-21
Ok and thanks. Fingers crossed that'll stop those annoying emails.

Cheers.

---

### Post by gencon on 2012-05-22
Unfortunately the command "sudo dpkg --clear-avail" has **not** cleared the warnings permanently, I received another warning email today. :(

Any ideas?

---

### Post by phaemon on 2012-07-03
Sorry about not replying; I wasn't looking at forums for a while.

This is a problem with a ppa you have added for handbrake. You have a few options:

1. Remove this ppa
2. Contact the people in charge of this ppa and tell them to fix their packages
3. Put up with the emails

Hope you found a solution already, but I thought I ought to post in case anyone googled and found this thread.

---

### Post by gencon on 2012-07-03
Thanks for the reply.

Yes, I did work that out. Since I will be upgrading to Precise Pangolin soon I decided to live with the emails. :)

Cheers.

---

### Post by JohnAStebbins on 2012-07-04
FYI, the version number issue in the handbrake packages was fixed some time ago.  But HandBrake has discontinued support for Lucid, so you never received any updates to fix the version number of your existing package.

---

### Post by gencon on 2012-07-04
Ok, thanks for the info. John.

As mentioned I'll be upgrading to Precise (just as soon as I have a spare day). :)

---

