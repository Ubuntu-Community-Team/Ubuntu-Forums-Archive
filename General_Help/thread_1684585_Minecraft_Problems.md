---
title: "Minecraft Problems"
date: 2011-02-09
forum: General Help
---

### Post by muddpup64 on 2011-02-09
I recently downloaded a Minecraft jar package (to play Minecraft of course), but  instead of the jar package that was supposed to be there, there are  these three files [ LZMA, META-INF, net ]. I have looked at possible  problems, but found nothing. How can I play Minecraft?

---

### Post by mmsmc on 2011-02-09
try downloading it from the site again, and this time 
be sure to follow each direction thouroghly

---

### Post by muddpup64 on 2011-02-09
I have already downloaded the file four times, trying to get it to work. But I have three files when I need only one.

---

### Post by theyain on 2011-02-09
Interesting, those are the folders that are contained inside the jar file.

To help, I've uploaded the minecraft.jar file inside of a tar.gz file.

---

### Post by SavageWolf on 2011-02-09
I think the default action for .jar files is to open them. The jar you are looking for is the actual file you downloaded, and you shouldn't decompress it.

---

### Post by muddpup64 on 2011-02-09
Now that I have the file what should I do with it?

I'm not sure I trust that web site anymore.

---

### Post by theyain on 2011-02-09
run this in a terminal

```
java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame
```

Also, make sure your minecraft.jar file is in your home folder.

---

### Post by SavageWolf on 2011-02-09
I have this script:
```

java -jar /opt/minecraft/Minecraft\.jar

```

And the file was downloaded to /opt/minecraft/Minecraft.jar

---

### Post by muddpup64 on 2011-02-09
It worked, thanks!

:guitar:

---

