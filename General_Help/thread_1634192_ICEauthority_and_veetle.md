---
title: "ICEauthority and veetle"
date: 2010-11-30
forum: General Help
---

### Post by mauribera on 2010-11-30
after installing trying to install veetle on my ubuntu 10.04 64 bit I always get the message at the start-up:
could not update /home/user/.ICEauthority
my sound control does not work anymore (message: 'waiting for sound system to respond')
using Krusader I get the message 'Cannot talk to klauncher: The name org.kde.klauncher was not provided by any .service files.

I checked the owner of .ICEauthority and the permission and they are OK. Same for my /home. None of the suggestions found in the other threads worked.

Does anybody know how to solve the problem?

Veetle has been installed using the install.sh script and there is no unistall option

Thanks in advance

---

### Post by philinux on 2010-11-30
This seems to be happening if you run the script as root. A few threads here with possible fixes.

[http://ubuntuforums.org/search.php?searchid=77762249](http://ubuntuforums.org/search.php?searchid=77762249)

---

### Post by mauribera on 2010-11-30
..thank you for the prompt reply. Is it not possible to go back? I mean to unistall veetle and restore the previous conditions?

---

### Post by mauribera on 2010-11-30
I solved the problem replacing the .ICEauthority in my home with the .ICEauthority version in /var/lib/gdm and changing ownership to the user.
Apparently veetle installation had damaged the origin in my home directory

---

