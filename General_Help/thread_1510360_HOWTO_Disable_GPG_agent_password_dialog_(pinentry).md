---
title: "HOWTO: Disable GPG agent password dialog (pinentry)"
date: 2010-06-15
forum: General Help
---

### Post by mwjones on 2010-06-15
Say you want to symmetrically encrypt a file with GPG:
```
gpg -c foobar.txt
```

You have already decided on a nice long passphrase and have it copied to the keyboard, when a dialog window pops up asking for the passphrase, but won't allow it to be pasted in.

The fix is simple:
[LIST=1]
[*]Open **~/.gnupg/gpg.conf** in your favorite editor
[*]Comment the use-agent line (prefix it with #)
[*]Kill off the gpg-agent service (sudo killall -9 gpg-agent)
[/LIST]

Now you will be prompted at the shell for the passphrase whenever you use gpg -c.  This also helps for scripts.

---

### Post by js31 on 2011-12-20
Thank you! :)

In case others search for this > command where it's useful (non-interactive file encryption via gpg/command line):

```
gpg --batch --yes --passphrase secret -c file
```

---

