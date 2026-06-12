---
title: "Unity User Interface"
date: 2011-12-25
forum: General Help
---

### Post by 01001101 on 2011-12-25
I've just upgraded to Ubuntu 11.10. I've been holding onto the classic gnome for a while, but I hate the classic gnome that comes with gnome 3. So, I'm now forced to switch to Unity and have a few problems making everything on my desktop as easy to access as possible.

1. In the gnome2 classic gnome, I was able to right click on the panel and add things to it. One of my favourite things to add was a system monitor app that would tell me information about RAM, processor, hard-disk, and network usage. I know that I could just open the system monitor, but I'd like to have something just on the toolbar that I can glance up at.

2. I want to put a tile on the Unity Launcher that is a link to my Downloads and my Documents folder. I'm able to drag and drop applications in, but I can't do the same with folders. I've seen the option where when you right click on the home folder, it shows the list of the other folders, and I'd rather just have a tile. Is there any way to do this.

3. I would like the link Blender as one of the tiles on the Unity launcher. But, since the version of Blender I use isn't exactly an installed application, I can't drag it into the launcher. In the classic gnome I was able to add a custom launcher by right clicking on the panel. How do I do it here?

4. Is there any way that you can set a shortcut key that will hide and show the Unity Launcher. I've made it so that it shows all the time because I hate it when GUI elements autohide, but there are times that I want to just hide it myself.

---

### Post by kaytalyst on 2011-12-25
I've also just installed 11.10 I haven't tested all of the things listed yet but I did come across this article which has solutions to #1 &2

[http://www.ubuntuvibes.com/2011/10/things-you-should-do-after-installing.html](http://www.ubuntuvibes.com/2011/10/things-you-should-do-after-installing.html)

Hope it helps a bit.

---

### Post by wildmanne39 on 2011-12-25
Hi, the super key also known as the windows key will show the launcher then just let go of it and it will close.

But I am do not think you can set a key that will make it close.
Thanks

---

### Post by mc4man on 2011-12-25
> **01001101 said:**
> 
4. Is there any way that you can set a shortcut key that will hide and show the Unity Launcher. I've made it so that it shows all the time because I hate it when GUI elements autohide, but there are times that I want to just hide it myself.

Pretty simple, I set up as a toogle switch thru a .desktop, usually accessed thru a quicklist entry though can be a desktop or launcher icon.

Same idea for keyboard, instead of creating a .desktop you'd create a keyboard binding with a command to a small script.

Easiest way is to use a ~/bin, once added,  after a restart will be in your path, so the 'command' is simply just the scriptname.

```
mkdir -p ~/bin && gedit ~/bin/toggle1 &
```

Copy & paste this in, save & close gedit

```
#!/bin/bash
key_value=$(gconftool --get /apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode)
echo $key_value | grep "0"
if [[ $? -eq 0 ]] ; then
gconftool --type Integer --set /apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode 1
else
gconftool --type Integer --set /apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode 0
fi
```

Then in terminal make executable, 
```
chmod u+x ~/bin/toggle1
```

If ~/bin was newly created then restart to add to path, then just create a keyboard binding in System Settings > Keyboard > Custom Shortcuts using toggle1 as the command
Screen shows

This toggles between hide-mode 1 "Autohide" & hide-mode 0 "Never"    
(I use 2 (dodge) & 0  here

---

