---
title: "invoke-rc.d: initscript gdm, action &quot;reload&quot; failed."
date: 2009-08-19
forum: General Help
---

### Post by t.rei on 2009-08-19
Hello,

for quite a while now I wanted to switch back to gdm and gnome (while currently deploying kdm and kde4) due to missing features that outweigh any "beauty" that kde4 provides.

however whenever I try to reconfigure or reinstall gdm I get:

```
 
* Reloading GNOME Display Manager configuration...                                                                                     
* Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.
```this happens when I do:
sudo dpkg-reconfigure gdm
sudo apt-get install --reinstall gdm
sudo apt-get purge gdm && sudo apt-get install gdm
...

Anything I found in some anchient results on google, bing, etc did NOT resolve this issue. Yet I am reluctant to do it the windows way and "just" reinstall, since that won't get me any smarter. ;) 

Does anyone have an idea what is going on?

thanks in advance.

---

### Post by t.rei on 2009-09-02
I am still having this problem.

No help to be found. :( 

Btw: when I do "dpkg-reconfigure kdm" it just returns without giving me the option to choose.


*edit*
one "solution" is to edit /etc/X11/default-display-manager and change its single line entry manually to "/usr/**s**bin/gdm" after having stopped kdm using /etc/init.d/kdm stop. One can then start gdm by running /etc/init.d/gdm start.

So it just seems to be broken to reconfigure kdm/gdm via apt oder dpkg.

---

### Post by mastermindg on 2010-01-27
I'm having the same issue. I ended up having to kill kdm and start gdm at login prompt.

---

