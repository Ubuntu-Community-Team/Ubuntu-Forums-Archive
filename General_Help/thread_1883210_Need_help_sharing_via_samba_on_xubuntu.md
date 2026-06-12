---
title: "Need help sharing via samba on xubuntu"
date: 2011-11-18
forum: General Help
---

### Post by zensawa on 2011-11-18
Hello folks, I Have recently switched OS from ubuntu to xubuntu. Now I liked the way I could share with samba share on ubuntu. I would simply goto PLACES > CONNECT TO SERVER > SELECT WINDOWS SHARES > TYPE IP ADDRESS > TYPE PASSWORD > CONNECTED.

Can anyone guide me through the process of doing this on xubuntu?

---

### Post by Toz on 2011-11-18
First instal gvfs-backends - look for it in the Software Centre, or:
```
sudo apt-get install gvfs-backends
```

Then open Thunar, click on "Network", traverse to the server and click on the share. You will be asked for a username and password. The actual mounts can be found in the hidden .gvfs directory in your home directory.

OR...

use Gigolo. I believe its installed by default on 11.10. If not, look for it in the Software Centre or:
```
sudo apt-get install gigolo
```

---

### Post by zensawa on 2011-11-21
Thanks! Work like charm.     :guitar:

---

### Post by Toz on 2011-11-21
Glad to hear. Can you please make the thread Solved from the Thread Tools link above?

---

