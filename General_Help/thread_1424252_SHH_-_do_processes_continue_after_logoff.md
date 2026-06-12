---
title: "SHH - do processes continue after logoff?"
date: 2010-03-07
forum: General Help
---

### Post by Red Penguin on 2010-03-07
Hi, I'm running a headless server, connecting remotely with ssh. Currently, I'm using aria2c to download from a list of urls in a text file. I've got it running in the background and logging output to a separate text file.

My question is, will aria continue downloading if I log out of the shell?

Also, I've previously used crontab to automatically start processes, and I'm thinking that I can write a simple bash script to launch aria with the parameters I want, and use crontab to set it to start at a certain time. Is this possible?

Thanks

RP

---

### Post by falconindy on 2010-03-07
No, it won't. You need to leave the program running inside screen or tmux.

---

