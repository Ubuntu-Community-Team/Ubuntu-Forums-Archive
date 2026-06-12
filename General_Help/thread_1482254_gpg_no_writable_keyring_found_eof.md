---
title: "gpg: no writable keyring found: eof"
date: 2010-05-13
forum: General Help
---

### Post by windfix on 2010-05-13
I had Picasa 3,6 running beautifully under Lucid, after following this post:  [http://www.webupd8.org/2010/04/how-to-install-picasa-36-in-ubuntu.html](http://www.webupd8.org/2010/04/how-to-install-picasa-36-in-ubuntu.html)

Later, I made the grievous error of moving my /home directory to an ntfs partition.  Realizing that it had destroyed all the file ownership of my files (somehow made them all root's), I moved back to ext3 and chown'ed the whole directory back to my ownership.  It fixed most problems, except Picasa now won't run.

I've tried removing wine and picasa, reinstalling to no avail.  One symptom is that I keep getting these gpg errors when I attempt to add the Google Linux repo's key:

gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error

The contents of my .gnupg directory are all owned by me, and are:
gpg.conf, pubring.gpg, secring.gpg, trustdb.gpg

I'm clueless.... anyone have suggestions?  I miss Picasa!

---

### Post by windfix on 2010-05-14
OK... partial solution.  The APT instructions on googles website call for this compound command:

[COLOR="Magenta"]wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | apt-key add -
apt-get update[/COLOR]

By executing them separately, for some reason it worked.

I downloaded the public key, linux_signing_key.pub, to my desktop.  Then I ran

[COLOR="Blue"]sudo apt-key add /home/paul/Desktop/linux_signing_key.pub
[/COLOR]
It took it.  I have no idea why.

---

### Post by plucky on 2010-05-14
Because there is no sudo in the commands.

It should look like ```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -
sudo apt-get update
```

and then it will work.

Good Luck

---

### Post by windfix on 2010-05-14
Makes sense, although I had tried preceding their entire command with sudo... I guess it needed to be on the latter section of the compound command.

---

