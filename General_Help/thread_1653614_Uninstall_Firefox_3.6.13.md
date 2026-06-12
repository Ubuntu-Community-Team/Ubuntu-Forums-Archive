---
title: "Uninstall Firefox 3.6.13"
date: 2010-12-27
forum: General Help
---

### Post by prasadvj on 2010-12-27
Hi All, 

I have installed Firefox 3.6.13 as a LOCALAPPS in Ubuntu 9.10 using "apt-get install firefox" command. I would like to remove/uninstall the firefox 3.6.13 completely and install firefox 3.5.8. I have tried the command "apt-get remove firefox" but unfortunately it keeps all the folders as it is and does not allow to install firefox 3.5.8.

Any ideas to achieve the above would be of great help.

Thanks in anticipation

Prasad

---

### Post by sikander3786 on 2010-12-27
Try,

```
sudo apt-get remove --purge firefox
```

Then in your /home, press Ctrl + H to see the hidden files and delete the .mozilla directory.

Apart from that, any specific reason behind running an older version?

If you've some problems with 3.6.13, you might consider trying the FF 4 Beta.

---

