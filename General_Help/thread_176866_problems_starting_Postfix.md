---
title: "problems starting Postfix"
date: 2006-05-15
forum: General Help
---

### Post by batkins on 2006-05-15
I noticed that my server wasn't automatically starting Postifx when it boots.  It is in the default runlevel, so I tried starting it manually:

```

  bill@galoot /home/bill % sudo /etc/init.d/postfix start                 11:33AM
 * Stopping Postfix Mail Transport Agent... postfix/postfix-script: fatal: usage: postfix start (or stop, reload, abort, flush, check, set-permissions, upgrade-configuration)

```

On the other hand, 

```

bill@galoot /home/bill % sudo postfix start                             11:34AM
postfix/postfix-script: starting the Postfix mail system

```

works perfectly.  I have the latest Postfix available from Ubuntu.  Why doesn't the init script work properly?

---

