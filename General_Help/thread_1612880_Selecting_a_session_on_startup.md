---
title: "Selecting a session on startup"
date: 2010-11-03
forum: General Help
---

### Post by rmcellig on 2010-11-03
I have a few sessions as shown in the attached file. When I start up my machine and get to the login screen, I don't see anywhere on the screen where to select the session I want to startup in. I even checked along the bottom of the screen and all I have is an icon that when clicked allows me to restart/shutdown the machine.

How can I select whatever session I want to login into on startup?

Is there also some kind of session manager I can install as well?

I am using Ubuntu 10.10.

---

### Post by sikander3786 on 2010-11-03
Ubuntu by default comes with the GDM login manager and it shows the sessions options after you click your username.

You can try running

```
sudo dpkg-reconfigure gdm
```

And select gdm to make it your default login manager.

---

### Post by rmcellig on 2010-11-04
Thanks! I just noticed that.

---

