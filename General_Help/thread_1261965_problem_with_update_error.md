---
title: "problem with update error"
date: 2009-09-09
forum: General Help
---

### Post by medic0079 on 2009-09-09
so while running the update manager I got this

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


im sure its an easy fix but im kinda ubuntu new/dumb so trying to work it through. I assume it is because I just upgraded opera, and the old pub keys are no longer valid but Im not sure how to upgrade to new keys, or if I need to just delete the old keys. nor would I know how to do this. thanks for the help

---

### Post by tigerking615 on 2009-09-20
It's not just because you installed Opera. I don't remember updating anything, but I am getting the same thing. It happens when I try Administration > Update Manager and check for new updates, and when I go to Synaptic and click Reload. 

I'm also trying to figure out what the problem is.

---

### Post by MelDJ on 2009-09-20
you must add the gpg key. Watch the video here: [http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

---

### Post by odinb on 2009-09-20
--== Issues with missing Public Keys? ==--
Enter this command, replacing 9D1A0061 with your NO_PUBKEY-key last eight digits from the error-message to import the key:
	gpg --keyserver keyserver.ubuntu.com --recv 9D1A0061

Then add the key to your software sources, again, replace 9D1A0061 with the keynumber used in above command:
	gpg --export --armor 9D1A0061 | sudo apt-key add -

Then update your software sources:
	sudo apt-get update

---

### Post by tigerking615 on 2009-09-20
Thank you very much for the quick replies. This isn't making much sense, but hopefully it works.

@ MelDJ - I added the Opera key, but now i have a new error message:

```
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0Failed to fetch [http://deb.opera.com/opera-beta/dists/stable/non-free/binary-i386/Packages](http://deb.opera.com/opera-beta/dists/stable/non-free/binary-i386/Packages)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

I guess it was a problem with Opera...



@ odinb - I did what you said, and now I have this:

```
W: Failed to fetch http://deb.opera.com/opera-beta/dists/stable/non-free/binary-i386/Packages  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by tigerking615 on 2009-10-03
Okay, so I got this thingy working. 

1. Go to Synaptic Package Manager. Go to Settings > Repositories > Third-Party Software, and uncheck anything with Opera in it. Click Reload to update everything else. 

2. Enter this command to be able to update Opera:
```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```
It's from here: [http://deb.opera.com/](http://deb.opera.com/)

---

