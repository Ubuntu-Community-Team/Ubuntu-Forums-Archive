---
title: "MediaTomb is preventing me from installing.. anything??"
date: 2010-09-23
forum: General Help
---

### Post by Roasted on 2010-09-23
Not sure where I got MediaTomb. Probably clicked it in the software center because it looked interesting. Anyway I cannot download or install anything. Any. Thing.

I get this error:

installArchives() failed: Preconfiguring packages ...

Preconfiguring packages ...

dpkg: unrecoverable fatal error, aborting:

 syntax error: unknown user 'mediatomb' in statoverride file

---

### Post by Roasted on 2010-09-23
EDIT:

Someone in the IRC helped me. He found a bug report about it, something about MediaTomb tries to delete a user that doesn't exist and that's why it bombs out. He suggested I create a user and group named mediatomb and go from there. So I installed mediatomb, then removed + purged mediatomb, then deleted the user and group. All is well now. Curse you, Mediatomb...

EDIT again: Not solved. In order for anything to work, I need to have the user "mediatomb" added to my system. No joke. With mediatomb (the user) not on my system, I cannot install firestarter. I get the error above. I add mediatomb as a user, and guess who can install firestarter now? I can!

How can I remove this **** so I can have no mediatomb user and install things like normal? Is this normal behavior of mediatomb? Why is this software such a pain in the ***?

EDIT EDIT EDIT EDIT - Went into the IRC channel again and a user was nice enough to give some advice, which was to run apropos statoverride, which told me via terminal that statoverride was dpkg related. SO.... I ran man dpkg-statoverride and I read that statoverride is a way for dpkg to make certain functions happen as a certain owner, and in my case it was mediatomb. As a result, without mediatomb existing, everything bombed out for some reason. I ran gksudo-nautilus and as root (be careful) navigated to /var/lib/dpkg/statoverride. There were 4 lines. (MAKE A BACKUP OF IT FIRST). Two lines were pertaining to root, two lines were pertaining to mediatomb. I deleted each mediatomb line and made sure there were NO BLANK LINES in the file. If there are, you'll still get an error (but a different error). Now everything is running great once again.

I have no clue why it happened, or how it happened. But it did, and it's fixed. PHEW.

---

### Post by skippycostin on 2011-07-21
> **Roasted said:**
> EDIT:

Someone in the IRC helped me. He found a bug report about it, something about MediaTomb tries to delete a user that doesn't exist and that's why it bombs out. He suggested I create a user and group named mediatomb and go from there. So I installed mediatomb, then removed + purged mediatomb, then deleted the user and group. All is well now. Curse you, Mediatomb...

EDIT again: Not solved. In order for anything to work, I need to have the user "mediatomb" added to my system. No joke. With mediatomb (the user) not on my system, I cannot install firestarter. I get the error above. I add mediatomb as a user, and guess who can install firestarter now? I can!

How can I remove this **** so I can have no mediatomb user and install things like normal? Is this normal behavior of mediatomb? Why is this software such a pain in the ***?

EDIT EDIT EDIT EDIT - Went into the IRC channel again and a user was nice enough to give some advice, which was to run apropos statoverride, which told me via terminal that statoverride was dpkg related. SO.... I ran man dpkg-statoverride and I read that statoverride is a way for dpkg to make certain functions happen as a certain owner, and in my case it was mediatomb. As a result, without mediatomb existing, everything bombed out for some reason. I ran gksudo-nautilus and as root (be careful) navigated to /var/lib/dpkg/statoverride. There were 4 lines. (MAKE A BACKUP OF IT FIRST). Two lines were pertaining to root, two lines were pertaining to mediatomb. I deleted each mediatomb line and made sure there were NO BLANK LINES in the file. If there are, you'll still get an error (but a different error). Now everything is running great once again.

I have no clue why it happened, or how it happened. But it did, and it's fixed. PHEW.

Thank you very much! Damn mediatomb! :D

---

