---
title: "No terminal transparency?"
date: 2012-05-26
forum: General Help
---

### Post by TechnicalMechanic on 2012-05-26
Just installed 12.04 after a long break from linux and did not enjoy unity, installed gnome and got rid of unity. 

Im not sure if that hand anything to do with it, but i cannot for the life of me get transparency to work correctly on terminal. I like to use transparency to see through the terminal window and type code that is on the window behind it, but when i change the transparency option, all i can see is the desktop background, not the window behind it.

Not sure if i explained it well enough, but here is a screen cap:

---

### Post by PhantomTurtle on 2012-05-26
The screen transparency will only work when desktop effects are enabled, or it will just give you fake transparency. It should work with Unity 3D, Gnome Shell and Gnome Classic with effects. Which desktop environment are you using?

---

### Post by Zvlwab on 2012-05-26
> **PhantomTurtle said:**
> The screen transparency will only work when desktop effects are enabled, or it will just give you fake transparency. It should work with Unity 3D, Gnome Shell and Gnome Classic with effects. Which desktop environment are you using?

I remember running a transparant terminal without having desktop effects enabled.

You may need to install a video card driver.

---

### Post by PhantomTurtle on 2012-05-26
> **Zvlwab said:**
> I remember running a transparant terminal without having desktop effects enabled.

You may need to install a video card driver.

I have tried this on Gnome Classic without effects and it didn't work but it did in Gnome-Classic with effects. Same with unity, it works in 3D but not 2D, so I just assumed it had to do with effects being enabled.

---

### Post by Frogs Hair on 2012-05-26
I Just checked classic and terminal transparency is working . Go into Edit > Profile Preference > Background and make sure use transparent background is checked and move the slider. I don't know why it isn't working if you have done that. To use custom colors disable theme color under color and add a custom color.

---

### Post by PhantomTurtle on 2012-05-26
> **Frogs Hair said:**
> I Just checked classic and terminal transparency is working . Go into Edit > Profile Preference > Background and make sure use transparent background is checked and move the slider. I don't know why it isn't working if you have done that. To use custom colors disable theme color under color and add a custom color.

Is that gnome-classic with effects or without? And can you see the windows behind the terminal or just the wallpaper?

---

### Post by TechnicalMechanic on 2012-05-30
> **PhantomTurtle said:**
> The screen transparency will only work when desktop effects are enabled, or it will just give you fake transparency. It should work with Unity 3D, Gnome Shell and Gnome Classic with effects. Which desktop environment are you using?

Is there a way to enable effects while logged in? I had the icon for it before i got rid of unity to switch from effects/noeffects

Edit: Found the effects/classic button. Now i realize why i switched to no effects. As soon as i logged on the windows were stuck in an unmovable position at the top left of screen. Right click and move didnt move them, and they were also missing the taskbar to exit, minimize or maximize. 

Get a "ubuntu 12.04 has experienced an internal error"

---

### Post by zombifier25 on 2012-05-30
Looks like your Compiz profile is messed up. Reset it:
```
gconftool --recursive-unset /apps/compiz-1
```

---

### Post by TechnicalMechanic on 2012-05-30
> **zombifier25 said:**
> Looks like your Compiz profile is messed up. Reset it:
```
gconftool --recursive-unset /apps/compiz-1
```

Why would that happen though? Also, ran that command and switched back to classic with effects. Still the same problem

[IMG]http://i.imgur.com/Z1orf.png[/IMG]

After logging back into no effects
[IMG]http://i.imgur.com/Ox8A7.png[/IMG]

---

### Post by Frogs Hair on 2012-05-30
> **PhantomTurtle said:**
> Is that gnome-classic with effects or without? And can you see the windows behind the terminal or just the wallpaper? I was logged into classic with effects and I can see whatever is behind the terminal.

---

### Post by PhantomTurtle on 2012-05-30
> **Frogs Hair said:**
> I was logged into classic with effects and I can see whatever is behind the terminal.

And that's why it works, because the effects are enabled.

To TechnicalMechanic, check the settings for the terminal now. Make sure that transparency is still enabled in gnome-classic with effects.

---

