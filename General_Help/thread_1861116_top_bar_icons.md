---
title: "top bar icons"
date: 2011-10-15
forum: General Help
---

### Post by kadlam on 2011-10-15
RE: Ubuntu 11.10
How do program icons get added to the bar at the top of the screen?
Example: When I installed skype, it put the nice little green icon in the bar. 
I would like to do the same with programs or open terminals.
Suggestions?

k

---

### Post by Frogs Hair on 2011-10-15
If you are using Unity , it no longer has the Gnome panel and icons can't be added by drag and drop anymore . This option was excluded in Unity 11.04 also . 

I have not tried the Gnome shell yet and don't know if the fall back mode has this option or not .  

It is possible to white list some application by using the command below .```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

---

