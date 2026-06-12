---
title: "Minecraft 64 bit version error"
date: 2011-04-30
forum: General Help
---

### Post by konnorrigby on 2011-04-30
Ok first sorry if this is in the wrong place.



im getting an error in minecraft on ubuntu 11.04...

```

Exception in thread "Minecraft main thread" java.lang.LinkageError: Version mismatch: jar version is '18', native libary version is '17'
    at org.lwjgl.Sys.<clinit>(Sys.java:103)
    at org.lwjgl.opengl.Display.<clinit>(Display.java:132)
    at net.minecraft.client.Minecraft.a(SourceFile:224)
    at net.minecraft.client.Minecraft.run(SourceFile:658)
    at java.lang.Thread.run(Thread.java:662)

```


it says the jar version is wrong... ive updated java and minecraft so i dont exactly know what is...... HELP...

---

### Post by greybirds on 2011-05-01
It sounds like LWJGL's jars and libraries have somehow gotten out of sync. 

LWJGL is a Java-based game library Minecraft uses; half of it is written in Java and stored in jar files, and the other half is written in native code and stored in so files. Minecraft downloads and updates these on its own, so I don't know how it could have gotten different versions of the two halves, but there might be an easy fix.

If you can start Minecraft and get to the login screen, click the Options button and then click the Force Update button in the window that pops up. This should make Minecraft redownload the library files. **However**, if you've modded Minecraft it will wipe them out and you'll have to remod. 

If you can't start Minecraft at all, you can move the files in the .minecraft/bin folder and Minecraft might be able to start and redownload matching versions. Don't outright delete them but copy them into another folder.

If you're ok with using the terminal, start it and type the following, line by line:
```
cd
cd .minecraft
mv bin bin_backup
mkdir bin

```
The first line just makes sure you're in your home directory; the second moves into the .minecraft folder. The third backs up the files in bin by renaming the entire directory, and the fourth creates a new bin directory for Minecraft to look in. After this, Minecraft should realize it's missing LWJGL and redownload it.

If you prefer using Gnome do this instead:
```

1. Open your home folder
2. Select View -> Show Hidden Files
3. Locate the .minecraft folder and double-click it to open it.
4. Right-click the bin folder, select Rename from the popup menu, and rename it to something like bin_backup. 
5. Right-click an empty spot in the folder area of the window and select Create Folder from the menu; name it bin.
6. Select View -> Show Hidden Files again to get rid of all the extra junk in your home folder.

```

Hope this helps.

---

### Post by konnorrigby on 2011-05-01
Thank you for the reply but I seem to have fixed it.  I had to run as root I don't know why.

---

