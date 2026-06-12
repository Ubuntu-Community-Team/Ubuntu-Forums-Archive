---
title: "Minecraft"
date: 2011-03-06
forum: General Help
---

### Post by Flying Pig on 2011-03-06
When I try to play Minecraft classic in my browser (Chrome)it quickly says Minecraft in stone letters and then the screen just turns black... HELP!!!

---

### Post by ase1590 on 2011-03-06
the entire screen or just Minecraft itself?

---

### Post by mcduck on 2011-03-06
You need to install the proprietary Java version, and then set it as your default Java machine. After that Minecraft should work (although I've never tried playing it on the browser).

First run this (or install the sun-java6-plugin package using whatever package management tool you prefer:
```
sudo apt-get install sun-java6-plugin
```

After that's done run this and sett the Sun Java as the default:
```
sudo update-alternatives --config java
```

---

### Post by Flying Pig on 2011-03-06
just minecraft

---

