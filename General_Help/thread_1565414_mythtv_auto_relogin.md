---
title: "mythtv auto relogin"
date: 2010-08-31
forum: General Help
---

### Post by slimx3m on 2010-08-31
i just recently install mythtv on a old machine which it meets mythtv requirements.  after setting up the backend and trying to finish the configuration i am running into problems.  whenever i finish setting up the backend properties and then it tries to go to mythtv main screen, my pc logs out and then logsin into a blank screen.  nothing that i do, ctrl+alt+bkspc, alt+fx, ctrl+alt+del, etc; works.

any thoughts would be appreciated.

thanks...

---

### Post by slimx3m on 2010-09-01
ok, after doing some research, i found my problem.  my problem is the X11.  1) didn't exist because is automatically generated in ubuntu 10.04.  2) when i created is currently not working in my machine.

when i ran the the following command
```
sudo Xorg -configure
```
a x11 gets generated..... great. but, whenever i do a
```
X -config /root/xorg.conf.new
```
i get the same output as if i would run mythtv.  so the problem i believe is whenever mythtv is going to execute x11 to run the interface.

source [http://ubuntuforums.org/showthread.php?t=1437980](http://ubuntuforums.org/showthread.php?t=1437980)


any body has any thought on how i could fix this issue?

---

