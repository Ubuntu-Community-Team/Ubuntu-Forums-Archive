---
title: "Getting a remote desktop (kde) into a server install of ubuntu"
date: 2006-01-30
forum: General Help
---

### Post by glave on 2006-01-30
I installed ubuntu as a server installation on my media server, and now I'm looking to be able to have a remote desktop on the server (accessing from winxp), using kde. I don't necessarily want a desktop login while at the server console, but I could go either way.

I had heard you could get a kde desktop on a normal ubuntu by just doing a few apt-gets, but I honestly don't have a clue on where to begin for this.

---

### Post by bartbes on 2006-01-30
I've done this myself (now typing from KDE), the only thing I did was ```
 sudo apt-get install kde
``` but I don't have my language pack (dutch) working.

---

### Post by Stereotypical Rage on 2006-01-30
> Desktop Sharing for KDE
Desktop Sharing (krfb) is a server application that allows you to share
your current session with a user on another machine, who can use a
VNC client like krdc to view or even control the desktop. It doesn't
require you to start a new X session - it can share the current session.
This makes it very useful when you want someone to help you perform a
task.

This package is part of KDE, as a component of the KDE network module.
See the 'kde' and 'kdenetwork' packages for more information.

So I do believe all you'll want is "krfb", else you could SSH in and use the console.

---

