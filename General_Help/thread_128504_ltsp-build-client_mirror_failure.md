---
title: "ltsp-build-client mirror failure"
date: 2006-02-11
forum: General Help
---

### Post by turqy on 2006-02-11
hey all.  i previously used the ltsp-build-client tool about a month ago when i set up a terminal server just for kicks.  i'm trying to do it again now and i'm at the last stage, but whenever i try to run 'sudo ltsp-build-client' it fails to retrieve release from [http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release).

i know that it is locked into a single mirror and apparently that mirror is not working.  how can i change that mirror to one that likes me a bit more?

for those of you that are unfamiliar with ltsp stuff but want to chime in an educated guess a good place to look is here: [https://wiki.ubuntu.com/ThinClientHowto?highlight=%28thin%29%7C%28client%29](https://wiki.ubuntu.com/ThinClientHowto?highlight=%28thin%29%7C%28client%29)

thanks in advance for any solutions.

---

### Post by dcstar on 2006-02-11
[QUOTE=turqy]hey all.  i previously used the ltsp-build-client tool about a month ago when i set up a terminal server just for kicks.  i'm trying to do it again now and i'm at the last stage, but whenever i try to run 'sudo ltsp-build-client' it fails to retrieve release from [http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release).

i know that it is locked into a single mirror and apparently that mirror is not working.  how can i change that mirror to one that likes me a bit more?

for those of you that are unfamiliar with ltsp stuff but want to chime in an educated guess a good place to look is here: [https://wiki.ubuntu.com/ThinClientHowto?highlight=%28thin%29%7C%28client%29](https://wiki.ubuntu.com/ThinClientHowto?highlight=%28thin%29%7C%28client%29)

thanks in advance for any solutions.[/QUOTE]
Remove the "us." from your Repositories in Synaptic.

---

### Post by turqy on 2006-02-11
the ltsp-build-client app doesn't use the sources.list file i believe.  quoted from the wiki:

> #

Build the thin client runtime environment:

sudo ltsp-build-client 

    *

      This script is hardcoded to use a particular Ubuntu mirror, so you may wish to edit it if you have a nearby mirror or CD (sudo ltsp-build-client --mirror [WWW] file:///cdrom), remember to copy sources.list from the server into the chroot)
    *

      If you changed your aptitude dependency-settings not to select recommended packages automatically, not all required packages will be downloaded and installed by this script. Then no login with sdm is possible for example because some parts of the x-server are missing

obviously that partially contains my answer, but i don't understand the part about the chroot.  also i'm unsure of my kubuntu CD contains the packages i need, so i'd need an appropriate mirror.  on top of that i'm a complete noob to how apt-get works.

any suggestions?

---

### Post by stults on 2006-02-18
I'm having the same problem.  Has anyone got an answer???

---

