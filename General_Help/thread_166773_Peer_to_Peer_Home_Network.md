---
title: "Peer to Peer Home Network"
date: 2006-04-27
forum: General Help
---

### Post by CharlieC on 2006-04-27
Hi;

    Sorry for the simple question. 
    I am trying to share computers. Both my XP Home box and my OSX box can see my Ubuntu box. The problem is I cant get through the password authentication. I have tried everything. I have checked the wiki and googled for it and tried numerous solutions and none work. I know there must be an easy answer to this someplace.
Can someone point me in the right direction.

TIA
Charlie the noob

---

### Post by teasum on 2006-04-27
[QUOTE=CharlieC]I am trying to share computers. Both my XP Home box and my OSX box can see my Ubuntu box. The problem is I cant get through the password authentication. I have tried everything. I have checked the wiki and googled for it and tried numerous solutions and none work. I know there must be an easy answer to this someplace.
Can someone point me in the right direction.[/QUOTE]

If you're sharing with Samba on your Ubuntu box (and you probably are), you need to add a user and password in Samba in order for the Windows box to log in (and probably the OSX box too, though I haven't had any experience networking macs).  From the command line on your Ubuntu box, try

```
sudo smbpasswd -a username
```

Of course, substitute the 'username' you want to use to log in to your Ubuntu box from your Windows box.  You'll be prompted to enter a password for the new user.  Then, use the username and password to log in from your Widnows box.  

I'm a real newbie as well, so I'm sure other people out there have more detailed and/or advanced advice for you.  In any case, this is what worked for me.  

Good luck!

---

### Post by CharlieC on 2006-04-27
Thank you very much. It is so simple if you know how.

Charlie

---

