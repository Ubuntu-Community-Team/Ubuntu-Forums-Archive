---
title: "Applying &quot;.patch&quot; file to directory"
date: 2011-09-05
forum: General Help
---

### Post by IQAndreas on 2011-09-05
Despite searching laboreously on Google, I am unable to find what I am looking for there.

I have a file named "minecraft.patch" that has contents as follows (just the first few lines are shown):
```
diff -u -r --strip-trailing-cr ../src_base/minecraft/net/minecraft/src/Block.java ../src_work/minecraft/net/minecraft/src/Block.java
--- ../src_base/minecraft/net/minecraft/src/Block.java	2011-08-27 13:36:14.084021000 +0200
+++ ../src_work/minecraft/net/minecraft/src/Block.java	2011-08-27 13:38:17.237064900 +0200
@@ -3,6 +3,7 @@
 // Decompiler options: packimports(3) braces deadcode 
 
 package net.minecraft.src;
+import net.minecraft.src.forge.ForgeHooks;
 
 import java.util.ArrayList;
 import java.util.Random;
@@ -276,19 +277,12 @@
         return blockID;
     }
 
+    /* FORGE: This function isn't called by Minecraft anymore.  Use
+     * blockStrength(EntityPlayer,int) instead.
+     */
     public float blockStrength(EntityPlayer entityplayer)
     {
-        if(blockHardness < 0.0F)
-        {
-            return 0.0F;
-        }
-        if(!entityplayer.canHarvestBlock(this))
-        {
-            return 1.0F / blockHardness / 100F;
-        } else
-        {
-            return entityplayer.getCurrentPlayerStrVsBlock(this) / blockHardness / 30F;
-        }
+	return blockStrength(entityplayer,0);
     }
```

Is there any way to apply those changes to a specific directory?

Either command line or GUI are fine with me.

---

### Post by Lampi on 2011-09-05
nope - what patch can do is strip parts of the full path - in your case ../src_base/minecraft/net/minecraft/src/

this id done by the -p X option (X defines how many sublevels patch should cut from the path)

usually you should play with the dry-run option until everything fits, then you can remove the dry-run, so the patch gets applied:

```
patch --dry-run -p X -i ../minecraft.patch
```

once it's okay you apply the patch (b backups the original file):

```
patch -b -p X -i ../minecraft.patch
```

---

### Post by IQAndreas on 2011-09-05
Thank you for the prompt reply.

I have changed "X" to to, so now it searches in "minecraft/net/minecraft/src" and "minecraft_server/net/minecraft/src", correct?

The ".patch" file is located in the same directory as the folders "minecraft" and "minecraft_server", and the command prompt's current directory is that folder. Am I doing everything correctly so far?


However, when I run the commands, I get the following output (it's several pages of "Hunk failed" and has therefore been trimmed)
```
patching file minecraft/net/minecraft/src/Block.java
Hunk #1 FAILED at 3.
Hunk #2 FAILED at 276.
Hunk #3 FAILED at 600.
3 out of 3 hunks FAILED -- saving rejects to file minecraft/net/minecraft/src/Block.java.rej
patching file minecraft/net/minecraft/src/BlockButton.java
Hunk #1 FAILED at 41.
Hunk #2 FAILED at 78.
// etc...
```

Am I doing something wrong, or is there a problem with the patch file?

---

### Post by Lampi on 2011-09-05
can't tell from what you gave me here - it can be both (wrong patch -p parameter or the patch is not a fit for your source)

---

