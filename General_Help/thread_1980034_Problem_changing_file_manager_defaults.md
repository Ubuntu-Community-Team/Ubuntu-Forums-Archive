---
title: "Problem changing file manager defaults"
date: 2012-05-14
forum: General Help
---

### Post by Manmadegod on 2012-05-14
Hello, I have been trying to change my default file manager, and I have already installed and run Nautilus on my Xubuntu system (latest version, just installed). What I have been told and did so far has not produced the results which I expected.

What I expect I should be able to change on my system are the Place links which are installed as default by the DVD. What I have observed are three types of these:
**1**. There are non-removable links to the File System and Home which the system maintains on my desktop.
**2**. There is a removeable (so I think) menu launcher (for Home, documents, downloads, media types, etc) which was placed on the lower desktop panel  by the DVD installer.
**3**. There are the Place links which I have created on my desktop and panel as launchers. The edit menu for creating these is the same as for creating application launchers, and is different from the edit menu for Place Link Type 2.

Through the Settings Manager->Preferred Applications window I was able to select Nautilus over Thunar. This has been saved, but it has only been effective with Type 2. The links of Type 1 cannot be removed, therefore they will annoy me when I impulsively hit them and find that I don't have the search feature (Nautilus is among a relative few of the GTK 2 toolkit which do, what's with that) when I need it. 

I'm not concerned about my Type 3 launchers, as the system gives me control for each of them in the Command box, but I hope somebody can resolve my question on whether those Type 1 launchers can be made to point to a different file manager. I'm sure there's an  editable code file for this and probably other things somewhere, but where is it?

I would also appreciate some explanation of how Type 2 launchers are set up, and why the edit menu is different.

Thanks.

---

### Post by rai4shu2 on 2012-05-14
The "Type 1" Icons come from the Desktop (not the file manager). You need to:

right-click the desktop, select "Desktop Settings", then click the "Icons" tab

That will let you uncheck the icons that are otherwise unremovable.

For search, it's generally suggested that you use Accessories/Catfish.

---

### Post by Manmadegod on 2012-05-14
> **rai4shu2 said:**
> The "Type 1" Icons come from the Desktop (not the file manager). You need to:

right-click the desktop, select "Desktop Settings", then click the "Icons" tab

That will let you uncheck the icons that are otherwise unremovable.

For search, it's generally suggested that you use Accessories/Catfish.


Thanks - I guess that's a workable solution, if not a truly satisfying one. Getting rid of them will prevent annoyance, but this feature (not known to Windows XP) of the Linux desktop would be  nice to have if it could be tweaked to call the browser of my choice when USB devices are plugged in.  Don't suppose there's a way of fixing this through some text configuration file, somewhere?

---

### Post by rai4shu2 on 2012-05-14
Automatically browsing removable media is a feature of Thunar (thunar-volman to be specific). I suppose you need to go to Settings/Settings Manager/Removable Drives and Media, then uncheck that option (so that Thunar doesn't kick in). Then configure Nautilus to do that (I'm not sure how to do that as I don't use Nautilus).

---

### Post by Manmadegod on 2012-05-14
> **rai4shu2 said:**
> Automatically browsing removable media is a feature of Thunar (thunar-volman to be specific). I suppose you need to go to Settings/Settings Manager/Removable Drives and Media, then uncheck that option (so that Thunar doesn't kick in). Then configure Nautilus to do that (I'm not sure how to do that as I don't use Nautilus).

Guess I'm going to be happy with just pulling the desktop icons after all - I just found out that Nautilus happily launches an open window when I plug in devices - nice!

And thanks for your helpful answers!

---

