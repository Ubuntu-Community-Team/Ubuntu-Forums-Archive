---
title: "Java launches Wine"
date: 2011-04-08
forum: General Help
---

### Post by mito551 on 2011-04-08
I've just installed Ubuntu Studio 10.10 (coming from Ubuntu 10.10) and instaleed wine, then java etc... now, i'm trying to launch jar file (minecraft), it launches wine and with wine launches java! and java doesnt work in wine (and, for now, i dont really want it to). so, how can i launch java "using linux", not wine?
and if i use
```
java -jar
```it shows me such message
```
Exception in thread "main" java.awt.HeadlessException
    at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:173)
    at java.awt.Window.<init>(Window.java:437)
    at java.awt.Frame.<init>(Frame.java:419)
    at net.minecraft.LauncherFrame.<init>(LauncherFrame.java:27)
    at net.minecraft.LauncherFrame.main(LauncherFrame.java:158)
    at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:13)
```

UPD: Managed to prevent system from using wine, just deleted java from wine (didnt know it was there (^_^")7)

---

