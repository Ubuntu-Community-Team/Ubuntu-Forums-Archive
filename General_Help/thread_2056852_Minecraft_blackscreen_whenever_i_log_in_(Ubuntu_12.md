---
title: "Minecraft blackscreen whenever i log in (Ubuntu 12.04)"
date: 2012-09-12
forum: General Help
---

### Post by jmmeis13 on 2012-09-12
Hello!
I am an almost noob at ubuntu. I have done all of the setup stuff, and have started using ubuntu somewhat frequently for my internet needs, but i have a problem.
 Whenever i want to play any of my games, i boot into my windows 7 (i got dual install, so i now have the choice between win 7 (and for some reason also win vista) and ubuntu, when i boot up my computer), i want to change that.
 I am looking, at how to play my games at ubuntu, and im starting with Minecraft. I installed using a terminal program i found online ( i have also used the .jar from minecraft.net, same problem), i press the minecraft icon to launch, i type in my username and password, press login, and it goes blackscreen. I tried out launching from terminal using the code in the launcher, so that i can give you the bug code for help. Here it is.



janis@janis-HP-Pavilion-dv6700-Notebook-PC:~$ java -jar /home/janis/.minecraft/minecraft.jar
Xlib:  extension "RANDR" missing on display ":0".
asdf
Exception in thread "Thread-3" java.lang.UnsatisfiedLinkError: /home/janis/.minecraft/bin/natives/liblwjgl.so: /home/janis/.minecraft/bin/natives/liblwjgl.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary1(ClassLoader.java:1939)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1864)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1825)
    at java.lang.Runtime.load0(Runtime.java:792)
    at java.lang.System.load(System.java:1059)
    at org.lwjgl.Sys$1.run(Sys.java:69)
    at java.security.AccessController.doPrivileged(Native Method)
    at org.lwjgl.Sys.doLoadLibrary(Sys.java:65)
    at org.lwjgl.Sys.loadLibrary(Sys.java:81)
    at org.lwjgl.Sys.<clinit>(Sys.java:98)
    at net.minecraft.client.Minecraft.F(SourceFile:1857)
    at aof.<init>(SourceFile:20)
    at net.minecraft.client.Minecraft.<init>(SourceFile:77)
    at anw.<init>(SourceFile:36)
    at net.minecraft.client.MinecraftApplet.init(SourceFile:36)
    at net.minecraft.Launcher.replace(Launcher.java:136)
    at net.minecraft.Launcher$1.run(Launcher.java:79)



I have installed java, and i have installed nvidia driver using the driver update feature in the system settings (i have tried all of them, i curently have 
"NVIDIA accelerated graphics driver (post-release updates) (version current-updates)")
HOW DO I FIX THIS?
sorry, for misspellings and such, english is not my first language
         Thank you for your time and help,
                          Sincerely Janis

---

### Post by drmrgd on 2012-09-12
Based on the error, it looks like you have 32-bit java installed, and a 64-bit Minecraft installation.  You should double check that you've installed the 64-bit version of java and try again.

---

### Post by jmmeis13 on 2012-09-12
> **drmrgd said:**
> Based on the error, it looks like you have 32-bit java installed, and a 64-bit Minecraft installation.  You should double check that you've installed the 64-bit version of java and try again.
Im pretty sure i did, but how do i check?

---

### Post by drmrgd on 2012-09-12
Unfortunately, I don't have my linux box handy, and so I can't verify.  I think running:

```
java -version
```

might show you what you've got as the default.  

Another possibility (I'm not sure what the Minecraft installer you used is actually doing), is that the LWJGL files you have are the wrong architecture.  I'm not sure at all how to check those.  If the java version is correct, I'd try to just repatch the LWJGL files with the 64-bit version to be on the safe side.  I can't give you the link for those (firewall here won't permit me to look that up), but a quick Google search for something like "minecraft lwjgl update" or something like that should point you in the right direction.  It's a simple as replacing the 3 or 4 files you have now with new ones.  Pretty quick and painless!

---

### Post by Ubunterrific on 2012-09-12
I remember reading about this problem recently. The solution was to download the latest lwjgl from [http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.8.4/]("http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.8.4/")

and then you swap the old versions of the named files in **/home/username*/.minecraft*  **(it's a hidden folder, so hold ctrl and H in nautilus to show it) with those from the zip folder.

They seem to be in lwjgl-2.8.4/native/linux (in the zip folder)

There was a proper guide for this, i'll see if i can find it.

UPDATE: Yes, here it is [B][http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL](http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL)
[/B]LWJGL is the **L**ight**W**eight **J**ava **G**ame **L**ibrary. Essentially, it is what Minecraft uses for graphics, sound, and input and minecraft will not ship with the latest version of LWJGL.

---

### Post by jmmeis13 on 2012-09-12
OMG! Thank you so much!  just found the lwjgl files, and extracted them, as said in a tutorial, except in the natives folder i put the native linux files, AND NOW IT WORKS!
THANK YOU SO MUCH!

---

### Post by jmmeis13 on 2012-09-12
wait, it crashed when i joined a server

---

### Post by Ubunterrific on 2012-09-12
> **jmmeis13 said:**
> wait, it crashed when i joined a server

So close lol Which version of java did you find you're running?

I personally use java 7 from the webupd8 ppa and have no problems. If you'd like to try that?
```
sudo add-apt-repository ppa:webupd8team/java 
sudo apt-get update 
sudo apt-get install oracle-java7-installer
```

---

### Post by jmmeis13 on 2012-09-12
oh, wait. the problem is serverside, since my maps and other servers work.

THANKS FOR THE HELP!

---

### Post by Ubunterrific on 2012-09-12
> **jmmeis13 said:**
> oh, wait. the problem is serverside, since my maps and other servers work.

THANKS FOR THE HELP!

Woo! You're welcome :) Always nice to have things running smoothly.:popcorn:

---

### Post by drmrgd on 2012-09-12
Cool!  Glad that fixed it, and thank you Ubunterrific for providing the links to the LWGJL files since I couldn't look those up from this network.  I like easy fixes!

---

### Post by Ubunterrific on 2012-09-12
> **drmrgd said:**
> Cool!  Glad that fixed it, and thank you Ubunterrific for providing the links to the LWGJL files since I couldn't look those up from this network.  I like easy fixes!

As do i ;)  I'm just glad i read that tutorial a while back and so knew the fix.

---

