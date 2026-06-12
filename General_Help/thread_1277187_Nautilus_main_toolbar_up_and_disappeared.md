---
title: "Nautilus main toolbar up and disappeared"
date: 2009-09-28
forum: General Help
---

### Post by Murrquan on 2009-09-28
Okay ... this is weird, so bear with me.

Open a Nautilus window. Go to View, and look at Main Toolbar. Uncheck that and see what disappears. That's what my Nautilus window looks like. Except that it's still checked, and toggling it doesn't do anything. Even more inexplicable, the Global Menu Applet identifies Nautilus as a "CD/DVD Creator."

I installed the Gloobus preview a little while back, following the instructions here: [http://gloobus.wordpress.com/2009/09/08/ppa/]("http://gloobus.wordpress.com/2009/09/08/ppa/") It patches Nautilus, and I thought that might be the problem. So I did a sudo apt-get remove gloobus-preview, and even uninstalled and reinstalled Nautilus, then did a nautilus -q and restarted it. Still no dice.

What can I do to solve this? Any ideas?

---

### Post by kerry_s on 2009-09-28
did you try deleting the settings folder? ~/.gconf/apps/nautilus

---

### Post by Murrquan on 2009-09-28
> **kerry_s said:**
> did you try deleting the settings folder? ~/.gconf/apps/nautilus

I did just now. No dice. >.>

---

### Post by Prominence on 2009-09-28
I'm having the same issue

---

### Post by ammonkey on 2009-09-28
Hi, if u want to go back to the original nautilus u have to deactivate the ppa. and then u can reinstall nautilus and have the original one provided by ubuntu.

---

### Post by sancho panza on 2009-09-28
> **ammonkey said:**
> Hi, if u want to go back to the original nautilus u have to deactivate the ppa. and then u can reinstall nautilus and have the original one provided by ubuntu.

Correct. Its due to the gloobus update and can be fixed by first deactivating the gloobus PPA and then locating the nautilus packages and forcing synaptic to downgrade using the Package > Force Version menu to select the previous versions. Then hit apply.

Cheers,

---

### Post by Murrquan on 2009-09-28
> **sancho panza said:**
> Correct. Its due to the gloobus update and can be fixed by first deactivating the gloobus PPA and then locating the nautilus packages and forcing synaptic to downgrade using the Package > Force Version menu to select the previous versions. Then hit apply.

No good. I edited /etc/apt/sources.list and removed the PPA (I already uninstalled the program itself, mind). Then I went to Synaptic and did a "complete uninstallation" of the nautilus package, then forced it to install the earliest version available. Still won't display the menu.

---

### Post by ammonkey on 2009-09-28
do u use globalmenu?

---

### Post by Murrquan on 2009-09-28
> **ammonkey said:**
> do u use globalmenu?

The GNOME Global Menu Applet? I do, and have for months now. Nautilus only just now gave me this problem after the last update.

---

### Post by ammonkey on 2009-09-28
Correct me if i am wrong but globalmenu remove menubar of an application right?
Anyway if u removed the ppa entry from your source list and reinstall nautilus u got the version provided by Ubuntu. The gloobus patched version don't replace configuration files of your system at any moment, so if u removed it u get rid of it. So investigate on how to remove a package or a ppa u're missing something

---

### Post by Murrquan on 2009-09-28
> **ammonkey said:**
> Correct me if i am wrong but globalmenu remove menubar of an application right?
Anyway if u removed the ppa entry from your source list and reinstall nautilus u got the version provided by Ubuntu. The gloobus patched version don't replace configuration files of your system at any moment, so if u removed it u get rid of it. So investigate on how to remove a package or a ppa u're missing something

The global menu applet removes the menu bar with things like File, Edit, etc. That's not what's missing here.

Thanks anyway.

---

### Post by ammonkey on 2009-09-28
u can try in a console:
gconf-editor
apps/nautilus/preferences/start_with_toolbar 
check if it's enabled close nautilus, reopen it and see if there's any differences.

---

### Post by Murrquan on 2009-09-28
Never mind ... somehow it seems to have solved itself >.>

Maybe one of those earlier solutions worked, but it didn't take effect until just now?

Many thanks!

---

### Post by ammonkey on 2009-09-28
nice u solved your problem

I still don't understand what u were missing in the patched version. Unfortunately u didn't take screenshots.
If it's just the menu toolbar u can pop it with alt+m shortcut like i already explained in other threads.

---

### Post by thomasboleyn on 2009-09-29
I seem to be having this problem also. The 'file, edit' etc toolbar is missing from nautilus. I DO have the gloobus PPA in my sources list, which I will promptly delete when I get home as well as reverting nautilus to it's previous state, and hopefully this will resolve the issue.

---

### Post by octopuskevin on 2009-09-29
edit.. missed ammonkey's post... lol how pathetic is that? I'm so used to broken packages I usually forget about shortcut keys.

Thanks

---

### Post by t4ggs on 2009-09-29
I had the exact same problem after installing gloobus and i do take a screenshoot...

[http://ubuntuforums.org/showthread.php?t=1277768](http://ubuntuforums.org/showthread.php?t=1277768)

---

### Post by thomasboleyn on 2009-09-29
> **thomasboleyn said:**
> I seem to be having this problem also. The 'file, edit' etc toolbar is missing from nautilus. I DO have the gloobus PPA in my sources list, which I will promptly delete when I get home as well as reverting nautilus to it's previous state, and hopefully this will resolve the issue.

I deleted the gloobus PPA, logged in to an xfce session, totally removed and reinstalled nautilus using repo version, logged back in to gnome and the problem was resolved.

---

### Post by coffee on 2009-10-06
> **sancho panza said:**
> Correct. Its due to the gloobus update and can be fixed by first deactivating the gloobus PPA and then locating the nautilus packages and forcing synaptic to downgrade using the Package > Force Version menu to select the previous versions. Then hit apply.

Cheers,

Ok I am having the same issue and can not get it fixed.  I do not seem to have the "gloobus" Update and have reinstalled nautilus, and deleted the config files to no avail.  This is a little disconcerting as it is showing up in synaptic, the terminal, nautilus and I am sure some place yet not found.  I do have the toolbar in Firefox, Thunderbird and Openoffice.  This is a weired one.

I got it you have to completely install all "global-menu" items.  Open Synaptic (or you package management tool of choice) do a search for "global menu" and select completely remove for all installed packages.  After this is done the toolbar comes back.

---

### Post by Janhouse on 2009-10-09
I had the same problem (actually it is not problem for me because I like nautilus better without menubar) after installing gloobus.
Today after playing with themes it appeared back. I found out that there is shortcut key alt+m to hide/unhide it :)

But I can't get gloobus to work in nautilus. :(

---

### Post by umutert on 2010-04-19
I had exactly the same problem, there were no menu bars on nautilus.
the cause of the problem was using global menu (which is a kind of menu bar as in mac) instead of menu bar.
solution comes with disabling 'Enable Global Menu For GTK applications'. you can do it by adding global menu applet to a panel, after right click on the applet in the panel > preferences, at this point you should see two options under General Settings tab, un-check both of the check boxes(actually unchecking 'Enable Global Menu For GTK applications' is enough) and taadaaaa, menu bar is in your service.

---

