---
title: "update manager error, so annoying"
date: 2009-08-06
forum: General Help
---

### Post by lovhorror on 2009-08-06
> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E394067C90172836Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources)  404 Not Found [IP: 91.189.88.40 80]
Some index files failed to download, they have been ignored, or old ones used instead.


How do I fix this stupid ****, it's happened before but I forgot what to do.

---

### Post by wojox on 2009-08-06
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com E394067C90172836
```

Are you using Jaunty because it pointing to a Gutsy server which is EOL.

---

### Post by lovhorror on 2009-08-06
didn't do ****, thanks for trying tho

---

### Post by Cheesemill on 2009-08-06
The default repositories for 7.10 are now offline because support has run out for Gutsy (it ended in April).
 
You really should think about upgrading as you are no longer recieving security updates for your system.

---

### Post by slakkie on 2009-08-06
See the EOL link in my sig, should help you out.

---

### Post by Fatman_UK on 2009-08-06
I wrote a little script because I was fed up with this.  Here:

```

#!/bin/sh

gpg --keyserver hkp://subkeys.pgp.net --recv-keys $1
gpg --export --armor $1 | sudo apt-key add -
```

Put that in getkey.sh in your home dir and run "chmod a+x getkey.sh" so it can run. Whenever you get the error, copy the last 8 bytes from the bit after PUBKEY in the error (so "90172836" in this case). Then in the console type:

```

~/getkey.sh 90172836
```

which will take a minute or so, be patient. Then try the update again.

----

Yeah, upgrade first. Then create the script, will save you annoyance later on.

---

### Post by lovhorror on 2009-08-07
thanks slakkie, everything's back to normal now

---

