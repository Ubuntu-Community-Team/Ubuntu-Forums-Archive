---
title: "trn newsreader authentication"
date: 2011-02-26
forum: General Help
---

### Post by linfidel on 2011-02-26
I was trying to set up the trn newsreader, and I'm going crazy trying to get it to run.  It fails with an error "Unknown response code 480", which is an authentication error.

My news server uses pretty standard authentication.  I can connect using telnet, using the "authinfo name/pass" commands, with no problem.  I've tried all combinations of entering the information in the configuration file ~/.trn/access.  I suspect it may not even be reading this file, as I tried putting in a bogus name for the server config file in /etc/news, and it didn't notice.

I've searched Google and found a couple of posts that say to do the same thing I'm doing, but they were all sketchy and I don't know if anyone got it to work.  Also, it wasn't for Ubuntu.

Anyone ever get trn or rn to work on Ubuntu?

---

### Post by linfidel on 2011-02-27
Somehow, between installing and uninstalling newsreaders, and looking through source code, etc, I've gotten the trn4 version to work.  Once it starts working, there is some help to get it working; someone seems to have missed the point there.

Now, as to whether it was worth it...  I'll have to see.  :)

---

