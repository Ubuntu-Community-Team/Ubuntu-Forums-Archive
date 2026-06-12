---
title: "Trouble Accessing Encrypted partition with Live CD"
date: 2011-04-25
forum: General Help
---

### Post by PhillyKingston on 2011-04-25
I found this website [http://bodhizazen.net/Tutorials/Ecryptfs/#Live](http://bodhizazen.net/Tutorials/Ecryptfs/#Live), and am able to go all the way up to "ecryptfs-mount-private" command, but the response I get after entering my login passphrase is "mount: Operation not permitted".  I am not sure why though I am guessing I have a permission issue.

---

### Post by PhillyKingston on 2011-04-25
Did some searching and this has a better explanation [http://ubuntuforums.org/showthread.php?t=1357556](http://ubuntuforums.org/showthread.php?t=1357556).  I used "/mnt" instead of "/home/user/old-home".  Using these commands will transfer it somewhere else for you automatically.

```

$ mkdir <new location> 
$ rsync -va /mnt/ <new location>

```

---

