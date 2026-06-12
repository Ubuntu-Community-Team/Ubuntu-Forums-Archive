---
title: "Cannot Login to Skype: Server Connect Failed"
date: 2009-10-12
forum: General Help
---

### Post by f00fyf00f3r on 2009-10-12
Cannot Login to Skype: Server Connect Failed

This is a good one for all of us that like computer mysteries. Everyone at work can get onto Skype as it is allowed except one co-worker. Tat has an eee pc 1005 brand new and her twin sister has the same, also brand new. Tat cannot get on, but her sister can. Her connection times out and she gets the "Skype cannot connect. Get help fixing this problem" message." We have disabled firewalls, uninstalled firewalls, del/readded Skype, but the issue persisted. She is running version 3.6.0.248 windows. She also cannot connect from her ipod.

I have been using Skype 2.1 at work for nearly a year now, currently on my eee pc 701 with Ubuntu 9.10 beta on it. I have never had an issue connecting to Skype. I was on a video chat, clicked end call, signed out and quit Skype. I had Tat login using my eee, and she received the message "Sign in failed. Server connection failed." This is where it gets interesting. We chopped it down to her username and I went to login to mine, and now I am receiving the same message. I can no longer log in from work either. I removed Skype, purged all, removed .Skype folder in home directory, reboosted and reinstalled, but the issue persisted.

This is a real head scratcher, she bricked 3 different systems with her username, all different platforms. We reset our passwords and the issue persisted. We are able to connect from home without issue. This is really fascinating, any ideas? Please assist.

---

### Post by P4man on 2009-10-13
contact skype. Sounds like her account was blocked/blacklisted and they are blacklisting all IPs that connect from it or something like that...

---

### Post by f00fyf00f3r on 2009-10-15
I tried another route just for the heck of it on Tuesday...

I put my netbook in standby after logging into Skype at home and then woke it up at work, and it signed right back in! Of course, before I left I logged out and tested and then the issue came back

---

### Post by f00fyf00f3r on 2009-10-15
Per Skype:

-----Original Message-----
From: Skype English Support <en_support@skype.net>
Sent: Thu, Oct 15, 2009 5:46 am
Subject: Re: TE004: Cannot Login to Skype: Server Connect Failed (KMM2157018I15977L0KM)

Hello,

Thank you for contacting Skype Support.

We are happy about your interest in Skype!

We are sorry to learn that you encountered problems when using Skype.

We understand that you are having problems with two Skype accounts in
your company.

It is quite unlikely that a username will cause these problems you
report about.

We recommend the following:

1. Make sure to be logged out from any Skype programme.

2. for Windows XP: Go to C:\Documents and
Settings\your_windows_username\ApplicationData\Skype\your_skype_username

* Delete config.xml
* Start Skype (config.xml will be recreated)

2. for Linux: Go to /home/your_linux_username/.Skype/your_skype_username
and delete config.xml

Now start Skype again and try to log in.

If these suggestions should not solve the problem please contact us
again.

If you should have any more questions or problems, please do not
hesitate to contact us.

With kind regards,

Joerg

Skype Customer Support

Visit [www.skype.com](www.skype.com) for latest news, updates and tips.

---

### Post by f00fyf00f3r on 2009-10-15
I'm not sure how successful that is going to be, as I've wiped the eee and reinstalled completely but will update accordingly

---

