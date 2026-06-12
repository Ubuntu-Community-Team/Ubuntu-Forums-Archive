---
title: "Couple AWN questions"
date: 2011-02-13
forum: General Help
---

### Post by michaelzap on 2011-02-13
Bored with standard Gnome panels, so I started using AWN instead...

When I first installed it, I had a clipboard applet (like Glippy or Parcelite). After restart, it's disappeared and is no longer available in the applets list. Any ideas how I can get that back?

What do you AWN users use for a network applet? I guess I can just open Network Connections, but that doesn't show me available networks afaik. And do most of you AWN users keep one Gnome panel running but hidden so as not to lose Alt+F2 and other Gnome features, or is it better to just nuke them all?

---

### Post by Vaphell on 2011-02-13
i removed all gnome panels and went with gnome-do instead. Gnome panels are annoying because they don't cooperate well with other objects like docks and waste space. Gnome devs should create some daemon for hotkeys and stuff and make panels easily removable.
Workflow with gnome-do: press WIN+space, little window shows up in the center, type few characters and it suggests you the app you want. I don't bother with the menu anymore.

I use parcellite and i put it in startup apps. AWN has its own notification area applet so you can access all that stuff that used to be shown in systay on gnome panel - parcellite is there, so is standard network manager.

---

### Post by michaelzap on 2011-02-13
Thanks for the tip. I also use Gnome Do, and I was using Parcelite until I switched to AWN. Before when I tried to test out the Notification Area applet it would crash because I also had a hidden Gnome panel with that on it. Now that I realize that I want that to work on AWN, I removed it from the Gnome panel and that did the trick. Now I have the network manager and Parcelite icons in AWN where I want them.

So if I remove all Gnome panels, I'll lose the Alt+F2 dialog, right? I kinda like that (it's better for say "gksudo nautilus" than Gnome Do), but I think I could live without it (I also have Guake). What else would I be giving up by deleting all the Gnome panels? I think that I'd also need to use Gnome Do or Compiz to set keybindings, and that may be more trouble than it's worth. Right now I just have an empty panel set to autohide, so it's not really bugging me.

Although I haven't been all that excited by Unity or Gnome Shell, I'm glad that some more radical experimentation is going into desktop environments lately, since the same old same old gets boring after a while.

---

### Post by kerry_s on 2011-02-13
> **michaelzap said:**
> Bored with standard Gnome panels, so I started using AWN instead...

When I first installed it, I had a clipboard applet (like Glippy or Parcelite). After restart, it's disappeared and is no longer available in the applets list. Any ideas how I can get that back?

What do you AWN users use for a network applet? I guess I can just open Network Connections, but that doesn't show me available networks afaik. And do most of you AWN users keep one Gnome panel running but hidden so as not to lose Alt+F2 and other Gnome features, or is it better to just nuke them all?

first, use the ppa version, it's more up-to-date:
[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

the network applet is in notifications, indicator applets provide the rest.

alt-f2 i replace with gexec

sorry, forum is acting up. will try to fix pics later.

---

### Post by Vaphell on 2011-02-14
> So if I remove all Gnome panels, I'll lose the Alt+F2 dialog, right? I kinda like that (it's better for say "gksudo nautilus" than Gnome Do), but I think I could live without it (I also have Guake).

in what way it's better than gnome-do? if you type 'gksu nautilus' in gnome-do it will work just fine, besides i have terminal open pretty much all the time so i don't need alt-f2 at all. Does alt-f2 provide a history of recently used commands? if so, then i sorta see your point :)

---

