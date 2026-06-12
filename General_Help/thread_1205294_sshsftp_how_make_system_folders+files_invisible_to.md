---
title: "ssh/sftp: how make system folders+files invisible to ftp users?"
date: 2009-07-05
forum: General Help
---

### Post by ruipedroca on 2009-07-05
hi,

i'm running a ssh/sftp server inside a vpn-lan.

how make system folders+files invisible to ftp users?

---

### Post by Jebtrix on 2009-07-05
Not without editing the source code yourself. Only alternative I know is proftpd (with mod_sftp) and use "IgnoreHidden on" option in the config.

---

### Post by Boondoklife on 2009-07-05
You could check out if your server app supports jailing, this way they only have access to what you want.

---

### Post by ruipedroca on 2009-07-14
Thanks :p

---

