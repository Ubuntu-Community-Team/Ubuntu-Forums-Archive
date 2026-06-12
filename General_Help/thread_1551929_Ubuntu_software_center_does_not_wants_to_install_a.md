---
title: "Ubuntu software center does not wants to install anything"
date: 2010-08-12
forum: General Help
---

### Post by m_ghv_geo on 2010-08-12
Ubuntu software center does not wants to install anything

when i select software and press to install it does nothing

does someone knows a way to fix this?

---

### Post by Quackers on 2010-08-13
Do you mean that it does nothing at all?
When you click on the program you want to install and look to the right side you will see the install tab. Click on that and you should see 2 little green arrows spinning round in a circle on the left panel of the display. This runs until the install finishes. Is this not happening for you?
Or do you mean that you cannot find the program once the install finishes?

---

### Post by m_ghv_geo on 2010-08-13
no i said when i press install it does nothing completely nothing

---

### Post by snowpine on 2010-08-13
What is the name of the program you are trying to install?
Try installing it from the terminal (Applications, Accessories, Terminal). Copy & paste the entire output here.

For example to install firefox:

```
sudo apt-get update
sudo apt-get install firefox
```

(substitute the actual name of the application you're trying to install instead of 'firefox')

---

### Post by philinux on 2010-08-13
> **m_ghv_geo said:**
> Ubuntu software center does not wants to install anything

when i select software and press to install it does nothing

does someone knows a way to fix this?

Open a terminal, Apps>access and run it. See if any errors appear.

```
software-centre
```

When you click install it's supposed to ask for your login password.

---

### Post by m_ghv_geo on 2010-08-16
right know it started working by it self

---

