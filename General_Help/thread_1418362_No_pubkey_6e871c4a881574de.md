---
title: "No_pubkey 6e871c4a881574de"
date: 2010-02-28
forum: General Help
---

### Post by Emascu on 2010-02-28
Hello.

I've been using kubuntu for the past year on my laptop and last week I decided to install ubuntu and use it as primary desktop environment but now I'm having some trouble. The first few minutes after I start up it's all fine but after a few minutes something strange happens. All the sudden all compiz effects are off and things and icons are all weird. The other day panels, icons and everything even started blinking.

When I try sudo apt-get update I also get an error of which I assume got something to do with it.

This is the last few lines of what the terminal tells me. It's in dutch though but I hope you'll be able to figure it out, the error message is still in english.

...
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic-updates/multiverse Packages
Geraakt [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic-updates/multiverse Sources
308B opgehaald in 0s (675B/s)
Pakketlijsten worden ingelezen... Klaar
W: GPG-fout: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: De volgende ondertekeningen konden niet geverifieerd worden omdat de publieke sleutel niet beschikbaar is: NO_PUBKEY 6E871C4A881574DE
lars@lars-linux:~$

I will just translate the last sentence: The following signature could not be ferrified because the public key is not available: NO_PUBKEY 6E871C4A881574DE

I hope anyone can help me. Step by step please.

---

### Post by fooman on 2010-02-28
to fix the update error,  open a terminal and type or copy/paste the following:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 881574DE
```

then try to update again....hope that helps.

---

