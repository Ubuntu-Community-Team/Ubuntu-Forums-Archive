---
title: "Another custom launcher question."
date: 2010-01-19
forum: General Help
---

### Post by ripeart on 2010-01-19
I'm having trouble launching HP Device Manager when logged in using a super user account.

The following commands work fine when run one by one through terminal:

xhost +
su *[user]*
/usr/bin/hp-toolbox

How can I get these commands into a custom launcher applet? I have chmod the permissions on the hp-toolbox file. I have tried:

xhost + && su *[user]* && /usr/bin/hp-toolbox

Also, where can I look at error logs for this sort of thing? I would like to be able to see a log of what is happening when I click this applet.

Thanks!

---

