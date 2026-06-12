---
title: "Icon size not getting decreased using CompizConfig setings manager"
date: 2012-03-12
forum: General Help
---

### Post by alwaysonnet on 2012-03-12
I'm running on 11.10 ubuntu now and downloaded CompizConfig settings manager. I'm trying to decrease the icon sizes in the launcher, but size is not getting decreased.

Pls find the screenshot. Any ideas on this. FYI, i made my launcher fixed on left side of my screen ( don't know how i've done, but executed some command found over internet)

---

### Post by ajgreeny on 2012-03-12
> **alwaysonnet said:**
> I'm running on 11.10 ubuntu now and downloaded CompizConfig settings manager. I'm trying to decrease the icon sizes in the launcher, but size is not getting decreased.

Pls find the screenshot. Any ideas on this. FYI, i made my launcher fixed on left side of my screen ( don't know how i've done, but executed some command found over internet)
You should be able to find the command that you've forgotten in the .bash_history file in your home.  Ctrl+H to see hidden files if it is not visible.

Are you running unity 3d or 2d?
I don't think the launcher icons can be resized if using unity 2d.  At least, I could never get it to work on my old system.

---

### Post by alwaysonnet on 2012-03-13
During the Login screen I see 5 options. 


[LIST=1]
[*]gnome
[*]gnome classic
[*]gnome (with no effects)
[*]Ubuntu
[*]Ubuntu 2D
[/LIST]
does Unity mean Ubuntu 2D?

---

### Post by ajgreeny on 2012-03-13
> **alwaysonnet said:**
> During the Login screen I see 5 options. 


[LIST=1]
[*]gnome
[*]gnome classic
[*]gnome (with no effects)
[*]Ubuntu
[*]Ubuntu 2D
[/LIST]
does Unity mean Ubuntu 2D?
I do not use unity nor have I updated from 10.04, but I think 4. Ubuntu is unity 3D and 5. Ubuntu 2D is unity 2D.

The problem may be that your hardware is not able to run unity 3D for whatever reason, eg no graphics driver installed, and the system then defaults to unity 2D, which looks basically then same, but acts differently in certain situations. I am not sure how you can tell which you have, 2D or 3D, but no doubt others can tell us.

---

### Post by stinkeye on 2012-03-13
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=11760889&postcount=8") for help to diagnose what session your in and if you 
can run compiz.

---

### Post by alwaysonnet on 2012-03-14
@Stinkeye: Yes, even when I login into Ubuntu session, echo'ing $DESKTOP_SESSION is showing as ubuntu-2d.

I ran the following command, and 'Unity 3d Supported' is showing as 'NO'

I also ran the commands mentioned by you in other post, but my launcher is never hiding. It always shows up in the right hand side of the screen.

---

### Post by stinkeye on 2012-03-14
You can't change the size of the unity-2d-launcher icons.
You can change the hide-mode to never
```
gsettings set com.canonical.Unity2d.Launcher hide-mode [COLOR="Red"]0[/COLOR]
```
> [COLOR="red"]0[/COLOR]: never hide; the launcher is always visible and windows won't overlap with it
        [COLOR="red"]1[/COLOR]: auto hide; the launcher will disappear after a short time if the user is not interacting with it
        [COLOR="red"]2[/COLOR]: intellihide; same as auto hide but the launcher will disappear if a window is placed on top of it

To set back to the default setting ([COLOR="Red"]2[/COLOR]) use
```
gsettings **reset** com.canonical.Unity2d.Launcher hide-mode
```


In the dash type in "additional drivers" to check for gfx drivers.

You can't run compiz without 3d gfx drivers so when you try to log in to the
"ubuntu" session you get dropped back to the "ubuntu-2d" session
Compiz is the window manager for the "ubuntu" session and unity 3d is a plugin for compiz.

Posting the output of this will help
```
sudo lshw -c video
```
Use the "#" button and paste between the code blocks
eg (CODE)*paste here*(/CODE)
[ATTACH]214278[/ATTACH]

---

