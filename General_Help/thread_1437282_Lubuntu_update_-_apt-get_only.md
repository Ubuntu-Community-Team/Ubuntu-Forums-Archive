---
title: "Lubuntu update - apt-get only?"
date: 2010-03-23
forum: General Help
---

### Post by TBABill on 2010-03-23
Just curious if anyone has insight into how to update Lubuntu (normal system updates)? I can sudo apt-get update in a terminal window, but is there another GUI method I have not stumbled upon yet? 

The terminal is very easy, but I like the icon on screen to remind me to update my system.

---

### Post by tommynz1975 on 2010-03-23
have you used
System --> Administration --> Update Manager.
you can set how often you want to be told of updates.

I my self do prefer terminal commands for updates, but each to their own.

---

### Post by 2hot6ft2 on 2010-03-23
> **tommynz1975 said:**
> have you used
System --> Administration --> Update Manager.

Lubuntu 10.04 doesn't have that. Let see from memory you could click on the Menu then System > Administration > Synaptic Package Manager
Then you can click on Mark All Upgrades.
But I don't remember there being a Update Manager in the menus.
I only played with it for a while.

---

### Post by TBABill on 2010-03-23
Unfortunately in Lubuntu (Not Ubuntu) the menus are very different (LXDE interface) so it's not the same as in Ubuntu. I'm sure it's buried somewhere but I'm missing it.

---

### Post by 2hot6ft2 on 2010-03-23
> **TBABill said:**
> Unfortunately in Lubuntu (Not Ubuntu) the menus are very different (LXDE interface) so it's not the same as in Ubuntu. I'm sure it's buried somewhere but I'm missing it.
They may have left it out of the Menu by not creating the menu launcher for it. That way it would still run once in the background but wouldn't take up menu space.
Like I said I only played with Lubuntu for a little while but I don't remember seeing it in the menus and it's not like there's much to the menus to have overlooked it.

---

### Post by TBABill on 2010-03-29
2hot, you were correct in your first post. I hadn't realized it was that easy in Synaptic and I found when using PCLinuxOS 2010 beta that they specifically say in their forums NOT to apt-get update unless absolutely necessary. Their OS folks prefer the method you describe with Synaptic to mark all upgrades and let the system update that way. Not hard at all, just different than Ubuntu with the update manager. Command line is faster but it seems strange that Synaptic is preferred over command line, unless it better manages dependencies that way.

---

### Post by Alex22 on 2010-04-29
I use Lubu 10.04, and there is a position next to Synaptic, "Software Surces" (i translated it from Polish).

And there is a tab "Updates", with all the settings like how often, with whom, etc..

But osd manager, with notes about changes, download progress and console install progress in Lubu is absent.

Thanks for the info that apt-get update/upgrade is not to be done.

---

### Post by Spaced on 2010-04-30
Today the Ubuntu update-manager came with the newest updates. Unfortunately, it's not yet integrated with the panel - i.e. when it founds updates available, no icon appears in the panel. This makes it completely useful, because if I have to go to the menu, open update-manager and see if I have anything available, it's faster to launch ```
sudo apt-get update
sudo apt-get upgrade
``` from a terminal.

They will probably add some integration soon, I guess.

---

### Post by ranch hand on 2010-04-30
I would just use synaptic and for get Update Mangler altogether.

Synaptic is easy to use and actually gives you usable information on what is being done.

---

### Post by phillw on 2010-04-30
Hi,

I've updated the instructions on the wiki page for updating, you can find them here --> [https://wiki.ubuntu.com/Lubuntu/DocumentationHelp](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp)

Regards,

Phill.

---

### Post by TBABill on 2010-04-30
Just like in PCLinuxOS! Works great, easy, simple.

---

### Post by phillw on 2010-05-01
Just so as you know, the reason we were using dist-upgrade is that it does a bit more than upgrade on its own. If you'd like to read the subtle differences one of the mods helped tidy up my descriptions of them & you can read it here --> [http://forum.phillw.net/viewtopic.php?f=4&t=9](http://forum.phillw.net/viewtopic.php?f=4&t=9)

Regards,

Phill.

---

### Post by Alex22 on 2010-08-30
Thanks Phill, i think the best method is to add  the Update Manager to the system.
sudo apt-get install update-manager
The only thing is, there will be no systray popup, but you can visit it once a week manually.

---

### Post by Futurian on 2012-07-16
If you install the Gnome update-manager, it will appear as Preferences > Update Manager, at least in 12.04.

---

