---
title: "That damned red triangle again"
date: 2010-12-28
forum: General Help
---

### Post by b9k9kiwi on 2010-12-28
Been a while since I had the 'update information is outdated' irritant, but it is back with me now.

I have searched the forum for fixes but to no avail (can't recall how I fixed it last time, it was on 10.04 anyway and I am now running 10.10).

I've checked for updates manually and get;

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

My other Ubuntu (10.10) box is happily downloading updates but I can't remember the last time any updates were available for the box in question.

So, now what?

---

### Post by wilee-nilee on 2010-12-28
Try a different server.

---

### Post by DeMus on 2010-12-28
Compare the repository lists in both computers to see if you have the same ones added.
Then check the authentication keys in both computers. Do you have the same keys?
You write a key is missing. Look [_here_]("http://ubuntuforums.org/showthread.php?t=1581172"). Could it be you have the same?

---

### Post by b9k9kiwi on 2010-12-29
Found my previous thread on the same issue and fixed it in the same way.

---

