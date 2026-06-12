---
title: "clicked on update balloon and now video is 640x480:("
date: 2009-08-10
forum: General Help
---

### Post by breadbin on 2009-08-10
I had left it there for ages without updating and then when i did it did something to the display drivers. I downloaded the latest drivers from nvidia and went through the process of installing them again but there was some sort of error when i restarted x. so i tried installing the earlier drivers which were working grand and its just back to 640x480 and no other resolutions. i can't even use linux now cos the fan on my gpu turns off. so writing this in windows:(

my system is hardy heron and i have a 9800GT. anybody know the best way to fix it? like i said when i start the x server the fan turns itself off so i can't use it for long. if i reinstall a new version of ubuntu will my files be safe? like my home folder and stuff? tia

---

### Post by P4man on 2009-08-10
Dont download drivers from nvidia site, just use the repositories. Long answser short:

```
sudo apt-get install nvidia-glx-180 nvidia-180-modaliases
```

(assuming you are on jaunty)

---

### Post by breadbin on 2009-08-10
fixed it:) just copied xorg.conf.1 over the new xorg.conf and its perfect. now to disable the update balloon;)

---

### Post by 3rdalbum on 2009-08-10
> **breadbin said:**
> if i reinstall a new version of ubuntu will my files be safe? like my home folder and stuff? tia

Your home folder will be safe if you use the 'manual' partitioning method and don't elect to format the partition. I just did a Hardy-to-Jaunty install with this method and was very pleased that the contents of /home were preserved.

---

### Post by Toke on 2009-08-10
I tried that too, updating my grafics drivers.
Reinstalling Ubuntu worked.

---

### Post by breadbin on 2009-08-10
> **3rdalbum said:**
> Your home folder will be safe if you use the 'manual' partitioning method and don't elect to format the partition. I just did a Hardy-to-Jaunty install with this method and was very pleased that the contents of /home were preserved.

i might have a look at jaunty in a few days. have to make sure i back everything up first though. not going to risk it without;)

---

