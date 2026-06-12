---
title: "Adding a JAR to the dock?"
date: 2012-08-21
forum: General Help
---

### Post by HoCo xXSamXx on 2012-08-21
So I play Minecraft, and it a an executable JAR file. I have it in my home/games folder, and a link to it on my desktop. How can I add a shortcut to my dock that when clicked will run it? Will I be able to set a custom icon?

Thanks!
HoCo

---

### Post by Zvlwab on 2012-08-21
You need to create a launcher to run the following command:
```
java -Xmx1024M -Xms512M -cp /path/to/minecraft.jar net.minecraft.LauncherFrame
```

---

### Post by HoCo xXSamXx on 2012-08-21
Great! Will that work for any executable JAR?

---

