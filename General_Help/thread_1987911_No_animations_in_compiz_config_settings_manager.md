---
title: "No animations in compiz config settings manager"
date: 2012-05-26
forum: General Help
---

### Post by PhantomTurtle on 2012-05-26
As the title says, its not there. I changed some settings a while ago in the animations tab, so it was there before. I have attached a screenshot of ccsm. Anybody have any idea what's going on?

---

### Post by Zvlwab on 2012-05-26
This should do the trick:
```
sudo apt-get install compiz-fusion-plugins-extra
```

---

### Post by PhantomTurtle on 2012-05-26
> **Zvlwab said:**
> This should do the trick:
```
sudo apt-get install compiz-fusion-plugins-extra
```

Thank you for that, but it did not help. I still can't see the animations. I have a screenshot with what I am missing. The thing that is circled is not in mine. I get everything there except Animations.

---

### Post by Zvlwab on 2012-05-27
Are all of the following packages installed?
```
you@pc:~$ dpkg -l | grep compiz
...
ii  compiz-fusion-plugins-extra                                 0.9.7.0~bzr9-0ubuntu6                   transitional dummy package.
ii  compiz-fusion-plugins-main                                  1:0.9.7.0~bzr19-0ubuntu10               transitional dummy package.
ii  compiz-plugins                                              1:0.9.7.8-0ubuntu1                      OpenGL window and compositing manager - plugins
ii  compiz-plugins-default                                      1:0.9.7.8-0ubuntu1                      OpenGL window and compositing manager - default plugins
ii  compiz-plugins-extra                                        0.9.7.0~bzr9-0ubuntu6                   Collection of extra plugins from OpenCompositing for Compiz
ii  compiz-plugins-main                                         1:0.9.7.0~bzr19-0ubuntu10               Compiz plugins - main collection
ii  compiz-plugins-main-default                                 1:0.9.7.0~bzr19-0ubuntu10               Compiz plugins - main default collection
...
```

If you're missing any of those packages, it's probably the one you need to install.

---

### Post by PhantomTurtle on 2012-05-27
I have all those,
```
me@pc:~$ dpkg -l | grep compiz
ii  **compiz**                                                        1:0.9.7.8-0ubuntu1                      OpenGL window and compositing manager
ii  **compiz-core**                                                   1:0.9.7.8-0ubuntu1                      OpenGL window and compositing manager
ii  **compiz-fusion-plugins-extra**                                   0.9.7.0~bzr9-0ubuntu6                   transitional dummy package.
ii  **compiz-gnome**                                                  1:0.9.7.8-0ubuntu1                      OpenGL window and compositing manager - GNOME window decorator
ii  **compiz-plugins**                                                1:0.9.7.8-0ubuntu1                      OpenGL window and compositing manager - plugins
ii  **compiz-plugins-default**                                        1:0.9.7.8-0ubuntu1                      OpenGL window and compositing manager - default plugins
ii  **compiz-plugins-extra**                                          0.9.7.0~bzr9-0ubuntu6                   Collection of extra plugins from OpenCompositing for Compiz
ii  **compiz-plugins-main**                                           1:0.9.7.0~bzr19-0ubuntu10               Compiz plugins - main collection
ii  **compiz-plugins-main-default**                                   1:0.9.7.0~bzr19-0ubuntu10               Compiz plugins - main default collection
ii  **compizconfig-backend-gconf**                                    0.9.5.92-0ubuntu5                       Compiz Fusion configuration system - gconf backend
ii  **compizconfig-settings-manager**                                 0.9.5.92-0ubuntu3                       Compiz configuration settings manager
ii  **libcompizconfig0**                                              0.9.7.0~bzr428-0ubuntu6                 Settings library for plugins - OpenCompositing Project
ii  **python-compizconfig**                                           0.9.5.94-0ubuntu4                       Compizconfig bindings for python

```

The thing is I edited the minimize animation a while ago so I know it was there before.

---

### Post by Zvlwab on 2012-05-27
Maybe reinstalling ccsm helps
```
sudo apt-get purge compizconfig-settings-manager && sudo apt-get install compizconfig-settings-manager
```

---

### Post by PhantomTurtle on 2012-05-27
> **Zvlwab said:**
> Maybe reinstalling ccsm helps
```
sudo apt-get purge compizconfig-settings-manager && sudo apt-get install compizconfig-settings-manager
```

It is still the same, but thanks anyway's. Have anything else?

---

