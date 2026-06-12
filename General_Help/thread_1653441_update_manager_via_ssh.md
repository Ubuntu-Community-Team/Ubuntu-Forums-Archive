---
title: "update manager via ssh"
date: 2010-12-26
forum: General Help
---

### Post by Dex73 on 2010-12-26
Can update manager be controlled through ssh. Just the functions of downloading updates and installing them. I want to be able to use the key board of this laptop to run some basic commands for update manager on the other one and, if it is possible, then what two commands do I need?

---

### Post by b0b138 on 2010-12-26
It should be. Once you've made the ssh connection to the remote computer, it's the same commands you would use locally. ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
```

---

### Post by Dex73 on 2010-12-27
Thanks for the commands. I already have ssh up and running and now I can update my parents laptop when they continuously forget!

---

