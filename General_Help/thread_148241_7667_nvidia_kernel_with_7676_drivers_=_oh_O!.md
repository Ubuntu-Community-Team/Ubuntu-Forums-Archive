---
title: "7667 nvidia kernel with 7676 drivers = oh O!"
date: 2006-03-21
forum: General Help
---

### Post by zombie1000 on 2006-03-21
Well basically i'll get straight to the point, I installed nvidia drivers version 7676 forgetting I had the ```
nvidia-kernel-common
``` package still installed which is version 7667 so now when I boot I get nothing til I ctrl-alt-F1 into console then when I run startx I just get the nvidia drivers complaining about the versions mismatching.

Is there anyway I can rectify this?

Simon

---

### Post by tseliot on 2006-03-21
Press ctrl-alt-F1
and type:
```
sudo /etc/init.d/gdm stop (OR "kdm stop" if you use KDE)
```

```
sudo apt-get --purge remove nvidia-kernel-common
```

cd path_to_the_nvidia_installer

And run the installer again (say yes if it asks you if you to overwrite your current driver)

---

### Post by zombie1000 on 2006-03-21
Yep thats sorted it!

Thank you very much!

Simon

---

