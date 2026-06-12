---
title: "Runescape &amp; Minecraft"
date: 2012-04-23
forum: General Help
---

### Post by Novus Anima on 2012-04-23
Hello, I have just recently converted to the Ubuntu Linux 11.10 OS from Windows 7, so everything is rather different and I need some help figuring these two games out.

Runescape runs fine, but I really miss playing in the Software and OpenGL modes. Whenever I try to select them it says that I am unable to enter the selected mode. My friend who has been using Linux for quite some time (he uses Arch Linux) told me it's because I may have 'foss drivers' and that graphics implementation may be low. That would certainly explain why I am unable to enter the graphics modes, but I was wondering if there was any way to get the graphics implementation working.

Lastly, when I go to run Minecraft I am stuck at a black screen. Now I know my Java is up to date and functional because I spent 5 hours yesterday making sure it works fine, and I even get my Java version when I do the 'java -version' command in the Terminal. Not sure why I get this black screen, it may be because I have to wait longer than 5 minutes? But I still shouldn't have to wait that long to run Minecraft.

If anyone has any solutions, I am certainly all ears.

---

### Post by tmaranets on 2012-04-23
Have you tried using Minecraft in Wine?

---

### Post by 11jmb on 2012-04-23
For the graphics question, did you install any proprietary drivers?

---

### Post by 11jmb on 2012-04-23
> **tmaranets said:**
> Have you tried using Minecraft in Wine?

I think minecraft is 100% java, so it should run on ubuntu pretty easily

How are you trying to run it? You should be able to download the .jar, do a quick chmod, and run it

---

### Post by Novus Anima on 2012-04-23
> **tmaranets said:**
> Have you tried using Minecraft in Wine?

No, I have not. That's another issue I am having; my Wine installation from the Software Center keeps stalling because of some apt-get it is waiting for to exit.

> **11jmb said:**
> For the graphics question, did you install any proprietary drivers?

No, not yet. Not too sure where I can get drivers that are Linux compatible. Would I just download a Win7 driver and run it in Wine?

> **11jmb said:**
> I think minecraft is 100% java, so it should run on ubuntu pretty easily

How are you trying to run it? You should be able to download the .jar, do a quick chmod, and run it

I downloaded it, changed the properties to be able to be run as an executable, then ran it just fine. Maybe I need to chmod it. What chmod should I apply to the jar?

---

### Post by techsupport on 2012-04-23
Try using the script install method:

[http://debianhelp.wordpress.com/2011/10/16/how-to-install-minecraft-in-ubuntu/](http://debianhelp.wordpress.com/2011/10/16/how-to-install-minecraft-in-ubuntu/)

---

### Post by 11jmb on 2012-04-23
> **Novus Anima said:**
> 
No, not yet. Not too sure where I can get drivers that are Linux compatible. Would I just download a Win7 driver and run it in Wine?

No. #3 on the list below (I recommend at least 1 and 2 as well)
[http://blog.sudobits.com/2011/09/08/10-things-to-do-after-installing-ubuntu-11-10/](http://blog.sudobits.com/2011/09/08/10-things-to-do-after-installing-ubuntu-11-10/)

If this doesn't work, please let us know what graphics card your computer is using

> **Novus Anima said:**
> 
I downloaded it, changed the properties to be able to be run as an executable, then ran it just fine. Maybe I need to chmod it. What chmod should I apply to the jar?

If you gave permissions to run as an executable, that should be enough. What happens when you try to run the .jar file? Do you get an error message or something.

---

### Post by Novus Anima on 2012-04-23
So it seems that I had to remove the OpenJDK 7 Runtime that I had, it worked just fine afterwards. Thank you all for your help on the matter!

@11jmb,

I've done step 1 just fine, but step 2 is confusing me. How do I exit out of this agreement screen?

[IMG]http://i.imgur.com/82U8A.png[/IMG]

---

### Post by 11jmb on 2012-04-23
can you not just navigate with your arrow keys/enter?

---

### Post by Novus Anima on 2012-04-23
> **11jmb said:**
> can you not just navigate with your arrow keys/enter?

Not sure, I closed out of it because I had to do something. Now I am unable to even access the file because of some lock file/directory.

[IMG]http://i.imgur.com/tTaK5.png[/IMG]

---

### Post by 11jmb on 2012-04-23
are you running apt-get in another shell? or perhaps synaptic?

Edit: we've digressed a bit. Try installing the proprietary drivers, and come back to the restricted extras

---

### Post by Novus Anima on 2012-04-23
> **11jmb said:**
> are you running apt-get in another shell? or perhaps synaptic?

Edit: we've digressed a bit. Try installing the proprietary drivers, and come back to the restricted extras

After quite a few hours of trial and error I figured it out. Anyhow, sorry for the digression. Now, I go into Additional Drivers and no drivers even show up. I waited a few minutes to see if that was the case, but I see nothing.

---

### Post by techsupport on 2012-04-23
> **Novus Anima said:**
> After quite a few hours of trial and error I figured it out. Anyhow, sorry for the digression. Now, I go into Additional Drivers and no drivers even show up. I waited a few minutes to see if that was the case, but I see nothing.

You needed to hit the TAB key to select OK and then press ENTER key. The fonts were for Sun Java's Plugin. Maybe it will effect your game. If it does, just reinstall Sun Java again and make sure to hit the TAB key and Press Enter on that same screen you got stuck on.  Restart your system first if you have a lock happening.

When I posted that link you needed to really follow all of the instructions on there, not just install Java. Step by step.

:guitar:

---

### Post by 11jmb on 2012-04-24
> **Novus Anima said:**
> After quite a few hours of trial and error I figured it out. Anyhow, sorry for the digression. Now, I go into Additional Drivers and no drivers even show up. I waited a few minutes to see if that was the case, but I see nothing.

Well, if that's the case, then you have open-source drivers for all of your hardware. 

I'm not much of a gamer myself, so I don't know what the solution might be beyond driver updates, but a quick google turned this up:

[http://services.runescape.com/m=rswiki/en/Linux_Known_Issues#I_am_stuck_in_Safe_Mode_and_RuneScape_is_unable_to_change_Display_Modes](http://services.runescape.com/m=rswiki/en/Linux_Known_Issues#I_am_stuck_in_Safe_Mode_and_RuneScape_is_unable_to_change_Display_Modes)

Hope it helps!

---

### Post by ookooboontoo on 2012-09-03
did you get this to work in the end, I have successfully been using both minecraft and minecraft server and the Tekkit ones too on 12.04 with jdk6?
A

---

