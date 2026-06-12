---
title: "Very, very basic question"
date: 2010-07-05
forum: General Help
---

### Post by maghoxfr on 2010-07-05
I know this is the kind of questions one hates to see posted.

I'm having all kind of problems with my ubuntu 10.04 which I updated to from the 9.10. I'm doing a clean install so I'd like to have this very clear. Right now I have three users:
1-the administrator
2-the one I use for music production
3-a general one.

The only one in which I can access synaptic is user 1. My question is: is there a way I can access to synaptic from the other users? I thought that you picked an admin password and if you were on a non admin account, by typing it you could use synaptic.

What's the setup of accounts you recommend?
Thanks (and sorry)

---

### Post by khuttger on 2010-07-05
SO what you can try is log onto the administrator account and go to
```
System > Administration > Users and Groups
```

And look through the tabs for the right settings you want for yours. Should do it for ya.

---

### Post by d3v1150m471c on 2010-07-05
one account and possibly a backup account in the event you fudge your main account. use your main account for both admin and music production. use sudo and gksudo wisely and sparingly.

---

### Post by tgm4883 on 2010-07-05
I don't think you understand the concept behind sudo. Read this and ask if you have any questions 

[http://www.psychocats.net/ubuntu/security#sudoisnotroot](http://www.psychocats.net/ubuntu/security#sudoisnotroot)

---

### Post by maghoxfr on 2010-07-05
Thank you all, I'll read that link and try the groups settings. I'll come back with doubts for sure.

---

### Post by maghoxfr on 2010-07-06
Thanks, I've changed my config to admin and now I can run synaptic. I've read the link you gave me, it was very explanatory, there was another [link]("https://help.ubuntu.com/community/RootSudo") to the ubuntu help that helped me further. I still don't understand something: to log as root is the same as using an admin user?

---

