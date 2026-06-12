---
title: "parcellite"
date: 2012-04-28
forum: General Help
---

### Post by gimcrack on 2012-04-28
I couldn't get parcellite clipboard-manager to work. So I found an alternative to work in Unity. This clipboard-manager is called Diodon. It seems to work fine. But has anyone got Parcellite to work in Unity? My never did open up.

---

### Post by marinara on 2012-04-29
can't help with unity

---

### Post by nothingspecial on 2012-04-29
Changed prefix from Lubuntu to Ubuntu.

---

### Post by Rodney9 on 2012-04-29
You could try clipman.

Rodney

---

### Post by stinkeye on 2012-04-29
> **gimcrack said:**
> I couldn't get parcellite clipboard-manager to work. So I found an alternative to work in Unity. This clipboard-manager is called Diodon. It seems to work fine. But has anyone got Parcellite to work in Unity? My never did open up.
Some programs that use the indicator need to be white listed to use the systray.

Get your current white listed apps.
```
gsettings get com.canonical.Unity.Panel systray-whitelist
```


Add parcellite to the white listed apps...
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'Update-notifier'[COLOR="Red"], 'parcellite'[/COLOR]]"
```

Log out/in for changes to take effect.

Tried most of the clipboards and like glipper the best.
Has a plugin for adding snippets.

---

### Post by gimcrack on 2012-04-29
Thanks stinkeye

First time I heard about this whitelist. It works now, thanks for solving this problem. I learn something new today.

---

