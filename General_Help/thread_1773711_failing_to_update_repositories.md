---
title: "failing to update repositories"
date: 2011-06-02
forum: General Help
---

### Post by jon zendatta on 2011-06-02
for some reason I cannot update software or repositories.Failed to fetch etc. Thought trying a different mirror may help, where do I locate this.
okay so i changed mirrors. then 
sudo dpkg --configure -a
sudo apt-get clean

and got

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz)  Unable to connect to packages.medibuntu.org:http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
Do I need to alter my sources list. This wasn't a problem until now

---

### Post by Rubi1200 on 2011-06-02
What error messages, if any, do you get running this?

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by jon zendatta on 2011-06-02
ummm NO errors. I didn't try that command because I got stuck on *apt-get clean*
thanks I feel like a clown

---

### Post by Rubi1200 on 2011-06-02
Everything sorted now? Hope so.

There were some issues with downloads the last couple of days, but for the most part they seem to be resolved (usually by waiting a few hours before trying to update again).

---

