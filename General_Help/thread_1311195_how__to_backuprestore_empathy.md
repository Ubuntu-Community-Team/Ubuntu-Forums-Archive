---
title: "how  to backup/restore empathy"
date: 2009-11-02
forum: General Help
---

### Post by bluefrog on 2009-11-02
if anyone has clues as of what to do to backup/restore empathy, I would be grateful.

I thought it was simple as copy/paste .mission-control-5 but it appears I must be missing some steps.

---

### Post by bluefrog on 2009-11-14
nobody is moving empathy accounts from one computer to another?

---

### Post by bluefrog on 2009-11-14
mc-tool must be used.

usage

you can list your accounts first

$ mc-tool list
gabble/jabber/account-name

show your account
$ mc-tool show gabble/jabber/account-name
Account: gabble/jabber/account-name
(string) account = my-login
(string) password = my-password

Basically all you need to restore your account with the following command
$ mc-tool add gabble/jabber account-name string:account=my-login string:password=my-password | xargs mc-tool enable

---

### Post by DPic on 2009-11-15
I always just back up these folders: 

 /usr/lib/gnome-keyring
 .config/Empathy
 .gconf/apps/telepathy
 .local/share/Empathy
 .mission-control
 .gnupg

but i'm not sure which ones are actually needed or not...

---

