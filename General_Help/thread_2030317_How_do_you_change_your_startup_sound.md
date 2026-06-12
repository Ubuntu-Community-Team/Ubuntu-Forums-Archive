---
title: "How do you change your startup sound?"
date: 2012-07-20
forum: General Help
---

### Post by Redrum741 on 2012-07-20
How do you change your default startup sound?

---

### Post by Scott Baker on 2012-07-20
First, welcome to the forums. If you could, please provide the version of Ubuntu that you're running. There are a couple of ways to do this, and knowing what version you're running will help greatly. :roll:

---

### Post by Redrum741 on 2012-07-20
> **Scott Baker said:**
> First, welcome to the forums. If you could, please provide the version of Ubuntu that you're running. There are a couple of ways to do this, and knowing what version you're running will help greatly. :roll:

I'm using the latest version of Ubuntu. Ubuntu 12.04

---

### Post by drs305 on 2012-07-21
Here is a link to changing the sound and/or enabling sound preferences to be shown on the Startup Application preferences:

[http://www.linuxandlife.com/2012/05/how-to-turn-off-or-change-login-sound.html]("http://www.linuxandlife.com/2012/05/how-to-turn-off-or-change-login-sound.html")

To just turn it (on/)off, you can install Ubuntu Tweak (see link in my signature line) or run this command:

```
gsettings set com.canonical.unity-greeter play-ready-sound "false"
```

---

