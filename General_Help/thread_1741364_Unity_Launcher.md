---
title: "Unity Launcher"
date: 2011-04-28
forum: General Help
---

### Post by ZachGretzinger on 2011-04-28
Can you change a SINGULAR icon in the Unity Launcher in Natty? I don't want to change the whole icon theme, just one SINGLE icon... To be more specific, I'm trying to change my Minecraft icon. I've tried a couple of different ways:
 
1) Changing the icon by right clicking on "minecraft.jar" and navigating to "Properties"
2) Creating a launcher to "minecraft.jar" with the icon set to the one I prefer
3) Extracting the "minecraft.jar" and finding the icon within and switching it out with the one I want (wouldn't compile afterwords)

Is there any other way to do this? I'm kind of anal about how my UI looks and this is driving me crazy. I'm at war with my own computer!

I know there is a way... This *is* Linux we're talking about afterall. I even poked around in /usr/share/unity and /usr/share/unity2d for answers. Needless to say - I found nothing. 

My current overall icon theme is Humanity. Once I get this darn Minecraft icon issue sorted out I'm going to merge in Faenza. 

Any ideas?

---

### Post by kerry_s on 2011-04-28
look in your applications for "main menu", there you can create or change.

---

### Post by ZachGretzinger on 2011-04-28
> **kerry_s said:**
> look in your applications for "main menu", there you can create or change.

That allows me to change the main menu, not the Unity Launcher. I'm trying the change the Unity Launcher. (The little sidebar to the left of the screen)

---

### Post by mc4man on 2011-04-28
Typically to set a new icon for an app in the launcher one would open the .desktop for that app and edit the Icon= line (path to new suitable icon
In the case of minecraft  - does it have a .desktop? 
If not then  you haven't mentioned what icon minecraft is currently using, if an actual  one then where is the location of?

---

### Post by coffeecat on 2011-04-28
There is a workaround for what you want by making a new launcher on the desktop first. You do this the same way as in previous releases by right-clicking on the desktop and choosing "Create Launcher". Fill in the Name, Command and Comment fields. The icon field will probably have picked up the Minecraft one automatically, but click on that and navigate to where your custom icon is and "Open" that. OK the launcher and test it while it is still on the desktop. Now simply drag it to the dock and you will get a new launcher for Minecraft with your own icon.

You can now remove the old one by right-clicking on it and unticking "Keep in launcher".

---

### Post by ZachGretzinger on 2011-04-28
> **mc4man said:**
> Typically to set a new icon for an app in the launcher one would open the .desktop for that app and edit the Icon= line (path to new suitable icon
In the case of minecraft  - does it have a .desktop? 
If not then  you haven't mentioned what icon minecraft is currently using, if an actual  one then where is the location of?

The one Minecraft is currently using resides within the minecraft.jar. I can view it when I extract it

---

### Post by ZachGretzinger on 2011-04-28
> **coffeecat said:**
> There is a workaround for what you want by making a new launcher on the desktop first. You do this the same way as in previous releases by right-clicking on the desktop and choosing "Create Launcher". Fill in the Name, Command and Comment fields. The icon field will probably have picked up the Minecraft one automatically, but click on that and navigate to where your custom icon is and "Open" that. OK the launcher and test it while it is still on the desktop. Now simply drag it to the dock and you will get a new launcher for Minecraft with your own icon.

You can now remove the old one by right-clicking on it and unticking "Keep in launcher".

Didn't work

---

### Post by ninjaaron on 2011-04-28
Remove the launcher from the dock
change the icon in "Main Menu"
logout
login
drag the launcher into the dock
boom

---

### Post by coffeecat on 2011-04-28
> **ZachGretzinger said:**
> Didn't work

You must have done something wrong. It works for me.

---

### Post by ZachGretzinger on 2011-04-28
> **coffeecat said:**
> You must have done something wrong. It works for me.

Hmm... Did you try it with a .jar application?

I think I identified the problem here:

Through extensive Google research I was able to find that .jar applications are not compatible with system icons. This is because, as I mentioned earlier, they contain icons within themselves. 

I did try to replace the icon contained in the .jar with the one I wanted but after doing so the .jar would no longer execute. I got an error message regarding "magic number" or something.

So yeah, I think the problem is simply because .jar files cannot use system icons. The reason the launcher work-around did not work is because it was trying to launch a .jar. 

Darn.

---

### Post by coffeecat on 2011-04-29
Sorry to hear that. That's frustrating.

I wonder if the "magic number" is to do with the icon type you tried to use. Perhaps the jar file didn't like the type you used. Magic numbers usually refer to the metadata stored in the file header describing the file type. 

[http://en.wikipedia.org/wiki/List_of_file_signatures](http://en.wikipedia.org/wiki/List_of_file_signatures)

At the moment I can't remember how to get at the metadata - it's a simple terminal command - but if I do I'll post back.

---

### Post by ZachGretzinger on 2011-04-29
> **coffeecat said:**
> Sorry to hear that. That's frustrating.

I wonder if the "magic number" is to do with the icon type you tried to use. Perhaps the jar file didn't like the type you used. Magic numbers usually refer to the metadata stored in the file header describing the file type. 

[http://en.wikipedia.org/wiki/List_of_file_signatures](http://en.wikipedia.org/wiki/List_of_file_signatures)

At the moment I can't remember how to get at the metadata - it's a simple terminal command - but if I do I'll post back.


I don't think it has to do with the icon... I made the icon an .svg just like the one that was already there and gave it the same name... Maybe I should resize it?

---

### Post by coffeecat on 2011-04-29
Sorry - I'm out of my depth. But one suggestion. Perhaps someone familiar with java programming would be able to help you, since this is a jar file refusing to execute. You might need to start a new thread if no one joins this one, perhaps in the programming section. It would be best to quote the exact magic number error message.

Good luck with that.

---

### Post by Trexla on 2011-05-07
Hey :smile:
Another way which was suggested earlier (making a custom launcher) can be effective, here's how i did it:

1. Put the minecraft.jar into my home directory (/home/jake)

2. On the desktop, i right clicked and created launcher, changed the icon to the one i wanted, and called it minecraft.

3. In the command area, i didn't point it to the minecraft.jar file, i put this in -  

```
java -Xmx1024M -Xms512M -cp /home/**jake**/minecraft.jar net.minecraft.LauncherFrame
```(REMEMBER: to change my username to your's - in bold)

4. I then cut this launcher to my home directory (/home/jake/) to get it out of the way.

5. I then simply dragged this onto my Unity shortcut bar and VOLIA, i have a custom icon on there :smile:

Hope this helps anyone searching for a solution/workaround.

Heres a screenshot of what mine looks like :smile: [http://i55.tinypic.com/2mebyid.png](http://i55.tinypic.com/2mebyid.png)

Trexla.

---

