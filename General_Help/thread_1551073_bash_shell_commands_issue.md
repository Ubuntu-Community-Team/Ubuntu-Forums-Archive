---
title: "bash shell commands issue"
date: 2010-08-11
forum: General Help
---

### Post by Ready2DropWin on 2010-08-11
Hi,

I was trying to clean up tmp files on my laptop in bash, but when my laptop reboots it freezes instead of going into recovery mode and asking me to to boot as root. Is the commands right?

```

sudo killall gdm
sudo telinit 1    

```

After this is should reboot into recovery and then I should be able to type this

```

rm -rf /tmp/*
reboot    

```

Thanks for any help in advance.

---

