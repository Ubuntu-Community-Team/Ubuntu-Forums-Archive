---
title: "questions about &quot;Unity&quot; in 11.04"
date: 2011-05-06
forum: General Help
---

### Post by gamblor01 on 2011-05-06
So I just installed 11.04 and I think the whole Unity thing adds a nice touch to the look and feel of stuff (previously I always installed Faenza icons, changed window themes, etc.).

I have a few questions however.  These are the things that are bothering me the most...


1. How do I add a freaking applet to the gnome panel at the top?  It seems to be locked and I previously wrote my own applet in Python (in 10.10) that I would like to be able to place up there.

2. Is there a way to prevent windows from always opening in full screen mode?  It would be nice if it remembered the window size used when the program was last closed (as gnome has always done).  I hate this auto-maximize behavior.

3. How can I add my own executables to the launcher?  For example, I installed Eclipse by downloading the tar.gz file from eclipse.org.  Now I would like to add a shortcut to the launcher and specify the path to the executable.  This was easy before -- just right-click the bar and hit "add custom launcher".  So far the only way I can see to add things is to search for them first in the new menu, launch them, and then click "Keep in launcher".  Well the new menu doesn't find eclipse if I search for it...so how do I add it to the launcher????

4. Can I change the behavior of the launcher so that it's always shown, or always hidden?  For example, maybe I don't want apps to be able to take up the entire screen and force the launcher to be hidden.  Is that possible?


I'll keep digging around (maybe in gconf-editor?) to see if I find some answers but if someone can point me directly to the answer that would be great.  Thanks!

---

### Post by elliotn on 2011-05-06
good questions

---

### Post by Megaptera on 2011-05-06
> **gamblor01 said:**
>  I have a few questions however.  These are the things that are bothering me the most...


1. How do I add a freaking applet to the gnome panel at the top?  It seems to be locked and I previously wrote my own applet in Python (in 10.10) that I would like to be able to place up there.

 someone can point me directly to the answer that would be great.  Thanks!

I'm not sure how easy it is but this guy found a way to customize the number of workspaces and rows used by the Unity ‘Workspace Switcher’, as well as switch between workspaces themselves directly from the panel. 

I know that's not what _you're_ looking to do but wondered if there's any info in there that could help you? 

Link [http://www.omgubuntu.co.uk/2011/05/quickly-adjust-the-number-of-workspaces-in-unity-with-indicator-workspaces/](http://www.omgubuntu.co.uk/2011/05/quickly-adjust-the-number-of-workspaces-in-unity-with-indicator-workspaces/)

---

### Post by gamblor01 on 2011-05-06
> **Megaptera said:**
> I'm not sure how easy it is but this guy found a way to customize the number of workspaces and rows used by the Unity &#8216;Workspace Switcher&#8217;, as well as switch between workspaces themselves directly from the panel. 

I know that's not what _you're_ looking to do but wondered if there's any info in there that could help you? 

Link [http://www.omgubuntu.co.uk/2011/05/quickly-adjust-the-number-of-workspaces-in-unity-with-indicator-workspaces/](http://www.omgubuntu.co.uk/2011/05/quickly-adjust-the-number-of-workspaces-in-unity-with-indicator-workspaces/)

Hmm...it's possible that might help me.  I suppose I could download it and then see how they actually get their applet to install.  If I could figure that out then I can probably push mine into the gnoem-panel manually.  It's also not called gnome-panel any longer.  Earlier today I removed the applets that I don't care about (like Evolution and Gwibber) and when I tried to execute "killall gnome-panel" it didn't know of any such process.  So everything is totally different and I'm not sure how to manage it yet.  :(

---

### Post by werewolves on 2011-05-06
> **gamblor01 said:**
> So I just installed 11.04 and I think the whole Unity thing adds a nice touch to the look and feel of stuff (previously I always installed Faenza icons, changed window themes, etc.).

I have a few questions however.  These are the things that are bothering me the most...


1. How do I add a freaking applet to the gnome panel at the top?  It seems to be locked and I previously wrote my own applet in Python (in 10.10) that I would like to be able to place up there.

2. Is there a way to prevent windows from always opening in full screen mode?  It would be nice if it remembered the window size used when the program was last closed (as gnome has always done).  I hate this auto-maximize behavior.

3. How can I add my own executables to the launcher?  For example, I installed Eclipse by downloading the tar.gz file from eclipse.org.  Now I would like to add a shortcut to the launcher and specify the path to the executable.  This was easy before -- just right-click the bar and hit "add custom launcher".  So far the only way I can see to add things is to search for them first in the new menu, launch them, and then click "Keep in launcher".  Well the new menu doesn't find eclipse if I search for it...so how do I add it to the launcher????

4. Can I change the behavior of the launcher so that it's always shown, or always hidden?  For example, maybe I don't want apps to be able to take up the entire screen and force the launcher to be hidden.  Is that possible?


I'll keep digging around (maybe in gconf-editor?) to see if I find some answers but if someone can point me directly to the answer that would be great.  Thanks!

Some of your questions are answered here:
[http://askubuntu.com/questions/29553/how-can-i-configure-unity](http://askubuntu.com/questions/29553/how-can-i-configure-unity)

And here:
[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)

As for number 3, I'm pretty sure you can create the launcher on the desktop and then drag it into the launcher.

---

### Post by gamblor01 on 2011-05-06
Cool thanks -- I'll check it out.  I have booted back up into 10.10 so that I could get to work for today.  Not only that, I accidentally hit something so that none of the windows show title bars any longer.  So I can't even drag windows around the screen...it's a real bummer.

I have also noticed some bugs where it doesn't properly recognize the mouse cursor (I have to move my mouse about 20 pixels BELOW where I actually want to click).  This is really buggy and very disappointing.  I'll reboot into 11.04 and try to fix some things, but thus far I'm not impressed at all.  I'm simply frustrated and disappointed.

---

