---
title: "how does unity handle .desktop files?"
date: 2011-10-31
forum: General Help
---

### Post by watgrad on 2011-10-31
How has the way Unity's launcher handles desktop files changes in 11.10?

Directions for adding launchers like the one listed below no longer seem to work:

[http://ubuntuguide.net/use-classic-menu-in-ubuntu-11-04-unity-launcher](http://ubuntuguide.net/use-classic-menu-in-ubuntu-11-04-unity-launcher)

Is there another method? or some other trick to adding these types of launchers to the sidebar?

---

### Post by 3rdalbum on 2011-10-31
As far as adding a .desktop file to the Launcher goes, it should work the same as before. Are you using Unity 3D?

---

### Post by Mark Phelps on 2011-10-31
Unfortunately, I wish it WERE the same as with 11.04 -- but sadly, this is yet another thing that worked with 11.04 but not with 11.10.

The right-click option has apparently been removed from the 11.10 Unity desktop.

So, I tried to create one manually by editing an existing .desktop file.  Not only does that NOT work (doesn't show up in the launcher), it had the side-effect of disabling the original .desktop file.

What I found DOES work is the following:
1) Use the create-launcher option in 11.04 to create the file
2) Login to 11.10
3) Copy the file from the 11.04 desktop to the 11.10 partition.

Yet ANOTHER reason why I am disliking 11.10 more every day.

---

### Post by watgrad on 2011-10-31
> **Mark Phelps said:**
> Unfortunately, I wish it WERE the same as with 11.04 -- but sadly, this is yet another thing that worked with 11.04 but not with 11.10.

The right-click option has apparently been removed from the 11.10 Unity desktop.

So, I tried to create one manually by editing an existing .desktop file.  Not only does that NOT work (doesn't show up in the launcher), it had the side-effect of disabling the original .desktop file.

What I found DOES work is the following:
1) Use the create-launcher option in 11.04 to create the file
2) Login to 11.10
3) Copy the file from the 11.04 desktop to the 11.10 partition.

Yet ANOTHER reason why I am disliking 11.10 more every day.

Well - sadly I replaced 11.04 with 11.10...so this isn't an option...

This seems like a basic functionality - the ability to add shortcuts to a launcher seems like kind of an essential feature...

---

### Post by philinux on 2011-10-31
> **watgrad said:**
> Well - sadly I replaced 11.04 with 11.10...so this isn't an option...

This seems like a basic functionality - the ability to add shortcuts to a launcher seems like kind of an essential feature...

 [http://askubuntu.com/questions/66677/how-to-create-a-custom-launcher-in-unity](http://askubuntu.com/questions/66677/how-to-create-a-custom-launcher-in-unity)

I think a gui will come out for this. As one will for quicklists I hope.

---

### Post by mcduck on 2011-10-31
> **watgrad said:**
> Well - sadly I replaced 11.04 with 11.10...so this isn't an option...

This seems like a basic functionality - the ability to add shortcuts to a launcher seems like kind of an essential feature...

I wouldn't expect Gnome developers themselves to add that feature back, considering how Gnome Shell doesn't even use desktop icons by default. 

Perhaps Ubuntu's developers or some another party creates a new tool for this at some point. Meanwhile, you might want to just use the "Main Menu" tool for the purpose. It's even installed by default.

---

### Post by 3rdalbum on 2011-11-01
Oh, excuse me. I misunderstood what was being asked.

The Unity Launcher handles .desktop files exactly the same as before - drag them onto the Launcher and they will stick there.

However, the Nautilus-drawn desktop no longer has the option to "Create a launcher". Easy fix: Instead of creating a .desktop file using the desktop, use the Main Menu program (available from the Dash) to create a .desktop file that will appear in the applications list. Then drag it to the Unity Launcher.

However, I don't think this works with Unity 2D, only with 3D.

---

