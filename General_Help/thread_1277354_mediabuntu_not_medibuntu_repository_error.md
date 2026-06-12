---
title: "mediabuntu not medibuntu repository error"
date: 2009-09-28
forum: General Help
---

### Post by inverse-linux on 2009-09-28
hi,
whilst following a tutorial for adding the medibuntu repository I inadvertently typed mediabuntu instead of medibuntu into the command line. It seemed to add some info, I now have files called mediabuntu.list and mediabuntu.list.save in my etc/apt/sources.list.d folder but now all attempts to update ubuntu fail with an error messages saying 'Error opening the cache '<!DOCTYPE>' is not known on line 1 in source list etc/apt/sources.list.d/mediabuntu.list
I think the docs that have been installed here are web code and not valid file types.
I have since corrected the script I ran and therefore also have medibuntu.list files in the correct place and the correct type. I guess I need to delete the erroneous entries but sudo rm /etc/apt/sou... in the command shell returns 'no such file or directory found'. I think the system should have protection built in to prevent the wrong list type from copying to the sources directory.

---

### Post by wojox on 2009-09-28
Try:

```
gksudo nautilus
```

This will open nautilus with root permissions. Go to etc/apt/sources.list.d/mediabuntu.list and delete them.

---

### Post by inverse-linux on 2009-09-28
That got rid of them... thank you so much for the help.
Getting a security key notice error now but I can probably deal with that.
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89
Thanks again :)

---

