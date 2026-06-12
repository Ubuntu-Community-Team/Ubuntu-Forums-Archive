---
title: "Minecraft and Ubuntu"
date: 2011-11-12
forum: General Help
---

### Post by PrivateAlpha on 2011-11-12
I cant seem to get minecraft working. I've installed openjdk and even tried to install the sun version although I think I didnt do it right.

But does anyone have any suggustions?

---

### Post by efflandt on 2011-11-12
I had trouble running it at first until I tried the suggested command line.  However, there is a minor typo because that shows **M**inecraft.jar when the actual downloaded file is minecraft.jar (proper upper/lower case is important in Linux). This script works fine with default java (icedtea) to launch minecraft 1.8.1 or 1.9PR5 in 64-bit Maverick (10.10) and 11.10 even when I forgot the #!/bin/sh in 11.10:

```
#!/bin/sh
# Change cd line to your path to orig minecraft.jar, NOT ~/.minecraft/bin
cd ~/Downloads
java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
```Note: 1.9 prerelease jar files do not have a launcher. So for those you need to:

[LIST=1]
[*]Run 1.8 minecraft.jar first and login (no need to create a world), then close it.
[*]Temporarily rename **original** minecraft.jar to something like minecraft-18.jar if still in your Downloads dir before downloading 1.9PR5 minecraft.jar.
[*]Rename minecraft.jar in **~/.minecraft/bin** to something else like minecraft-18.jar (you may need it to upgrade when 1.9 is actually released).
[*]Put the 1.9PR5 minecraft. jar in **~/.minecraft/bin**
[*]If both downloaded jar files are still in Downloads, rename them so 1.9PR5 is minecraft-195.jar, and minecraft-18.jar is minecraft.jar
[*]Then launch **original** downloaded 1.8 minecraft.jar, which will still show 1.8 during login, but should show 1.9 Prerelease 5 after login.
[/LIST]
 PS: For scripts, create a **bin** folder in your user's $HOME directory.  Log out of X and back in, which will automatically add your bin to your $PATH. Then create the script in your bin folder and make sure that you give it **execute** permission (besides read/write for you). ~ = $HOME = /home/<your-username>

I was able to login to minecraft in Lucid (10.04), but that computer is an old early Athlon64 3200+ with legacy ATI X1300 video and minecraft crashed at some point after that.

---

