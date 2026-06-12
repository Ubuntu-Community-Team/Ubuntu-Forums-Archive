---
title: "Pidgin and the Facebook Chat (Error: &quot;Not authorized&quot;)"
date: 2011-02-07
forum: General Help
---

### Post by Daniel_le_Rouge on 2011-02-07
Hello,

Since a week I cannot use the Facebook chat in Pidgin anymore. I configured everything like stated in the Facebook instructions, but I keep receiving the error message.

```
Not authorized.
```

I do not what the problem is. Before it worked charming, but last week I changed my Facebook user name and since then it get this error. Of course I changed the user name in the configuration as well.

I have no idea what to do. I have already asked Facebook, but got no answer.

I am using Pidgin 2.7.3 on Ubuntu 10.10.

Thanks for your help!

Daniel

---

### Post by Daniel_le_Rouge on 2011-02-11
I had to change my password in Facebook and after that in Pidgin and than it worked again.

---

### Post by sffvba[e0rt on 2011-02-11
Hi,

What I found with Empathy (and might also be an issue with Pidgin) is that if you use a user name and password to log into Facebook via the Internet as opposed to an e-mail address and password you should use the same for the IM client... vice-verse as well... 

If you use e-mail for the one, and user name for the other you tend to get authorization errors in the IM client... never checked this in Pidgin but I have this sneaking suspicion :)


404

---

### Post by svanarts on 2011-04-28
404, right on the money.  Solved my problem.  Thanks.

---

### Post by bemymonkey on 2011-08-16
Interesting, when I try to use my e-mail address, Pidgin says "Invalid XMPP ID", because the entire ID is [email]my@email.address@chat.facebook.com[/email]... doesn't look too promising in itself.

Any other ideas?

---

### Post by damnated on 2011-08-27
I tried logging in with my user name to facebook, then tried the same with pidgin. Same not authorized error.

LE: I have found out, that this still works on my laptop, where I am using an older Pidgin version, namely 2.7.11. On my PC I have 2.10.0. I copied every account setting from the older pidgin to the new one, but it just does not work. It seems to me, that newer Pidgin versions broke something.

---

### Post by Robert Finley on 2011-09-06
> **not found said:**
> if you use a user name and password to log into Facebook via the Internet as opposed to an e-mail address and password you should use the same for the IM client... vice-verse as well... 

I've experienced the same problem.  I don't know why, since it has run fine for months, but last night Pidgin stopped talking to Facebook and said "Not Authorized" every time I tried to reconnect. 

Sure enough, I went back to my browser and logged in with my user name instead of my email address and then re-connected with Pidgin and- voila! Works perfect now.

Thank you for your help!

---

### Post by blake.riley on 2011-10-05
@Robert Finley,
Thanks for expressing what I should do so clearly. Fixed my problem!

---

### Post by paulie420 on 2012-07-19
I use my email address to log in, I logged out of facebook and logged in using the username that goes behind the fackbook.com/username and solved all my issues.

Thank you!!

---

