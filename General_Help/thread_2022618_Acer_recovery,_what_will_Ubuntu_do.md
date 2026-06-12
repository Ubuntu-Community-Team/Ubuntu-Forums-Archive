---
title: "Acer recovery, what will Ubuntu do?"
date: 2012-07-11
forum: General Help
---

### Post by Mattedatten on 2012-07-11
Hey all!

I've installed ubuntu alongside windows, which gave me for example the GRUB boot-loader.

Now, I'm having some problems with windows and drivers and such, so I'm going to restore the computer to factory settings.

But my question is, might there be problems as I've installed ubuntu?

If so, how to uninstall it the safest way?

Thanks a lot in advance!
Mat

---

### Post by hal8000 on 2012-07-11
Ubuntu wont touch your windows installation.
If you've done a wubi install, then use windows control panel, add/remove programs and uninstall wubi or ubuntu.

Factory settings may restore your computer but may also but back on older windows drivers and files.
Hope that helps.

---

### Post by Mattedatten on 2012-07-11
> **hal8000 said:**
> 
If you've done a wubi install, then use windows control panel, add/remove programs and uninstall wubi or ubuntu.

I installed ubuntu from a (Live-)CD, there was a option to install it alongside windows.

> **hal8000 said:**
> 
Factory settings may restore your computer but may also but back on older windows drivers and files.

I know, but, I think my videocard are going down, I called Acer, and I have one more week of warranty. So until then I'll follow both their instructions (restore) and my own (testing software) for trying out if its actually hardware going bad.
But that's a little off topic :)

---

### Post by miegiel on 2012-07-11
@**[COLOR="DarkOrange"]Mattedatten[/COLOR]** I have an acer, but I never used acer recovery. It al depends on how acer implemented the recovery. It could be a "dumb" partition wipe and restore image method that erases everything. But it could also be a "smart" recovery that doesn't touch other partitions than the windows partition and also leaves the user data intact. Maybe there is more info in the manual or on acer's site.

Regardless of the method, I'd backup all the data I wouldn't want to loose and backup the whole /home/Mattedatten directory in ubuntu (including all the hidden files, excluding cashed files for the webbrowser etc.).

---

### Post by Mattedatten on 2012-07-11
> **miegiel said:**
> @**[COLOR=DarkOrange]Mattedatten[/COLOR]** I have an acer, but I never used acer recovery. It al depends on how acer implemented the recovery. It could be a "dumb" partition wipe and restore image method that erases everything. But it could also be a "smart" recovery that doesn't touch other partitions than the windows partition and also leaves the user data intact. Maybe there is more info in the manual or on acer's site.

Regardless of the method, I'd backup all the data I wouldn't want to loose and backup the whole /home/Mattedatten directory in ubuntu (including all the hidden files, excluding cashed files for the webbrowser etc.).

Thanks for the detailed reply!

Thing is, as for now, I'm trying to uninstall Ubuntu as I've not used it actively. I installed it alongside Windows for trying it out, I haven't got any important data on the Ubuntu partitions.

What I'm trying right now:
- Creating a windows repair disk
- Hoping that it will be able to "repair windows" so that it boots instantly to windows, instead onto GRUB.
- Clearing partitions containing Ubuntu
- Doing an Acer restore

Hope that the plan works :P

---

