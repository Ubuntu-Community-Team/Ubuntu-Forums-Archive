---
title: "Help to restore encrypted /home"
date: 2010-11-19
forum: General Help
---

### Post by dudeua on 2010-11-19
Hi,

I'm in trouble after applying latest updates to my Ubuntu 10.10

After reboot I could login, but got the very same errors, as in this post: [Could not update ICEauthority]("Could not update ICEauthority")

To resolve, I applied the following steps:
```

sudo ecryptfs-add-passphrase --fnek 
sudo mount -t ecryptfs /home/dude/.Private /home/dude/Private 
```

These commands a are from this article: [EncryptedPrivateDirectory]("https://help.ubuntu.com/community/EncryptedPrivateDirectory")

Now I have to questions: 
1. I can see all of my files inside the /home/dude/Private directory using the 'ls' command, but cannot copy them. If I issue the 'cp' command it says file not found. 
And if I do 'sudo ls', I see encrypted names for my files. 

How can I copy those files to restore them??

2. Is it possible to mount this .Private permanently, so that I do not have to reinstall Ubuntu?

Please, help!

Thanks

---

### Post by dudeua on 2010-11-19
And by the way, I applied chown commands to my /home/dude, /home/dude/.Private folders. 

Now I can boot into Gnome, but with brand new home directory, all of my files are locked inside the .Private folder :(

---

