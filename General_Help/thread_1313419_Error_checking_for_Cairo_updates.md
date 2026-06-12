---
title: "Error checking for Cairo updates"
date: 2009-11-03
forum: General Help
---

### Post by jesuisbenjamin on 2009-11-03
I recently upgraded from Intrepid to Jaunty and i use Cairo Dock.

Checking for updates, synaptic returns:
> W: GPG error: [http://repository.cairo-dock.org](http://repository.cairo-dock.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1392A97E41317877

My 3rd party software sources show: 
> [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu)
Jaunty
cairo-dock

What does this mean?
Thanks for your help.

---

### Post by fabounet on 2009-11-04
did you follow the method on wiki.cairo-dock.org ?
you have to record the private key of the repository to avoid such message

---

### Post by jesuisbenjamin on 2009-11-04
Thanks Fab,

but i just can't find any reference to any private key on the wiki, the search engine returns an error.
Do you more precise references to this how-to please?

Thanks

---

### Post by fabounet on 2009-11-04
here it is ;-)
[http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en")

---

### Post by jesuisbenjamin on 2009-11-04
OK thanks it went well, but what is the key-thing about?

---

### Post by fabounet on 2009-11-05
repositories are signed (by a key) for security reason (avoid phishing or such thing).

---

