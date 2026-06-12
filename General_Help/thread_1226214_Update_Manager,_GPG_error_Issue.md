---
title: "Update Manager, GPG error Issue"
date: 2009-07-29
forum: General Help
---

### Post by oaxacamatt1 on 2009-07-29
Hey all,
Got a Update Manager issue.  I was updating today and got this message that came up after the update finished.  I have no idea what might have happened to cause this.

------------------
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C174A7B143CBFCC0
------------------

Any ideas?
M

---

### Post by michy99 on 2009-07-29
Try running these two commands in a terminal.```
gpg --keyserver subkeys.pgp.net --recv C174A7B143CBFCC0
gpg --export --armor C174A7B143CBFCC0 | sudo apt-key add -
```

---

### Post by oaxacamatt1 on 2009-07-29
SORRY, folks I just figured it out.  

(In the voice of Roseanne Roseanna-dan) 'Nevermind'

I added a site that allowed me to load the development packages for exaile.  I put the address in but couldn't find the GPG key on their website and 'went for it' anyway.  I just took out the repository-suppository and that cleared it up.

On the good side, I am learning...
;)
M

---

