---
title: "Pidgin IM"
date: 2009-08-24
forum: General Help
---

### Post by accooper on 2009-08-24
I have heard that there are some security problems with Pidgin IM program.  I have never used IM before and know little about it but my son who has just gone of to be a freshman at college said we should us IM to communicate over the Internet.

If Pidgin is a security problem is there another more secure IM program?

TIA

Andrew From Texas

---

### Post by Revolutionary101 on 2009-08-24
You could install empathy. This program may actually replace pidgin in Ubuntu 9.10.

---

### Post by philcamlin on 2009-08-24
> **Revolutionary101 said:**
> You could install empathy. This program may actually replace pidgin in Ubuntu 9.10.
aMsn is good too :P

---

### Post by sefs on 2009-08-24
The problems are supposed to be fixed in 2.6.1 which is available in the PPA repos for it I believe.

See this article....
[http://www.h-online.com/security/Critical-vulnerability-in-Pidgin-IM--/news/114036](http://www.h-online.com/security/Critical-vulnerability-in-Pidgin-IM--/news/114036)

Pidgin Repos:
```

# PIDGIN REPOS
# ================================================================================
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main

```

---

### Post by Revolutionary101 on 2009-08-24
All of the security issues and when they were fixed are available for you to look at here

[http://www.pidgin.im/news/security/](http://www.pidgin.im/news/security/)

---

### Post by tuxxy on 2009-08-24
Which network do you plan to use? for MSN I would say aMSN is the best however pidgin will do for almost any network which is its advantage.  Security issues I wouldn't worry about them for simple IM.

---

### Post by redmk2 on 2009-08-24
> **accooper said:**
> I have heard that there are some security problems with Pidgin IM program...

...If Pidgin is a security problem is there another more secure IM program?


I have used pidgin everyday for the last few years.  I used GAIM before that.  GAIM is the predecessor of pidgin. 

I don't see pidgin any more insecure than the underlying IM protocols it supports.  Empathy uses the same code (libpurple) as pidgin so it is no more secure.

The biggest criticism seems to be the password file for your pidgin accounts is in clear text.  This file is in your home directory.  If an intruder is that far into our system you have big security problems with or without an IM client.

For a good description of pidgin see [[COLOR="Purple"]**_here_**[/COLOR]]("http://en.wikipedia.org/wiki/Pidgin_(software)").

---

### Post by earthpigg on 2009-08-24
one security concern -- often overlooked -- is that your usernames and passwords are saved on your machine in plain text, meaning anyone that has *_physical access_* to your computer can access them...if you allow that to happen, if the individual feels so inclined, and if he knows where to look.

in a college dorm setting, this may be quite possible.

look at /home/your-username/.purple/accounts.xml

since emphany also uses /.purple, i imagine it is exactly the same with that.

"whatever, its just my IM passwords..."

well, think of how that 'i forgot my password, send it to my e-mail address' stuff works.

your yahoo.com account was referenced when you made your professional-looking email account.

your @professionalsoundingdomain.com email was referenced when you made your online banking account.

bad guy gets access to your yahoo.com account by digging through your /home/.purple

bad guy 'forgets his professionalsoundingdomain.com account password', and gets it emailed to yahoo.com account.

bad guy now has prodomain.com account access.

then he 'forgets the password to the online banking site' and gets that pword sent.


bad guy transfers your life savings to a bank in bermuda.


wikipedia/google 'privilege escalation' :D

---

### Post by eldragon on 2009-08-24
> **earthpigg said:**
> one security concern -- often overlooked -- is that your usernames and passwords are saved on your machine in plain text, meaning anyone that has *_physical access_* to your computer can access them...if you allow that to happen, if the individual feels so inclined, and if he knows where to look.

in a college dorm setting, this may be quite possible.

look at /home/your-username/.purple/accounts.xml

since emphany also uses /.purple, i imagine it is exactly the same with that.

"whatever, its just my IM passwords..."

well, think of how that 'i forgot my password, send it to my e-mail address' stuff works.

your yahoo.com account was referenced when you made your professional-looking email account.

your @professionalsoundingdomain.com email was referenced when you made your online banking account.

bad guy gets access to your yahoo.com account by digging through your /home/.purple

bad guy 'forgets his professionalsoundingdomain.com account password', and gets it emailed to yahoo.com account.

bad guy now has prodomain.com account access.

then he 'forgets the password to the online banking site' and gets that pword sent.


bad guy transfers your life savings to a bank in bermuda.


wikipedia/google 'privilege escalation' :D

that cannot happen, i keep all my money under my matress ;)

---

### Post by mcDavid on 2009-08-25
> **earthpigg said:**
> one security concern -- often overlooked -- is that your usernames and passwords are saved on your machine in plain text, meaning anyone that has *_physical access_* to your computer can access them...if you allow that to happen, if the individual feels so inclined, and if he knows where to look.

in a college dorm setting, this may be quite possible.

look at /home/your-username/.purple/accounts.xml
  
Holy Cow! I just discovered the password of my ex-girlfrends mail-account! :o :popcorn:
nah not for real. But this is kind of a serious issue I wasn't aware of. Luckily I never save my password on other computers than my own.

---

### Post by blur xc on 2009-08-25
> **earthpigg said:**
> one security concern -- often overlooked -- is that your usernames and passwords are saved on your machine in plain text, meaning anyone that has *_physical access_* to your computer can access them...if you allow that to happen, if the individual feels so inclined, and if he knows where to look.

in a college dorm setting, this may be quite possible.

look at /home/your-username/.purple/accounts.xml

since emphany also uses /.purple, i imagine it is exactly the same with that.

"whatever, its just my IM passwords..."

well, think of how that 'i forgot my password, send it to my e-mail address' stuff works.

your yahoo.com account was referenced when you made your professional-looking email account.

your @professionalsoundingdomain.com email was referenced when you made your online banking account.

bad guy gets access to your yahoo.com account by digging through your /home/.purple

bad guy 'forgets his professionalsoundingdomain.com account password', and gets it emailed to yahoo.com account.

bad guy now has prodomain.com account access.

then he 'forgets the password to the online banking site' and gets that pword sent.


bad guy transfers your life savings to a bank in bermuda.


wikipedia/google 'privilege escalation' :D

Can't happen- under the email account in which I created my original IM account years ago no longer exists.  Not only that, I didn't use my email password for my im login password.  Also- when I created my IM account using msn messenger (years ago), it sternly warned that IM-ing was not a secure form of communicating, DO NOT SEND SENSITIVE DATA ACROSS AN IM.  

So yeah, if some bad guy got my im account and login info, they could seriously irritate me by making me sign out when they signed in on my account, and impersonated me to my friends that I im with.  (..with whom I im?)

BM

---

