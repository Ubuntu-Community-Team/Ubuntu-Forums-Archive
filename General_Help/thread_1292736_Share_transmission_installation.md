---
title: "Share transmission installation"
date: 2009-10-16
forum: General Help
---

### Post by lmellor on 2009-10-16
Hi, me and my girlfriend both have separate user accounts on my computer, mainly so that I can keep my work separate from everything else.  I have been recently wondering if it's possible for us both to 'share' the same copy of transmission.

That being a rough description I shall explain a little further how I would like the set-up to work...

I add a torrent to transmission, set it downloading and log out of my account/shut down, the next time we log into my girlfriend's account I would like for that torrent to appear in 'her transmission' and continue downloading it.  

We both already share a download partition so permissions shouldn't be an issue, and obviously if we do it this way then it doesn't matter who adds a torrent to the list, it will continue to download so long as the computer is on and at least one of us is signed in.

:confused:
Hopefully it wouldn't be an issue if both of us were signed in at the same time, but even if it were, it would be no problem to ensure that we aren't both logged in simultaneously .

---

### Post by lovinglinux on 2009-10-16
Clean up her Transmission torrent list and add them to yours. Then copy your .transmission folder from home to the shared partition. Then delete her .transmission folder, then run this command on both accounts:

```
ln -s /**[COLOR="Red"]shared_partion_path[/COLOR]**/.transmission ~/.transmission
```

This will create a symlink in your/her home folder to the .transmission folder in the shared partition. Basically you will be sharing all Tranmission settings and torrent states, because the application will be reading/writing this info from/to the shared partition.

---

### Post by justleen on 2009-10-16
you could run the transmission daemon, with the web interface enabled?
That way you could share it via a webinterface..

---

### Post by justleen on 2009-10-16
> **lovinglinux said:**
> Clean up her Transmission torrent list and add them to yours. Then copy your .transmission folder from home to the shared partition. Then delete her .transmission folder, then run this command on both accounts:

```
ln -s /**[COLOR="Red"]shared_partion_path[/COLOR]**/.transmission ~/.transmission
```


I thought of that, but you have make sure permissions are setup correct, since you normally dont have access to other users home dir..?

edit:  nevermind, you thought of that by placing it on a share!  

READ!! then post... :|

---

### Post by lmellor on 2009-10-16
So far so good, the only problem I seem to have now is that torrents added by one user seem to automatically have the wrong permissions, I started a torrent off in my girlfriend's profile, quit transmission, went into mine only to be given a permission denied error on that torrent in transmission :(

Anybody got any smart ideas on how to solve this final hurdle?

---

### Post by lovinglinux on 2009-10-16
> **lmellor said:**
> So far so good, the only problem I seem to have now is that torrents added by one user seem to automatically have the wrong permissions, I started a torrent off in my girlfriend's profile, quit transmission, went into mine only to be given a permission denied error on that torrent in transmission :(

Anybody got any smart ideas on how to solve this final hurdle?


Try this script to launch Transmission on your account only:

```
#!/bin/bash

sudo chown $USER:USER -R /**[COLOR="Red"]path_to_shared_partition[/COLOR]**/.transmission

transmission && 

sudo chown **[COLOR="Red"]yourgirlfriend[/COLOR]**:[COLOR="Red"]yourgirlfriend[/COLOR] -R /**[COLOR="Red"]path_to_shared_partition[/COLOR]**/.transmission 
```

Replace only stuff in red. Save it as *transmissionpermits.sh* or whatever you like, then make it executable. Launch Transmission only with the script on your machine.

This will change the permission of all files in the .transmission to you before starting Transmission and give back to your girlfriend when closing Transmission.

EDIT: you can also add a line to change the permission of the content folder where transmision saves the downloaded content.

---

### Post by Charles Kerr on 2009-10-17
lovinglinux is right as usual about BitTorrent info, but I would point out one change -- in newer versions of Transmission, the configuration directory is stored in ~/.config/transmission, not ~/.transmission... so make sure to make links / permissions for the correct directory.

---

