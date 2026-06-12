---
title: "Virtual box"
date: 2010-05-13
forum: General Help
---

### Post by Ädamas on 2010-05-13
i have been trying to get Virtual-box to work and it is showing me this.
[IMG]http://1.bp.blogspot.com/_BLpkrKAcI3U/S-veQcb6niI/AAAAAAAAADg/rDOjYLCfUJo/s1600/Screenshot.png[/IMG]

---

### Post by roccivic on 2010-05-13
If you have virtualbox-ose, then:
```
sudo apt-get install virtualbox-ose-dkms
```

otherwise, if you have the closed source edition check out their website.

---

### Post by sandyd on 2010-05-13
"sudo apt-get install dkms && sudo /etc/init.d/vboxdrv setup"  try running that (without quotes)

---

