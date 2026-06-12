---
title: "Mouse pointer style won't change"
date: 2010-05-06
forum: General Help
---

### Post by DomesDKG on 2010-05-06
I just installed Kubuntu on my machine, but on returning to gde I still have the oxy-white pointer from kde.  I went to preferences>appearance>themes>customize>pointer, and changed it back to DMZ White, yet the pointer still looks like oxy-white.  I tried it with all of the different pointer options, but none of them will override oxy-white.

How can I fix this?

---

### Post by Smart Viking on 2010-05-06
If you still have kde, change it to the default desktop again, and try to change the mouse pointer from there, and then switch. :)

---

### Post by DomesDKG on 2010-05-06
Well, it changed in KDE, but not in GDE. So now I've got swapped pointer themes. Any other ideas?

---

### Post by helicase on 2010-05-06
Same problem here. However, the 'busy' icon (or whatever it's called) and the little hand have changed back. It's only the mouse pointer itself that's stuck in oxy-white mode. Except when I mouse over the firefox window. How strange is that?

---

### Post by DomesDKG on 2010-05-06
That's actually the exact behavior mine was exhibiting.  I got fed up with it and just removed the oxy-white package which fixed it,though makes oxy-white a non-option of kde as well.  Hopefully there is a more elegant solution to this problem.

---

### Post by helicase on 2010-05-07
Hm, it's even weirder than I thought. When I hover the mouse over the menus in Firefox, I get the pointer as it should be. Then, when I click on one of them (e.g. History) it changes to the KDE one. With others (e.g. Bookmarks) there's no change, though. Even different menu items in the same menu show a different pointer. I took screenshots to illustrate this strange behaviour and lo and behold: the oxygen pointer has magically morphed into the other one.

---

### Post by lancerocke on 2010-05-09
same problem, same behavior as the above poster. is there any fix?

---

### Post by mister_playboy on 2010-05-09
I've seen this sort of behavior when changing between GTK themes in Ubuntu, but logging out/back in fixes it.

Now that I'm using Kubuntu, I dare not install a bunch of Gnome stuff for fear of messing things up. :P

---

### Post by StarWarrior on 2010-05-09
I'm not sure, but this sounds like this known bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/459647](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/459647)

Do you use compiz?

I had this problem with gnome and advanced desktop effects enabled. It went away when disabling them.

---

### Post by helicase on 2010-05-09
Cheers StarWarrior, looks like that's the little bug(ger) I'm having trouble with. I think I'll just be patient and wait for it to be patched officially, but for those of you who can't wait, you can find how to do it yourself in the comments of the bug report (see previous post).

---

### Post by lancerocke on 2010-05-09
> **StarWarrior said:**
> I'm not sure, but this sounds like this known bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/459647](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/459647)

Do you use compiz?

I had this problem with gnome and advanced desktop effects enabled. It went away when disabling them.yes, i use compiz

---

### Post by James78 on 2010-05-09
<Removed>

---

### Post by avl555 on 2010-05-18
That is definitely the bug we're talking about.
For advanced users: see the bug report, there is also a way to install the source package of compiz-core, without this bug. It's quite simple.

---

### Post by gozo-pavo on 2010-05-18
> **helicase said:**
> Hm, it's even weirder than I thought. When I hover the mouse over the menus in Firefox, I get the pointer as it should be. Then, when I click on one of them (e.g. History) it changes to the KDE one. With others (e.g. Bookmarks) there's no change, though. Even different menu items in the same menu show a different pointer. I took screenshots to illustrate this strange behaviour and lo and behold: the oxygen pointer has magically morphed into the other one.

Had a similar problem with gnome in lucid 32 bit with Nvidia restricted drivers.
Removed the restricted drivers and the pointer behaved normally on desktop and in Firefox.

---

### Post by Skywa&#8224;cher on 2010-05-18
I can't remember exactly where I read this, but there is a workaround available.

Find the exact name of the cursor theme you want to install (just look in Appearance Preferences, the same place as where you would normally set a cursor theme). Now go to your /etc/alternatives folder and open the x-cursor-theme file in a text editor (or simply run "**sudo gedit /etc/alternatives/x-cursor-theme**" from a terminal). Change the line "**Inherits = themename**", substituting the name of the cursor theme for "themename". Save the file and reboot.

Works for me. :)

---

### Post by todak on 2010-05-18
Or try this ```
sudo update-alternatives --config x-cursor-theme
``` and select the theme you want for the system default. Log out for the change to take effect. Users will still be able to choose their own pointers under Preferences.

---

### Post by helicase on 2010-05-18
Cheers todak. That's done the trick for me.

---

### Post by NorthenerOfTheSouth on 2010-06-05
> **helicase said:**
> Hm, it's even weirder than I thought. When I hover the mouse over the menus in Firefox, I get the pointer as it should be. Then, when I click on one of them (e.g. History) it changes to the KDE one. With others (e.g. Bookmarks) there's no change, though. Even different menu items in the same menu show a different pointer. I took screenshots to illustrate this strange behaviour and lo and behold: the oxygen pointer has magically morphed into the other one.
I got the same behaviour from the pointer, until I removed the Oxy pointer package. I suppose that that's the best solution unless you have some intention of using it somewhere.

---

### Post by vince2678 on 2010-08-20
Compiz cannot update the mouse cursor theme when it is updated in GNOME.    Install this package to allow compiz to notice the change and feel   free  to modify it however you want. PLEASE read he control info!

Unfortunately only works with GNOME. If anyone has LXDE and XFCE please    send me info on how it stores info about cursor theme and size and the    program used for changing cursor theme. I have KDE in a VM so I'll  try   something there.
 
 LINK: [_http://ubuntuforums.org/showthread.php?t=1557297_]("http://ubuntuforums.org/showthread.php?t=1557297")

READ CAREFULLY!

---

### Post by Bobbyrne01 on 2010-09-25
check out this link, worked for me

[http://www.ubunturoot.com/2010/05/how-to-change-mouse-cursor-in-ubuntu.html](http://www.ubunturoot.com/2010/05/how-to-change-mouse-cursor-in-ubuntu.html)

---

### Post by Shpongle on 2010-09-25
Cheers bob

---

