---
title: "How to change the UID of a user with an encrypted home folder?"
date: 2010-09-18
forum: General Help
---

### Post by BFG on 2010-09-18
Just did a new netbook install of Lucid.

Went through the setup, putting in my usual username etc.  But I thought as it's a portable, I'd better select the encrypted home folder option.  All went OK.

I have a home network with a NAS and I needed to change the UID to 1004 to match the rest of the network.

That's when it all when wrong. If I do that, I end up with no permissions on the user folder.  A bit of a paradox, you can't change UID if logged in, but unless you're logged in, can't access the files.

My attempts to get around it by changing UID's back chowning, changing back etc. have screwed things up completely. 

I have managed to open the encrypted folder and chown, but after a reboot it's all back to the original UIDs, but now I can't get in at all.

1. Help getting this resolved is welcome, but unless it's simple it'll probably be quicker to re-install.
2. So, what's a good strategy for setting my own UID and having enrypted home folder?

---

### Post by blueridgedog on 2010-09-18
The best approach would be to remove encryption, then move files.  This may help:

[http://www.satansgarden.org/2010/03/05/removing-encryption-from-home-directories-in-ubuntu-9-10/](http://www.satansgarden.org/2010/03/05/removing-encryption-from-home-directories-in-ubuntu-9-10/)

---

### Post by BFG on 2010-09-20
Thanks :)

---

