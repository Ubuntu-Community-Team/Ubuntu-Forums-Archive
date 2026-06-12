---
title: "Update problem"
date: 2010-12-14
forum: General Help
---

### Post by josh.wright on 2010-12-14
A colleague of mine has installed Ubuntu 10.10 as a virtual machine. He's been having problems with running updates through the terminal.

Error message is:
WARNING: The following packages cannot be authenticated!

Followed by a list of packages then:

Install these packages without verification [y/N]?

I'm at a loss, any thoughts?

Cheers.

---

### Post by staticsafe on 2010-12-14
> **josh.wright said:**
> A colleague of mine has installed Ubuntu 10.10 as a virtual machine. He's been having problems with running updates through the terminal.

Error message is:
WARNING: The following packages cannot be authenticated!

Followed by a list of packages then:

Install these packages without verification [y/N]?

I'm at a loss, any thoughts?

Cheers.

I assume he's using some PPAs for updates. You have to get the GPG keys.

There is a simple script that will allow you to import all missing GPG keys:

[http://www.webupd8.org/2010/12/import-missing-gpg-keys-even-behind.html](http://www.webupd8.org/2010/12/import-missing-gpg-keys-even-behind.html)

---

