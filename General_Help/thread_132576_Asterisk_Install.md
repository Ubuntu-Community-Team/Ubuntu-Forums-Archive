---
title: "Asterisk Install"
date: 2006-02-18
forum: General Help
---

### Post by fizgig on 2006-02-18
I'm trying to install Asterisk from scratch on Breezy server.  This thread will be my notepad that might also help others.  I'm not saying it's the right way - just the only way I was able to get through it...  Also, it's not complete since you have to apt-install a bunch of crap I have since forgotten (build tools, zlib stuff, etc...) but I might come back and fill that out.

**Build zaptel drivers:**
No issues

[B]Build libpri:
[/B]No issues

[B]Build Asterisk:
[/B]Initial compile failed.  It told me: *chan_zap.c:111:2: error: #error "Your zaptel is too old.  please update"* which was weird since I had just got it through svn.

Stay tuned as I try to get this sorted out - google doesn't have much info on this error so I might be up a creek here...

---

