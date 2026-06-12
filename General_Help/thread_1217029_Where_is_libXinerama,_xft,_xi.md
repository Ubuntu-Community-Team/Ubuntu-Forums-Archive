---
title: "Where is libXinerama, xft, xi???"
date: 2009-07-19
forum: General Help
---

### Post by simulacrum111 on 2009-07-19
Hello

I'm trying to port my application to ubuntu and I need libXinerama, libXft and libXi to do it.  I'm new to ubuntu...in fact I know nothing at all about the distro beyond what I hear on the streets.  I tried getting the binaries through synaptic and aptitude but failed.  That is most likely because I don't know where to look.

Knowing where to look bring me to my second question....

I am a developer.  I Ubuntu REALLY not for me?  I am not interested in argument.  I want insight.

This is the first time I've touched ubuntu and I have to admit its nice having the tedium of many things taken care of for me.  I wouldn't mind sticking with this distro if my early struggle are just a matter of education.  However, I have heard bad things and realize I truly know nothing when it comes to ubuntu.

I have to wonder how this distro is maintained if not a single one of its developers dare use it.  Either the claims of ubuntu stealing your cookies at night are exaggerated or those who keep this ship sailing are just so godlike would be development difficulties for me are but trivial amusements to pass the time for them.

I don't "why" I should lean one way or the other...but I would rather not learn things the hard way when I can simply ask in the first place.

---

### Post by jocko on 2009-07-19
> **simulacrum111 said:**
> Hello

I'm trying to port my application to ubuntu and I need libXinerama, libXft and libXi to do it.  I'm new to ubuntu...in fact I know nothing at all about the distro beyond what I hear on the streets.  I tried getting the binaries through synaptic and aptitude but failed.  That is most likely because I don't know where to look.

Knowing where to look bring me to my second question....

I am a developer.  I Ubuntu REALLY not for me?  I am not interested in argument.  I want insight.

This is the first time I've touched ubuntu and I have to admit its nice having the tedium of many things taken care of for me.  I wouldn't mind sticking with this distro if my early struggle are just a matter of education.[COLOR=Red]  However, I have heard bad things and realize I truly know nothing when it comes to ubuntu.

I have to wonder how this distro is maintained if not a single one of its developers dare use it.  Either the claims of ubuntu stealing your cookies at night are exaggerated or those who keep this ship sailing are just so godlike would be development difficulties for me are but trivial amusements to pass the time for them.

I don't "why" I should lean one way or the other...but I would rather not learn things the hard way when I can simply ask in the first place.[/COLOR]  

Welcome to ubuntu. You need the development headers for those libraries, so the names of the packages are libxinerama-dev, libxft-dev and libxi-dev. Just search for them in synaptic or use this command to install them:
```
sudo apt-get install libxinerama-dev libxft-dev libxi-dev
```You will probably need the package build-essential as well.

I have no idea where you heard your "bad things", but I'm sure it's just rubbish spread by some microsoft developer, or perhaps from some developer of one of the "for nerds, by nerds" distros that don't like the fact that ubuntu is usable by normal humans...

---

### Post by simulacrum111 on 2009-07-19
I believe I've gotten the x11 binaries I need with the following command line courtesy of google:

sudo apt-get install xorg-dev

Still, my second question is still open for anyone who wishes to comment.

---

