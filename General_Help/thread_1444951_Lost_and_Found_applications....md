---
title: "Lost and Found applications..."
date: 2010-04-02
forum: General Help
---

### Post by jlubey on 2010-04-02
Hey guys,
im fairly new to ubuntu, but i think im getting the hang of it. i just have a quick question:

i booted up my kubuntu partition, and for some reason the icons for some of my quick launch applications were missing. i investigated more and apparently 4 applications got moved to the ¨Lost and Found¨ folder in my application Launcher. (Amarok, Opera, Kopete, and Thunderbird). i have no idea why this happened, or what it means. what i would like to know is how to move them back where they belong and get their icons back (im assuming a simple uninstall and re-install would work here, but im not sure what commands to use. sudo apt-get install --reinstall didnt help).

Kubuntu 9.1, fully updated
any help would be greatly appreciated!! Thanks!

---

### Post by JoelOl75 on 2010-04-02
The lost+found directory is a so called dumping ground for files that had/have corrupted inodes.  They were placed there from the fsck'ing the drive.  Maybe you hard resetted?  Pulled the plug?  Not properly unmounted the filesystem after use?

---

### Post by jlubey on 2010-04-02
nope, i cant think of anything that would have caused this. i finally fixed it by pokin around my entire filesystem, and there were still a few files for those applications. i manually deleted them, and its all better now. Thanks!

---

