---
title: "Nvidia startup help"
date: 2012-06-03
forum: General Help
---

### Post by Derek Karpinski on 2012-06-03
I wanted to show the startup applications so I ran the widely accepted code:

```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```I disabled bluetooth and others I don't need.  But I noticed that my symbolic link on nvidia-autostart.desktop is broken now.  I didn't realize 'sed -i' breaks links.

So, can someone with nvidia drivers tell me where the following file is linked to?  Please run:

```
readlink /etc/xdg/autostart/nvidia-autostart.desktop
```Or can I fix this broken link with something like 'update-alternatives'?

Thanks!

---

