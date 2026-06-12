---
title: "Move Link to Launcher/Sidebar"
date: 2012-06-24
forum: General Help
---

### Post by danieldiazdon on 2012-06-24
I recently created a link to a specific folder in my 'Home' and I currently have it on my desktop. However, it would be more convenient to have it in the launcher/sidebar so that I can easily access it without having to look at the desktop since the launcher is ALWAYS visible. I tried what was obvious which was to drank the link to the launcher/sidebar, however it did nothing. Thanks. Oh, and Im running Ubuntu 12.04

---

### Post by efflandt on 2012-06-25
You can add launchers to the Unity bar, but not sure if you can link a folder.

But what you can do is open the file manager, open the folder you want to find easily, and then in top menu bar select Bookmarks > Add Bookmark.  The folder you added should end up in the left panel of the file manager.  That works even for hidden files beginning with a dot, so you do not have to hit Ctrl+H to find bookmarked folders.

---

### Post by zombifier25 on 2012-06-25
You can create a custom launcher for ta specific folder. Create a new file named whatever.desktop and put this in it (based on Nautilus's own launcher):
```

#!/usr/bin/env xdg-open
[Desktop Entry]
Name=**Put the name you want to show here** 
Comment=**Comment here (though I'm not sure what does this do)**
Exec=nautilus **/link/to/folder**
Icon=folder
Terminal=false
StartupNotify=true
Type=Application
OnlyShowIn=GNOME;Unity;
Categories=GNOME;GTK;Core;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=3.0.0
X-Ubuntu-Gettext-Domain=nautilus
Actions=Window;

```
When you're done, drag and drop the created file into the Launcher.

---

### Post by danieldiazdon on 2012-06-25
Thanks a million guys. Both, work well :D

---

### Post by Derxst on 2012-06-25
I was looking for this ability, too! Thanks for the solutions!

---

### Post by danieldiazdon on 2012-06-30
Okay, so I now know how to add a folder link to the launcher. However How would I add a link to an actual file to the launcher. For instance, Im using an 'SH' file to Run Minecraft (a game). From here, I created a link to the 'SH' file, now the next step would be to add the link to the 'SH' file to the launcher. How can this be done? Thanks :D

---

### Post by MG&amp;TL on 2012-06-30
> **danieldiazdon said:**
> Okay, so I now know how to add a folder link to the launcher. However How would I add a link to an actual file to the launcher. For instance, Im using an 'SH' file to Run Minecraft (a game). From here, I created a link to the 'SH' file, now the next step would be to add the link to the 'SH' file to the launcher. How can this be done? Thanks :D

You don't want to open the file, you want to execute it. Put this in the file:

```
#!/usr/bin/env xdg-open
[Desktop Entry]
Name=Minecraft 
Comment=Play an addictive, cube-based game.
Exec=bash /link/to/sh
Icon=folder
Terminal=false
StartupNotify=true
Type=Application

```

However, if you actually want to open a file with the default program, put this in the file:

```
#!/usr/bin/env xdg-open
[Desktop Entry]
Name=Put the name you want to show here 
Comment=My wonderful file
Exec=xdg-open /link/to/path
Icon=file
Terminal=false
StartupNotify=true
Type=Application

```

---

### Post by danieldiazdon on 2012-06-30
I got a little confused with the last post on what I had to do. Im gonna explain in detail what im trying to do so that you guys can help me step by step. Here are the files: 
[IMG]http://s7.postimage.org/9qvncy08r/Screenshot_from_2012_06_30_14_33_06.png[/IMG]

They are both the same. The one on the left is the initial SH file to run the Minecraft.jar, and the one on the right is a link of the SH file on the left. I want to put the file on the left (the link of the SH file) into the launcher so that I press it and then the Minecraft.jar will execute. 

The code you guys have provided me has confused me because I am not sure what to do with it. Here is an image of the code inside the SH file: 
[IMG]http://s16.postimage.org/7mdxlhecl/Screenshot_from_2012_06_30_14_33_27.png[/IMG]

I include this picture just in case I need to insert whatever code you guys provide me in here. Once again, the code above is the one of the actual SH file. If I need to add any code to it, please explain where to (Above, below, etc.) Thanks Guys. YOU HAVE NO IDEA HOW MUCH I APPRECIATE THIS UBUNTU COMMUNITY :D

---

### Post by MG&amp;TL on 2012-06-30
As before, with zombifier's example, simply call it "whatever.desktop", i.e. "minecraft.desktop" and drag it into the launcher.

---

### Post by MG&amp;TL on 2012-06-30
> **danieldiazdon said:**
> I got a little confused with the last post on what I had to do. [...]

Okay, keep Minecraft.sh where it is, and put this in the .desktop:


```
#!/usr/bin/env xdg-open 
[Desktop Entry] 
Name=Minecraft  
Comment=Play an addictive, cube-based game. 
Exec=bash /home/daniel/Desktop/Minecraft.sh 
Icon=folder 
Terminal=false 
StartupNotify=true 
Type=Application
```

...replacing 'daniel' with the output of this command:

```
echo $USER
```

---

### Post by danieldiazdon on 2012-06-30
Here is what it looks like. I did exactly as you said. However when I press the launcher icon, all it does is blink a few times and then stops. Not working. 
Once again, thanks for the quick responses :grin:
[IMG]http://s18.postimage.org/svmfsntdl/Screenshot_from_2012_06_30_14_50_19.png[/IMG]

---

### Post by MG&amp;TL on 2012-06-30
> **danieldiazdon said:**
> Here is what it looks like. I did exactly as you said. However when I press the launcher icon, all it does is blink a few times and then stops. Not working. 
Once again, thanks for the quick responses :grin:


Okay, can you post what's in the .desktop file? And can you make sure the .sh file works?

---

### Post by danieldiazdon on 2012-06-30
I just made sure the .sh file works. I double clicked it and was prompted with: "Run in Terminal, Display,  Cancel, and Run" Once I ran it in the terminal, it worked just as its supposed to. It launched the Minecraft.jar. 

Here is whats inside the .desktop file:
#!/usr/bin/env xdg-open 
[Desktop Entry] 
Name=Minecraft  
Comment=Play an addictive, cube-based game. 
Exec=bash /home/daniel/Desktop/Minecraft.sh 
Icon=folder 
Terminal=false 
StartupNotify=true 
Type=Application

---

### Post by MG&amp;TL on 2012-06-30
Okay, what's the output of:

```
echo $USER
```

in a terminal?

---

### Post by danieldiazdon on 2012-06-30
daniel

---

### Post by MG&amp;TL on 2012-06-30
Okay, let's test the .sh file properly:

Output of:

```
bash ~/Desktop/Minecraft.sh
```
please.

I'm not a bash scripter, but that script looks...odd.

---

### Post by danieldiazdon on 2012-06-30
[IMG]http://s18.postimage.org/5mnrufiih/Screenshot_from_2012_06_30_15_26_12.png[/IMG]

That is what it returned. Like I said, the SH file works. I mean I suppose it does what its supposed to. Im using it to allocate more RAM to the Minecraft.jar to avoid lagging and make the game run more smoothly.

---

### Post by MG&amp;TL on 2012-06-30
> **danieldiazdon said:**
> 

That is what it returned. Like I said, the SH file works. I mean I suppose it does what its supposed to. Im using it to allocate more RAM to the Minecraft.jar to avoid lagging and make the game run more smoothly.

You can you just copy-paste output in CODE tags, y'know. :)

Well, evidently, the sh file is not working. EOF isn't a command, and the relative paths are a no-go. Put this in it:

```

#!/bin/sh
BINDIR=/home/daniel/.minecraft
java -Xmx2048M -Xms1024M -jar /home/daniel/Desktop/Minecraft.jar

```

---

### Post by danieldiazdon on 2012-06-30
I changed the code of the SH file like you said, added the link to the launcher and it WORKED! :D Thank god, youve been great! One last question, before I label this as solved. How can I change the icon of the Launcher Link so that it isnt a "question mark" Thanks:KS

---

### Post by MG&amp;TL on 2012-06-30
> **danieldiazdon said:**
> I changed the code of the SH file like you said, added the link to the launcher and it WORKED! :D Thank god, youve been great! One last question, before I label this as solved. How can I change the icon of the Launcher Link so that it isnt a "question mark" Thanks:KS

Not a problem. :)

It depends on what you want your launcher icon to be. For instance, if you wanted thunderbird's icon, you'd set

```

Icon=thunderbird
```

...although obviously you don't want that.

---

### Post by danieldiazdon on 2012-06-30
Would it be possible to put the icon as PNG 256x256 file that I have? If so then how? Like I said, as of right now its just a "?".

---

### Post by MG&amp;TL on 2012-06-30
> **danieldiazdon said:**
> Would it be possible to put the icon as PNG 256x256 file that I have? If so then how? Like I said, as of right now its just a "?".

Er, yeah, I think so. Just set the icon field to the path to the icon, like so:

```

Icon=/home/daniel/Pictures/minecraft.png
```

---

### Post by danieldiazdon on 2012-06-30
WORKED PERFECTLY with the icon and everything. Once again, thanks again for all your help! I really appreciate it. This is why UBUNTU has the best community.

---

### Post by MG&amp;TL on 2012-06-30
> **danieldiazdon said:**
> WORKED PERFECTLY with the icon and everything. Once again, thanks again for all your help! I really appreciate it. This is why UBUNTU has the best community.

Not a problem. Enjoy your cube-based entertainment. :)

---

