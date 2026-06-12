---
title: "No sound after switching users"
date: 2010-11-13
forum: General Help
---

### Post by mashedbear on 2010-11-13
The scenario I have is that sound works fine for the first user who logs onto the system, but when the session is switched to another user they often are unable to hear any sound.

The applications typically being used where the problems are experienced are banshee and Firefox (browsing iplayer, you tube or similar).

It appears if one user is using / has used sound and their session is still active - then no other users can have sound ... I know this shouldn't be the case!

A not very good workaround is to either log out other users, or force reloading alsa using
Code:

sudo alsa force-reload

Am using Ubuntu 10.10 64-bit (I had the same problem in Ubuntu 10.04 as well). I think I am running alsa version 1.0.23 (at least this is what alsactl --version returns), and pulse audio pulseaudio 0.9.21-63-gd3efa-dirty (found by running pulseaudio --version).

Would appreciate help if there is a known fix or some guidance on steps to try and work through, as this issue doesn't appear to be covered in Ubuntu community sound documentation.

Thanks

---

