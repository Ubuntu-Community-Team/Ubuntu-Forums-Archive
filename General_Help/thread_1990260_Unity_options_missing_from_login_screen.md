---
title: "Unity options missing from login screen"
date: 2012-05-29
forum: General Help
---

### Post by xeddog on 2012-05-29
I have installed Ubuntu Precise 12.04 64-bit and played with Unity for a while, but I don't care for Unity.  So I installed Xubuntu desktop and I am much happier with it.  When I boot my machine, it automagically boots the xubuntu session which is what I want.  On occasion though, I have used the "Logout" option and then when I get the login panel I select Unity and run that for a while.  I'm still trying to like Unity but I am not having much luck with that for now.

Anyway, recently Unity is not showing up in the session options any more.  Everything else seems to be there like gnome classic etc., but no Unity.  I tried using synaptic and re-installing several of the unity packages but no joy.  I also tried 

```
sudo apt-get install unity
```

and it tells me that unity is already the latest version.

I don't know why the are gone now because I haven't made any changes to my computer for a while, but I would like to have them back.  How can I do that?

Thanks,

Wayne

---

### Post by kmsalex on 2012-07-23
Try 

```
sudo apt-get install ubuntu-desktop
```

---

### Post by xeddog on 2012-07-29
That worked.  Thanks.  Made me wonder when I rebooted because Xubuntu was then missing from the menu, but it was back the next time I booted so all is right once again.

---

