---
title: "how can I get unity back?"
date: 2012-05-13
forum: General Help
---

### Post by garyed on 2012-05-13
I was running 11.10 & didn't like unity so after some googling I found a way to disable it which I can't remember completely. Now that I've upgraded to 12.04 I'd like to try unity again but I can't find how to get it back. The only thing I remember changing is the lightdm.conf file but that hasn't helped.
Any ideas?

---

### Post by kc1di on 2012-05-13
you should be able to install unity from the software center or by this command in a terminal.

```
sudo apt-get install unity
```

---

### Post by wilee-nilee on 2012-05-13
Unity is the ubuntu-desktop, you need to find that original remove unity site I suspect to really get help with this.

---

### Post by garyed on 2012-05-13
> **kc1di said:**
> you should be able to install unity from the software center or by this command in a terminal.

```
sudo apt-get install unity
```

The problem is unity is already installed so I just get the message that the newest version is already installed. Whatever files I changed kept it from being the default desktop when I upgraded.

---

### Post by poloivan on 2012-05-13
Are you able to do it by Logging out and selecting Ubuntu 3D?

Regards.

---

### Post by Randymanme on 2012-05-14
At [http://askubuntu.com/questions/70572/reset-unity-and-gnome-to-default-values](http://askubuntu.com/questions/70572/reset-unity-and-gnome-to-default-values) I see the following advice:


[LIST=1]
[*]If you want to reset Unity (this will only reset the Unity  settings in CompizConfig Settings Manager and leave the other CCSM  settings intact), open a terminal (or press ALT + F2) and enter:
  unity --reset
[*]If you want to reset the Unity Launcher icons (dock bar on the left) to their initial state, run the following command:
  unity --reset-icons
[/LIST]

---

### Post by Randymanme on 2012-05-14
And [http://www.omgubuntu.co.uk/2012/01/gnome-shell-unity-2d-dock-unitary-gnome/](http://www.omgubuntu.co.uk/2012/01/gnome-shell-unity-2d-dock-unitary-gnome/) shows us how to install a modified Unity 2d launcher inside of Gnome Shell.  And  [http://www.youtube.com/watch?v=_gnuAkXW5Rs](http://www.youtube.com/watch?v=_gnuAkXW5Rs) shows us how it works.

---

