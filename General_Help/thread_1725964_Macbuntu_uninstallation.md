---
title: "Macbuntu uninstallation"
date: 2011-04-10
forum: General Help
---

### Post by whonut on 2011-04-10
hi, I installed Macbuntu but don't like it, so I tried to uninstall but the uninstall.sh file won't run

Why is this? Or can I uninstall it a different way

---

### Post by WorMzy on 2011-04-10
Does it give you an error?

You can probably change your theme by going to System -> Preferences -> Appearance, and that'll probably change the window decorations. As for the dock, you can probably disable that from the startup applications list by going to System -> Preferences -> Startup Applications.

I've never used the script myself, but I doubt it does much more than that.

---

### Post by d3v1150m471c on 2011-04-10
+1, you'll probably have to manually remove everything. I'd take a look at the script myself but i'm not downloading 40mb's of stuff i won't use because i'm on limited bandwidth. Like wormzy said, you have to remove the dock manually and possibly from startup, and i have a good feeling everything else is removable and/or changeable from:
```

gnome-appearance-properties

```

You should probably report this to whomever wrote the macbuntu packages as they're software is not removing itself as it said it should.

---

### Post by Timmer1240 on 2011-04-10
probably have right click the folder containing the uninstall.sh in a terminal and enter this command sudo ./uninstall.sh it will prompt for your password and should run then

---

### Post by Timmer1240 on 2011-04-10
right click the folder and select open in a terminal I meant

---

