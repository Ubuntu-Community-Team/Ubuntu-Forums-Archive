---
title: "terminal encrypt/password protect a folder"
date: 2011-04-15
forum: General Help
---

### Post by flyingsliverfin on 2011-04-15
is there a way to password protect a file or folder from the terminal? i wanted to do this because I may have several friends depositing files on my ssh server that they don't want each other to see. Or i might have a file i don't want them to see.

I installed cryptkeeper,but it can't take commands from the terminal. Anything else I can try?

---

### Post by bodhi.zazen on 2011-04-15
First, each user should have a unique user name and a private home directory.

You can then make a shared public directory, ~/public if you wish.

You can encrypt files with gpg and you can encrypt an archive (.zip).

---

