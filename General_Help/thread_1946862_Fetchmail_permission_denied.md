---
title: "Fetchmail permission denied"
date: 2012-03-25
forum: General Help
---

### Post by cssutto on 2012-03-25
ubuntu 10.4 new install on new machine.

mutt-msmtp-fetchmail- procmail.

Fetchmail gives permission denied.

Checked all permissions against permissions on old machine which also runs 10.4, but an older cobbeled up install a result of auto updating from earlier ubuntu.

I have googled for two days and have found no helpful suggestion.

Suggestions appreciated.

Edit to add:

I have sent to myself many emails and they do not appear in the /var/log/mail.log nor in the sys.log nor any other logs.

It would appear that they are never being executed by mutt but muttrc is an exact copy of the one on my old machine that has run for several years now.

Of course I changed the lines that reference host.  All other filenames are identical.

This 10.4 came without sendmail and since I have always used sendmail, I installed that from synaptic.

That installation did say that all postfix files were not removed.

Then I decided that maybe I installed the wrong version of msmtp so I removed it and installed msmtp-mta and that installation removed sendmail.

However in my muttrc I kept the line>  set sendmail="/usr/bin/msmtp" because without that mutt will not load.

whereis postfix shows that it still in on the machine, but synaptic can not see it.

I am wondering if mutt is trying to use the remnant of postfix.  I would like to remove it rather than junking up this system with leftovers from the very beginning.

---

