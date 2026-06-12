---
title: "'Folder widgets' question"
date: 2011-02-12
forum: General Help
---

### Post by Gaba_p on 2011-02-12
Hi,

is there a way to 'hide' all 'folder widgets' from the desktop with a mouse (or keyboard) action? I mean hide as in 'make invisible', not as in 'close forever'.
I'm trying to mimic this Window's app: [http://goo.gl/77cx](http://goo.gl/77cx) (Fences), which is nothing more than a 'folder widget' for windows. The only thing that this app has that I can not reproduce in KDE is the ability to hide all 'folder widgets' with a mouse action (Fences does it with a double click on the desktop)
It's not really that important, I just like a clean desktop and this would be great to have.

Cheers

---

### Post by Gaba_p on 2011-02-14
bump?

---

### Post by ankspo71 on 2011-02-26
Hi,
I think what you need to do is use two different "activities". Here is a link that shows what you can do with activities: [http://maketecheasier.com/use-kde-plasma-activities/2010/09/01](http://maketecheasier.com/use-kde-plasma-activities/2010/09/01)

Multiple activities are sort of like having multiple workspaces, but... Workspaces are more for placing windows across multiple 'duplicated' virtual desktops. Activities gives you multiple 'different' desktops to to customize. So you can have one activity with widgets, and have another without any widgets at all. They can also have separate wallpapers, or even separate slideshow backgrounds. You can then flip though each activity through the pager widget (or Activity Bar widget, depending on how you created the activities), or use the hotkeys to flip through them.

Hope this helps.

---

### Post by Gaba_p on 2011-02-27
Hi ankspo71,

first of all thanks a lot for answering; I thought this thread was buried and long forgotten :)

I tried the 'activities' approach and it comes very close to what I'm aiming at, but with a few little (and not so little) annoyances:

1- I use the 'Slide' or 'Presentation' (I have KDE in spanish, so I'm not sure what this is called in english) option set to rotate the desktop wallpaper automatically every x hours. Now I know that there are a few apps in Gnome that handle this and will let you select how do you want the images to rotate: by name, by date, by size or randomly. In KDE's built in feature there is no such option, and apparently the images are chosen randomly. Furthermore I could not find an equivalent app to perform this action, like the ones that run under Gnome. This is a setback because when I change desktops, instead of a smooth 'fading away' effect I get a whole different desktop wallpaper, which makes the transition feel kind of 'jumpy'.
There are two solutions to this that I can think of:

a- Have one of the Gnome apps run under KDE (which I don't know if it's possible)
b- Somehow control the way KDE rotates through wallpapers.

2- Opened windows are NOT shared. This means that if I am in 'Desktop 1' and I open say 'Google Chrome', if a then proceed to switch to 'Desktop 2', when I click on the minimized Chrome windows on the taskbar (from within 'Desktop 2'), it will go back to 'Desktop 1'

3- The system won't remember which desktop was used last and will always revert to 'Desktop 1' upon restarting. This is really a minor hindrance really, but maybe you know of a way to solve this...


Well, that's enough writing for today, I hope it's not too long and boring and you can direct me on how to solve this issues.

Regards,
Gabriel

---

### Post by ankspo71 on 2011-02-27
Hi Gabriel,

1- I use the 'Slide' or 'Presentation'.
I use this wallpaper feature too. I think KDE needs to improve the fade effect (or let us turn off fade effect) because many people have trouble with the performance when switching wallpapers.

2- Opened windows are NOT shared.

Try right click on your "task manager" widget on your panel and choose "Task Manager Settings". Here you can choose "only show task from the current desktop" and "only show tasks from current activity". These can stop windows from appearing in the panel if they are from other activities and desktops. I'm using KDE4.6 now but I think this also applies to KDE4.5x too.

Also, KDE has window rules that can be made to open any (or all) windows on all desktops if you like. I just created a generic rule to open all windows on all desktops and it's working well (so far). (see screenshot) In KDE you can make these rules by going to System Settings > Window Behavior > Window Rules. You can also make rules for windows by right clicking on the title bars of windows. Right Click on Title bar > Advanced > Special Window Settings (or special application settings).

3- The system won't remember which desktop was used last...
I don't know about this one... but that would be a nice feature.

---

