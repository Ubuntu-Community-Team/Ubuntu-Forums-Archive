---
title: "(eeebuntu) Running into a problem with the  Update Manager"
date: 2010-03-27
forum: General Help
---

### Post by two_fishes on 2010-03-27
This happens everytime the Update Manager runs. I get an error that it "Could not download all repository indexes". The error incudes this information:

GPG error: [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 81D820A9BB7A1A83Failed to fetch [http://www.statux.org/ubuntu/dists/jaunty/main/binary-i386/Packages](http://www.statux.org/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Do I have to make a public PGP key? Do I need to point the updater to a different address?

---

### Post by kamaji792 on 2010-03-27
I am not entirely sure way you have the problem you do.  I sort of suspect that the repository does not exist any more.

I do know when you add a new repository you need to fetch the Public key associated with it to allow verification of any updates.  That said it would not stop you doing an update.

I think you need to find out if the repository still exists or if it has been moved.

All the best

---

