---
title: "Ubuntu 10.04 Cannot login after downgrading GDM"
date: 2011-01-20
forum: General Help
---

### Post by silkworm2.5 on 2011-01-20
Hi all!
I recently decided to downgrade the GDM login screen manager to allow me to use some of the custom log-in screens at [www.gnome-look.org](www.gnome-look.org). I managed to get it to work, but then decided I wanted to revert back to the default login screen.

I went into the Software centre and installed GDM. It then Restarted the X server to accommodate the new GDM. It then just kept looping the boot animation. I pressed escape to view the text feedback, and it was stopped at "Checking Battery State".

I now cannot log in because of this. I can press Ctrl+Alt+F1 to swap over to a CLI, and that allows me to log in, but beyond logging in, I don't know how to do much else. can anyone help please?

I am running Ubuntu 10.04 64 bit, on a Compaq Altec Lansing Presario CQ61.

---

### Post by FluxboxUser on 2011-01-20
You could try to start an CLI session and reinstall GDM

---

### Post by silkworm2.5 on 2011-01-21
Well, it took me a while, but I got to do that. I now have the GDM installed, but it wont run automatically. In the CLI if i try to run "GDM" it says
```
(gdm-binary:1669): WARNING**: Failed to acquire org.gnome.DisplayManager: connection ":1.12" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file.

(gdm-binary:1669): WARNING**: could not acquire name; bailing out

```

But if I type in sudo gdm, it will run the GDm. So, what should I do?

---

### Post by silkworm2.5 on 2011-01-21
After looking around, I got to the gdm.conf-custom file in /etc/gdm. I see it has two themes it tries to load:

```
SystemMenu=false

GraphicalTheme=gdmtheme

GraphicalThemes=happygnome/:circles


DefaultWelcome=false

Welcome=You are now accessing %n
```

Circles was I think, the default theme of the older GDM manager I had. could it be these two line are conflicting?

---

