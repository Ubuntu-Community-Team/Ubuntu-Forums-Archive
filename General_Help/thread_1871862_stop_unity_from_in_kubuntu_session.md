---
title: "stop unity from in kubuntu session"
date: 2011-10-29
forum: General Help
---

### Post by elliotn on 2011-10-29
I have both ubuntu-desktop and kubuntu-desktop, when I login to kubuntu unity also loads, I want to have a clean kubuntu session at that time.
how can I stop this?

---

### Post by elliotn on 2011-10-30
Anyone

---

### Post by stinkeye on 2011-10-30
Never used kde. Does it use compiz or kwin?
...and by "unity" do just mean you can see the global menu.

**Edit**...anyway waited 20 mins for a response then you logged out.
If it's just the File Edit menu your seeing
Run
```
echo '[ "$DESKTOP_SESSION" != "ubuntu" ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy
```

which will remove the global menu from all but the ubuntu session.

---

### Post by elliotn on 2011-10-31
> **stinkeye said:**
> Never used kde. Does it use compiz or kwin?
...and by "unity" do just mean you can see the global menu.

**Edit**...anyway waited 20 mins for a response then you logged out.
If it's just the File Edit menu your seeing
Run
```
echo '[ "$DESKTOP_SESSION" != "ubuntu" ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy
```

which will remove the global menu from all but the ubuntu session.

sorry for the wait 
the code didn't work, yes am using compiz, the whole unity thing runs, the launchers, the panel etc, it just runs on top of kubuntu grrrrrr

---

### Post by stinkeye on 2011-10-31
Unity is a plugin for compiz.
Install **compizconfig-settings-manager** and disable the unity plugin.
If compiz doesn't load properly after disabling unity, run
```
compiz --replace
```

---

