---
title: "How to return to running command after logging out of remote server?"
date: 2012-03-16
forum: General Help
---

### Post by beetlejelly on 2012-03-16
I am running a program via the command line that will take many hours to complete (imapsync)
I would like to be able to run the command, close the terminal window, then login again and see the status of the running program. Any help would be greatly appreciated.
I am not using the x windows environment.  I am logging into a remote server via ssh.

---

### Post by Derek Karpinski on 2012-03-16
```
sudo apt-get update && sudo apt-get install screen
```

---

### Post by jerome1232 on 2012-03-16
I like byobu, it's already installed (I think 10.10+), and it's just a newbie friendly profile for the aforementioned screen. You can create split/windows etc... with (for me) easier to remember shortcuts. 

```
byobu
```

---

