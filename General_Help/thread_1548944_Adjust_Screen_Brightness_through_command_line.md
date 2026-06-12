---
title: "Adjust Screen Brightness through command line"
date: 2010-08-09
forum: General Help
---

### Post by gunjannigam on 2010-08-09
I have bought a Lenovo Ideapad S10-3 Netbook and installed Ubuntu 9.04 on it. I want to control the brightness of the scree using terminal. I tried

```

sudo echo 60 > /proc/acpi/video/IGD0/DD01/brightness

```

It executed, but the brightness of screen remained same. I dont have a LCD folder inside ```
/proc/acpi/video
```. I only have IGD0 folder.

My screen brightness changes by using Fn key and Brightness applet but not from terminal. what could be the cause of problem

---

