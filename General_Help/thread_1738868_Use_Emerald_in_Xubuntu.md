---
title: "Use Emerald in Xubuntu"
date: 2011-04-25
forum: General Help
---

### Post by neu5eeCh on 2011-04-25
OK... I give up. I'll be grateful for anyone who can point me to a plain and simple explanation for how to use Emerald in XFCE, thanks. Note: I've installed Compiz, Fusion, and Emerald, but XFCE just plain refuses to acknowledge their presence.

There must be a script I need to edit somewhere...

This is the BETA version of the latest Xubuntu, by the way...

---

### Post by Frogs Hair on 2011-04-25
This command is for Gnome , so I don't know if it will with Xubuntu .```
emerald --replace
```

---

### Post by WorMzy on 2011-04-25
I'm not sure how Xubuntu handles logins, but on Arch, you add
```
fusion-icon &
``` before ```
exec ck-launch-session startxfce4
``` in .xinitrc

You need to have fusion-icon installed for that to work though, obviously.

---

### Post by 3Miro on 2011-04-25
Can you run compiz? You need compiz config setting manager (CCSM) and edit the "Window decorations" command option to:
```
emerald --replace
```

Then from XFCE, you can hit Alt+F2 and then type
```
compiz --replace
```

This should get you into compiz + emerald.

---

### Post by 3Miro on 2011-04-25
> **WorMzy said:**
> I'm not sure how Xubuntu handles logins, but on Arch, you add
```
fusion-icon &
``` before ```
exec ck-launch-session startxfce4
``` in .xinitrc

You need to have fusion-icon installed for that to work though, obviously.

This will not work in Ubuntu. Login is handled by GDM not startx. This will not work in Arch + GDM either.

If you want to make the change permanent, you can add compiz --replace or fusion-icon to the sessions apps in XFCE. Also, the Fusion-icon is designed for Gnome, it works with XFCE, but I recommend the "--replace" command.

---

### Post by neu5eeCh on 2011-04-25
Just got home from work. Thanks to all for your suggestions. 

3Miro: Does using the --replace command obviate the need for Fusion? Should I just uninstall Fusion Icon?

Meanwhile, I'll try to use these suggestions.

---

### Post by neu5eeCh on 2011-04-25
You know... I'm trying to do this in Virtualbox (because I want to iron this all out before I install it), but I'm beginning to think VBox might be getting in the way. I have 3-D checked off but...

---

### Post by neu5eeCh on 2011-04-27
OK. I installed Xubuntu on my test partition, and I still can't get Emerald to work. I can switch windows manager to Compiz but all "Window Decorations" vanish. In other words, there are no title bars or window borders.

Any ideas?

---

### Post by WorMzy on 2011-04-27
Have you installed compizconfig-settings-manager, and used it to configure Compiz's plugins? You'll need the Window Decoration plugin enabled and set to use emerald; and you'll probably need to enable the Move, Resize and Place Window plugins too.

---

### Post by neu5eeCh on 2011-04-27
> **WorMzy said:**
> Have you installed compizconfig-settings-manager, and used it to configure Compiz's plugins? You'll need the Window Decoration plugin enabled and set to use emerald; and you'll probably need to enable the Move, Resize and Place Window plugins too.

Yeah, I've done all that. Thanks though...

I tried installing the Simple Settings Manager (too) but the Ubuntu Software Manager complained of missing dependencies, maybe because Xubuntu is still in Beta?

---

### Post by neu5eeCh on 2011-04-29
April 29: Just bumping this back to the top in case someone knows how to use Emerald in Natty Xubuntu? 

I can activate compiz, but it doesn't *stay* activated. Even with compiz activated, no screen decorations work.

I'm beginning to think Emerald doesn't work in Natty?

---

### Post by Borsook on 2011-04-30
Emerald does not work for me, it gives segmentation fault. But you can run Compiz in Xubuntu using GTK window decorator.

---

### Post by andrewthomas on 2011-05-02
I got it working

[http://ubuntuforums.org/showpost.php?p=10757398&postcount=11](http://ubuntuforums.org/showpost.php?p=10757398&postcount=11)

---

