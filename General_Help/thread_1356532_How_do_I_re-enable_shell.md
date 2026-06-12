---
title: "How do I re-enable shell"
date: 2009-12-16
forum: General Help
---

### Post by husskii on 2009-12-16
Im using unbuntu server 9.04 x64 & I disabled a user from using shell, so he couldnt access the server thru putty..
Later I restarted the server and now I cant figure out how to start his vnc connection..

Is there a command I could use to re-enable shell.

the command I used to disable shell was - 
```
usermod --shell /bin/false <username>
```

thanks

---

### Post by akakingess on 2009-12-16
Silly suggestion, have you tried just doing "usermod --shell /bin/true <username> ? I am not to familiar with all the command line or shell stuff, just wondering if "false" turned it off, could "true" turn it back on?

---

### Post by Leppie on 2009-12-16
assuming your server has bash installed, try this:
```
usermod --shell /bin/bash <username>
```

---

### Post by uid0 on 2009-12-16
Alternatively, you can just edit /etc/passwd in your favorite text editor and copy the shell value from another user. You will need to do this as root.
  
A typical passwd file entry looks like this:

foo:x:1000:1000:Foo Bar,,,:/home/foo:/bin/bash

Notice there are several fields seperated by colons  ":"

The fields are in order of right to left:

User name
Placeholder "x" for the user's password (now stored in /etc/shadow)
UID  -- User ID
GID  -- Primary Group ID
Comment Field
Home Directory
Shell

---

### Post by husskii on 2009-12-16
Thanks guys all sorted now, I tried 
usermod --shell /bin/bash <user> and all is good.. thanks Leppie :)

Hi akakingess lol I tried that myself too, thinging well if false disables it true must enable, but ye it wouldnt work.. lol thanks anyways mate :)

hi uid0 I was going tp try you way next is bash didnt work, 
thanks :)

much appreciated :)

oh and just 1 more question, s it ok to use bin/false and bin/bash a few times. because I just disabled his shell again, but will need to enable if we need to reboot again..

thank:)

---

### Post by Iowan on 2009-12-16
Depending on what you mean by "a few times", it wouldn't seem to be a problem to change a user's shell when necessary (probably not whilst (s)he's using it...).

---

### Post by Leppie on 2009-12-16
glad it worked.

I agree with Iowan, shouldn't be a problem switching shells (normally users can switch shells themselves as well during a session, provided more than 1 shell is installed on the system) though disabling/enabling on the server while a user is still logged on is not a thing to be recommended.

---

### Post by husskii on 2009-12-16
oh I wouldn't attempt this while the user is logged in, actually the user doesn't even know he has shell, its just for me to enable if I reboot the server and need to start up his vnc.., well at least till I figure out how to start vnc when the server starts. that way wen I reboot (if needed) the server will auto start vnc for each user for me..

Thanks for all your advise, its greatly needed and has been taken on board :)

---

