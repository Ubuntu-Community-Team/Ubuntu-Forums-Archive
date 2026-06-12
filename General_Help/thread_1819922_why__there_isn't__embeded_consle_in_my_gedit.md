---
title: "why  there isn't  embeded consle in my gedit??"
date: 2011-08-07
forum: General Help
---

### Post by luofeiyu on 2011-08-07
i have install plugins ,and active it,please the attachment 
sudo apt-get install gedit-plugins  
why i can't see the  embeded  console in my gedit when i restart it??

---

### Post by jwbrase on 2011-08-07
You need to tick the "bottom pane" checkbox in the view menu. If it's greyed out, try activating and deactivating the python console plugin. For some reason that seems to make it so that you can get the bottom pane to appear.

In any case, I have been able to get the bottom pane to appear and the terminal to show up in it, but the terminal does not seem to launch a shell and causes gedit to eat up loads of CPU (I'm on 64 bit Ubuntu 10.04). It seems there's a bug in the plugin that makes it useless.

---

