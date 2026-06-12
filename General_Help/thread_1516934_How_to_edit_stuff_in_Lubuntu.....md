---
title: "How to edit stuff in Lubuntu...."
date: 2010-06-24
forum: General Help
---

### Post by Linuxperiment on 2010-06-24
Hello everyone. I am trying out Lubuntu but I cannot find where the "file system" is....which is where /etc/rc.local is in. I am trying to make a command permanent but I'm so used to Ubuntu and where everything was. Can anyone tell me how to access it...or am I unable to? I really hate this "tap to click" on my laptop.

---

### Post by snowpine on 2010-06-24
Lubuntu is simply Ubuntu with the LXDE desktop environment instead of Gnome. You edit /etc/rc.local in exactly the same way:

```
sudo nano /etc/rc.local
```

Or if you prefer a GUI text editor:

```
gksu leafpad /etc/rc.local
```

The usual cautions apply; don't edit system files with "sudo" unless you know exactly what you are doing!

---

### Post by Linuxperiment on 2010-06-24
Thank you!

---

