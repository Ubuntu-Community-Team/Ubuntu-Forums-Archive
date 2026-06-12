---
title: "Uh, no gui after compiz settings manager"
date: 2011-04-28
forum: General Help
---

### Post by JigglyWiggly_ on 2011-04-28
Ok, so I ugpraded to Ubuntu 11.04
I then launched compiz settings manager, enabled desktop cube. GUI froze, rebooted pc from a different desktop session.

Then on reboot there is no GUI, I just see my background and that's it.

What should I do?

---

### Post by JigglyWiggly_ on 2011-04-28
Ok I fixed it, I am not sure what fixed it...
But here are a few things I did

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

also reinstalled nautilus with the purge option

#rm-rf ubuntu-desktop

then reinstall ubuntu-desktop

Works now, I lost my old desktop settings but who gives a **** about that eh?

---

### Post by garvinrick4 on 2011-04-28
Do not use cube in the Unity interface.

---

### Post by Krytarik on 2011-04-28
See here on how to use "Desktop Cube" instead of "Desktop Wall":
[http://ubuntuforums.org/showthread.php?p=10734118#post10734118](http://ubuntuforums.org/showthread.php?p=10734118#post10734118)

Greetings.

---

### Post by garvinrick4 on 2011-04-29
> See here on how to use "Desktop Cube" instead of "Desktop Wall":
[http://ubuntuforums.org/showthread.p...8#post10734118]("http://ubuntuforums.org/showthread.php?p=10734118#post10734118")
Nice link:
*Mc4man does come up with some good post's in these Ubuntu forums.

---

### Post by ubontik on 2011-04-29
I have the same problem with 11.04. Could you please explain in details how you fixed it. I do not want to reinstall everything.
Thank you

---

### Post by uShafee on 2011-04-29
> **mc4man said:**
> When you tried to change from wall to cube/rotate  you likely unset all the plugins inc. the unityshell one (several  plugins will do this when enabling or disabling

Before anything else gets to messed up. while in Classic(no effects),  open a terminal and run these _2  separate_ commands
```
gconftool --recursive-unset /apps/compiz-1
gconftool --recursive-unset /apps/compizconfig-1

```Then log out and back into the Ubuntu (unity) login - should be back to the defaults


this should work. also note that before you can run those commands, you will have to restart and / or log in with another ubuntu session set to ubuntu (classic no effects).

---

### Post by Krytarik on 2011-04-29
> **ubontik said:**
> I have the same problem with 11.04. Could you please explain in details how you fixed it. I do not want to reinstall everything.
Thank you
Another way, besides those *uShafee* is referring to, is imo to follow the instructions of the post I linked to, but also add "unityshell" to the respective key. Of course, you need to do this from within "Ubuntu Classic" or "Ubuntu Classic (No effects)", since you may not be able to somehow run 'gconf-editor' in Unity until fixed. Although you may try to create a launcher for it at the desktop.

---

### Post by ubontik on 2011-04-29
[uShafee]("http://ubuntuforums.org/member.php?u=1026707")

I ran those commands, and not too much help. After rebooting everything the same - no GUI. How can I switch to Classic if no GUI?

I ran gconf-editor in terminal and got (gconf-editor:2541) CRITICAL **: Failed to parse arguments: Cannot open display:

---

### Post by ubontik on 2011-04-29
[Krytarik]("http://ubuntuforums.org/member.php?u=1187548")
OK I figured out how to switch to Classic mode. In the Ubuntu Software Center I've found the Unity 2D Panel, Places and Launcher.

Should I install all of them?

Under  /apps/compiz-1/general/screen0/options I do not have active_plugins; only hsize and vsize.

Thanks

---

### Post by Krytarik on 2011-04-29
> **ubontik said:**
> [uShafee]("http://ubuntuforums.org/member.php?u=1026707")

I ran those commands, and not too much help. After rebooting everything the same - no GUI. How can I switch to Classic if no GUI?

I ran gconf-editor in terminal and got (gconf-editor:2541) CRITICAL **: Failed to parse arguments: Cannot open display:
I don't know why the commands *uShafee* was referring to didn't work, if you ran them within your account and *not* with 'sudo' or such.

But if you want to run "gconf-editor", you need to do so from a terminal within your desktop, *not* a console (Ctrl+Alt+F*). To do so, create a launcher at your desktop with the command "gnome-terminal", or even more direct "gconf-editor" itself.

---

### Post by Krytarik on 2011-04-29
> **ubontik said:**
> [Krytarik]("http://ubuntuforums.org/member.php?u=1187548")
OK I figured out how to switch to Classic mode. In the Ubuntu Software Center I've found the Unity 2D Panel, Places and Launcher.

Should I install all of them?
You can do so if you want a fallback alternative with the style of Unity, but you should install the package "unity-2d" instead, those pulls the others as dependencies:
```
sudo apt-get install unity-2d
```> **ubontik said:**
> 
Under  /apps/compiz-1/general/screen0/options I do not have active_plugins; only hsize and vsize.

How about this path then?:
"/apps/compizconfig-1/profiles/unity/general/screen0/options"

---

### Post by ubontik on 2011-04-29
[B][Krytarik]("http://ubuntuforums.org/member.php?u=1187548")

[/B]Thank you for your help**.** For now I'll work in Classic mode. I decided to postpone with 3d desktop. I'll wait until the version will be more stable.

---

