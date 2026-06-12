---
title: "quick commands to reinstall all display settings"
date: 2012-05-02
forum: General Help
---

### Post by goltoof on 2012-05-02
I use an nVidia card and desktop effects and multiple monitors have always been the biggest headache for me when it comes to ubuntu.  Using 11.04 with Unity was a steady degradation in visual performance, eventually all desktop effects stop working altogether.

I recently upgraded from 11.04 to 12.10, after getting the upgrade notification.  Everything went fine except my video settings are still whack. 

Is there a single command (or less than 5 commands) I can use to completely strip my system of all whack display configs and reset it to how it comes as a clean install?

And/or, uninstall all conlficting drivers from my system to make way fro nvidia drivers.  Something's conflicting I just don't know what.

---

### Post by kc1di on 2012-05-02
you can try this
in terminal 
```
sudo apt-get purge nvidia
```

---

### Post by goltoof on 2012-05-02
> **kc1di said:**
> you can try this
in terminal 
```
sudo apt-get purge nvidia
```

Thanks, but I've already tried reinstalling nvidia.  I could try it again, but removing nvidia may or may not change the fact that my desktop effects don't work anymore.  

I think I need to uninstall all conflicting drivers, then reinstall nVidia, I'm just not sure what else could be conflicting and keeping my desktop effects from working.

---

### Post by kc1di on 2012-05-02
Right now all you can do is uninstall nvidia and use the open source drivers.  There is a bug in the Nvidia Propriety drivers which causes Compiz to crash or work erratically. 
here's a link to the bug site :

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053")

---

### Post by goltoof on 2012-05-02
```

dpkg --get-selections |grep nvidia

```
... shows no nvidia is installed. However, typing "nvidia-settings" brings up the settings manager, which is odd.  Any attempt to move the nvidia-settings manager or any other package says it's not installed.

So why can't I get any desktop effects to work?  What else could I try?

---

### Post by goltoof on 2012-05-02
Anyone?

I know it's not nVidia since it's not installed.  I could try reinstalling xserver-xorg-video-nouveau, but can anyone else give their 2 cents on this?

---

### Post by goltoof on 2012-05-02
```

echo $DESKTOP_SESSION

```

Shows I was in 2d fallback

This solved it for me:
```

sudo apt-get purge xserver-xorg
sudo apt-get install xserver-xorg xserver-xorg-video-all

```

---

