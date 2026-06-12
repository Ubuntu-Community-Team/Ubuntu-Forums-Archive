---
title: "Successful Install, But No GUI, How Do I?"
date: 2010-02-14
forum: General Help
---

### Post by Jeffrey Wilinski on 2010-02-14
I've been able to do a successful intall of Ubuntu, version 8.xx, but I do not have a GUI. There is a startup error, but idk if it is related. It says: "Your sys does not have the cpu extensions required to use kvm. Not doing anything." I would just like to know how to get a gui.

---

### Post by jocko on 2010-02-14
Don't worry about that "error" message. It is not an error, just a piece of information that you don't need to care about. If you don't know what kvm is, I don't think you will ever need it.

But first of all, why did you install an "8.XX" version (that is one of the two releases from 2008; 8.04 and 8.10)? The current release is 9.10 (named so because it was released in october 2009).
Second, when you say you have no gui, do you mean you made a minimal, command-line only install from an alternate cd or a server cd, or do you mean that you made a full install from a live cd (or an alternate cd), but somehow the gui fails to start?

---

### Post by snowpine on 2010-02-14
Try this (assuming you want Gnome as your GUI):

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
startx
```

---

### Post by Jeffrey Wilinski on 2010-02-14
snowpine; awesome!!! :D I can't believe it. Everything downloaded and I was able to configure the GUI with your instructions. The only unanswered question is, why didn't it install in the beginning, or maybe it wasn't supposed to?

---

### Post by Jeffrey Wilinski on 2010-02-14
> **snowpine said:**
> Try this (assuming you want Gnome as your GUI):

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
startx
```
Awesome snowpine. This is quite a large step up from my older linux versions. I guess my only open question is, was the gui supposed to install in the beginning?

---

### Post by stoneage on 2010-02-14
Like jocko said, it depends whether you installed a server or a desktop version. If you run the live CD you installed from is there a desktop?

---

### Post by snowpine on 2010-02-14
Glad it worked out. :) For future reference, I think there is an option when you first boot the CD, which type of install to use... it's been a while but I think it's one of the Fn keys (F6? F4?)

---

