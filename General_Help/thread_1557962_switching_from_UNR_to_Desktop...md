---
title: "switching from UNR to Desktop.."
date: 2010-08-21
forum: General Help
---

### Post by switch10 on 2010-08-21
So I did a ```
sudo apt-get install ubuntu-desktop && sudo apt-get purge ubuntu-netbook*
``` To switch from UNR to the Desktop version.

Everything is fine except for the fact that when I have a maximized window, I do not have the minimize, maximize, and close buttons.  

I have a feeling I just need to tweak something in gconf-editor, but I can't seem to find the correct setting.

any help?

---

### Post by zaho0006 on 2010-09-02
Not really a direct fix but it may be helpful, I was running UNR and found out that applets were locked, so now I just boot into gnome instead. Another user posted the following instructions:

"you log out
select your name
in the session menu select gnome
log in
add the netbook stuff to startup(netbook-launcher, maximus)
tweak the panels"


Hope this helps

---

### Post by Objekt on 2010-09-02
I'm interested in more or less the same thing, with a twist: I sometimes hook my netbook up to a reasonably large (24") LCD monitor, so at those times I would prefer to have a normal GNOME desktop rather than the netbook-tweaked interface.

I tried logging in with KDE instead of GNOME, but that only sort of worked.  I couldn't find the "Display Preferences" app anywhere!  That app is essential when I'm switching between using the external monitor and using only the netbook's built-in display.

I'm hesitant to apply the command suggested above.  Won't that nuke the UNR bits (Maximus, etc.) completely?  

Another solution did occur to me: LXDE.  Might be just the thing.  I'll try it & report back.

---

### Post by ubun_two on 2010-09-02
You can safely choose Gnome or Netbook from login screen interchangebly from the default UNR installation.  You don't need to purge anything.

---

