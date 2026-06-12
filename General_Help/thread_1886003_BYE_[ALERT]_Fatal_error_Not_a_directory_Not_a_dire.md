---
title: "BYE [ALERT] Fatal error: Not a directory: Not a directory"
date: 2011-11-24
forum: General Help
---

### Post by switchkill on 2011-11-24
HI Guys,

I'm trying to install courier imap with postfix following this guide [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

i'm running ubuntu server 11.04 and when i'm trying to login to localhost 143 i get the following error.


administrator@FAXSERVER:~$ netcat localhost 143
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION] Courier-IMAP ready. Copyright 1998-2010 Double Precision, Inc.  See COPYING for distribution information.
a login administrator password
* BYE [ALERT] Fatal error: Not a directory: Not a directory

any ideas? Be easy, i'm just getting back into linux.
Thanks

---

### Post by lechien73 on 2011-11-24
During the postfix element of the installation, does the mailbox for administrator exist?

```
ls /var/mail
```

If not, create the mailbox and aliases as mentioned earlier in the tutorial and try again.

---

### Post by switchkill on 2011-11-24
The mailboxes exist.

---

### Post by lechien73 on 2011-11-24
Sorry, I should have been more specific. The mailboxes may exist, but are they Maildirs or Mboxes?

Is the mailbox a file, or is it a directory containing 3 x subdirectories - tmp, cur and new?

It needs to be a directory, rather than a file.

---

