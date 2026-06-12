---
title: "ALT + Tab changed and can't switch back.."
date: 2011-07-19
forum: General Help
---

### Post by akakingess on 2011-07-19
Okay, I am relatively familiar with Ubuntu, but some time last week it updated and now ALT + Tab temporarily minimizes windows to switch between open apps and shows a little window with icons representing the open apps. I much preferred the old way of just switching between them without minimizing and the more graphically appealing (I guess to some) window. I have checked Keyboard Shortcuts and it seems that I no longer have that my original option available, is there another way to select that option, or add it back to the keyboard shortcuts or am I just stuck with it unless I decide to back up to a previous release? Hope this made sense, and I won't be able to try any suggestions until tomorrow so please feel free to throw as many suggestions as you want to me and I will try them all one by one tomorrow morning.

Thanks in advance for any assistance you may provide,

Earl

---

### Post by CatKiller on 2011-07-20
Install compizconfig-settings-manager. It will let you adjust which plugin you're using for task-switching.

---

### Post by akakingess on 2011-07-21
Thanks for the quick reply, I should have explained that this is on a work computer that I don't have sudo privileges on, so I may not be able to do that. I will try that tomorrow morning, but do you know why it would have changed on it's own without my changing it, was it automatic as part of an update? Thanks for the suggestion and I will try that out and thanks in advance for any info about why as others in the office are curious as well.

EDIT:  I will mark this thread as solved as soon as I can test it and make sure it is working ;)

---

### Post by CatKiller on 2011-07-21
> **akakingess said:**
> I don't have sudo privileges

Although you'd need sudo to install new applications (because they affect all users) the configuration is owned by the user. It's just more difficult to follow without CCSM.

Depending on how locked-down you are, you may well be able to run ```
gconf-editor
```

If the plugin for window switching has been changed, you'll be looking at the active_plugins key of /apps/compiz-1/general/screen0/options. If it's just that the options for the same plugin have been changed, you'll be looking at /apps/compiz-1/plugins/<plugin-name>/screen0/options. The most basic-looking window-switching plugin is Static Application Switcher, or staticswitcher. Without looking at it, it's hard to say what's changed.

If you can't run gconf-editor, you can still change the options from the command-line, but that's even more particular. Or by changing directly the text files where the configuration options are stored.

> 
do you know why it would have changed on it's own without my changing it, was it automatic as part of an update? 

No idea at all. I don't use Unity, so I don't know what changes have come down the pipe recently. A big chunk of Unity is done as a collection of plugins for Compiz, so it's possible that they can interact in some way. Or the configuration got changed by something else.

Good luck!

---

### Post by akakingess on 2011-07-22
Okay, well I mentioned the sudo privileges because you said to install Compiz. I didn't know that simple window switching was a plugin, thought it was native in Gnome or Unity, so I don't know how/why a plugin would have been uninstalled. I will check gconf-editor in the morning and I do appreciate the information. Will let you know how it goes!

---

### Post by CatKiller on 2011-07-22
> **akakingess said:**
> Okay, well I mentioned the sudo privileges because you said to install Compiz. I didn't know that simple window switching was a plugin, thought it was native in Gnome or Unity, so I don't know how/why a plugin would have been uninstalled. I will check gconf-editor in the morning and I do appreciate the information. Will let you know how it goes!

Compiz is already installed. CCSM just lets you tweak its settings. Gnome is a set of applications & Compiz has been included by default in Ubuntu for a while now. The previous window manager, Metacity, also handled this function.

It's not that the plugin's been uninstalled, just that a different one's been selected instead. Or possibly that the settings for the existing one have been changed.

---

