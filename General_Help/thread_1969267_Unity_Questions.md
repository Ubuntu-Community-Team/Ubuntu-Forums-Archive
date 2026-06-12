---
title: "Unity Questions"
date: 2012-04-29
forum: General Help
---

### Post by Penguinnerd on 2012-04-29
I have some questions regarding Unity. I've been testing it since 11.04, and I'm making my final judgements on it now that it's in an LTS release. (Meaning I will need to make a decision soon)

1) In my (gnome 2) 10.04 install, I have a feature on my top toolbar that allows me to view the current CPU speed (1.00, 1.33, and 1.67 Ghz respectively, depending on load). It also lets me set how aggressively it under-clocks to save power (or conversely, to gain performance) Is there some way to do this in Unity?

2) On my bottom toolbar in 10.04, I have a workspace switcher. I can click any of four workspaces and switch to it in a single click. In Unity, I seem to require two clicks to switch workspaces. (Or use the keyboard) Is there a way to configure Unity to switch workspaces more efficiently?

3) On the top toolbar in Unity, there's quite alot of unused space in the middle. It's a waste of pixels. Is there some way to put an application launcher in that space? I know it's not an option by default, I'm just wondering if there's a hack of some kind.

That's all I'm wondering about for now. Thanks.

---

### Post by Penguinnerd on 2012-04-30
Does anybody know anything for any of these three questions?
(bump)

---

### Post by Enigmapond on 2012-04-30
Regarding #3...No. Just make it transparent and you won't see the waste of pixels....

Regarding #2...No, this seems to be the way Unity does it...for now but I never use the switcher to change workspaces. The keyboard is much more efficient.

Regarding #1... Have no idea...

---

### Post by Penguinnerd on 2012-04-30
> **Enigmapond said:**
> Regarding #3...No. Just make it transparent and you won't see the waste of pixels....


That's just silly. Whether there's a visible toolbar there or not, the pixels will remain unusable. In Gnome 2, I can compress the amount of screen area used by moving launchers to whatever free space is present on a toolbar. If Unity prides itself on efficient use of screen area, how can this be that way?

> **Enigmapond said:**
> Regarding #2...No, this seems to be the way Unity does it...for now but I never use the switcher to change workspaces. The keyboard is much more efficient.


The keyboard is not more efficient if I'm already using a mouse in most of my applications. If Unity prides itself on being touchscreen-friendly, how can it favor using a keyboard so heavily? It seems like if I were on a tablet, I'd want to switch workspaces with one tap instead of two.

---

### Post by Mathor on 2012-04-30
> **Enigmapond said:**
> Regarding 

Regarding #2...No, this seems to be the way Unity does it...for now but I never use the switcher to change workspaces. The keyboard is much more efficient.


Or when you click on that application in the launcher, it moves you to that particular workspace. click on worspace button, open an application, drag it into that worspace, and then when you click on that application on the launcher it will cycle to that workspace. It's pretty nice.

For your 1st problem go to System Monitor and click on the "Resources" tab. I usually keep that program pinned to my launcher for quick reference. Also, if you are familiar with Conky, you could set up a conky that shows your system info on the desktop.

---

### Post by Penguinnerd on 2012-04-30
> **Mathor said:**
> Or when you click on that application in the launcher, it moves you to that particular workspace. click on worspace button, open an application, drag it into that worspace, and then when you click on that application on the launcher it will cycle to that workspace. It's pretty nice.

That sounds pretty good if I understand correctly. It still requires me to use two clicks to switch to an unused workspace, but it's a useful tip.

> **Mathor said:**
> 
For your 1st problem go to System Monitor and click on the "Resources" tab. I usually keep that program pinned to my launcher for quick reference. Also, if you are familiar with Conky, you could set up a conky that shows your system info on the desktop.

System monitor isn't quite what I had in mind. I want to be able to change from "powersave" to "ondemand" to "performance", and so on. Sometimes I need to save power, and other times I really just need to override the CPU clocking mode to make a video play smoothly. It's about control.

---

### Post by Stray Wolf on 2012-04-30
> **Penguinnerd said:**
> I have some questions regarding Unity. I've been testing it since 11.04, and I'm making my final judgements on it now that it's in an LTS release. (Meaning I will need to make a decision soon)

1) In my (gnome 2) 10.04 install, I have a feature on my top toolbar that allows me to view the current CPU speed (1.00, 1.33, and 1.67 Ghz respectively, depending on load). It also lets me set how aggressively it under-clocks to save power (or conversely, to gain performance) Is there some way to do this in Unity?

2) On my bottom toolbar in 10.04, I have a workspace switcher. I can click any of four workspaces and switch to it in a single click. In Unity, I seem to require two clicks to switch workspaces. (Or use the keyboard) Is there a way to configure Unity to switch workspaces more efficiently?

3) On the top toolbar in Unity, there's quite alot of unused space in the middle. It's a waste of pixels. Is there some way to put an application launcher in that space? I know it's not an option by default, I'm just wondering if there's a hack of some kind.

That's all I'm wondering about for now. Thanks.

1. Try the "System Load Indicator" from the Ubuntu Software Center. You can just search "indicator" and it will come up in the USC. This does exactly what you're talking about unless they changed it in the last few months.
2. You can use CCSM to assign your own keyboard shortcuts. In USC type in "Compiz" and the Compizconfig settings manager will come up. I believe the options you'd be looking for here are under "Unity Plugins" in the CCSM. Or, you can just use Alt+Ctrl+arrow keys to navigate through workspaces.
3. If you load that space up too much it will conflict with the menus of some apps that need that space for options.

---

### Post by codingman on 2012-04-30
#3:

What would you like to put in that space instead? Like Stray Wolf said, you need some space there for indicators and sometimes the description for an application takes that entire space.

---

### Post by pqwoerituytrueiwoq on 2012-04-30
#2
right click the workspace :)
#1
this is why i don't like unity try xubuntu-desktop (in the software center) or mate-desktop (google this one)
currently the sensors applet does not work on nvidia :(

i cant seems to change the governor on xubuntu

---

### Post by Penguinnerd on 2012-04-30
> **Stray Wolf said:**
> 1. Try the "System Load Indicator" from the Ubuntu Software Center. You can just search "indicator" and it will come up in the USC. This does exactly what you're talking about unless they changed it in the last few months.

Nope. Still wrong. It won't let me change governor settings.


> **Stray Wolf said:**
>  2. You can use CCSM to assign your own keyboard shortcuts. In USC type in "Compiz" and the Compizconfig settings manager will come up. I believe the options you'd be looking for here are under "Unity Plugins" in the CCSM. Or, you can just use Alt+Ctrl+arrow keys to navigate through workspaces.

Nope. That still won't do what I want. I said I want to be able to click a workspace and switch instantly, without using the keyboard or clicking twice. (This should really be fixed if it's expected to be pleasant to use on a tablet)

> **Stray Wolf said:**
> 
3. If you load that space up too much it will conflict with the menus of some apps that need that space for options.
No. I have a wide screen, the kind of screen that's supposed to work well with Unity. There's loads of space. On a more narrow monitor, perhaps you would have a point.

Plus, I'm thinking about disabling global menus anyway. It reduces the clarity of context for the menus.

[QUOTE=codingman]
What would you like to put in that space instead? Like Stray Wolf said, you need some space there for indicators and sometimes the description for an application takes that entire space. 
[/QUOTE]
Um... I said application launchers. (Firefox, terminal, etc) I'd like to set the dock to autohide,(I like to have a wider view of my applications!) and have app launchers that I could hit whenever I want to up on the top bar. Even when the dock is hidden. Don't even say that I can just use the dock. I want it to autohide, and I want to be able to click my launchers without waiting for the dock to pop out.

[QUOTE=pqwoerituytrueiwoq]
right click the workspace
[/QUOTE]
You misunderstood me. Before you right-click it, you must click the workspace icon to zoom out to the multi-workspace display. That's two clicks... Count em.

[QUOTE=pqwoerituytrueiwoq]
#1
this is why i don't like unity try xubuntu-desktop (in the software center) or mate-desktop (google this one)
currently the sensors applet does not work on nvidia

i cant seems to change the governor on xubuntu 
[/QUOTE]

Yes, that's what I want to do. Let me know if you figure it out.

---

### Post by pqwoerituytrueiwoq on 2012-04-30
"You misunderstood me. Before you right-click it, you must click the  workspace icon to zoom out to the multi-workspace display. That's two  clicks... Count em."
use the expo plugin and enable a expo edge/corner

i know you can change the governor using the mate-desktop
[http://mate-desktop.org/install/#ubuntu](http://mate-desktop.org/install/#ubuntu)

---

### Post by Penguinnerd on 2012-04-30
> **pqwoerituytrueiwoq said:**
> 
use the expo plugin and enable a expo edge/corner


That's better. Although it still involves extra mouse movement, it's the best I could probably expect. Thanks.

It feels slow to move the mouse the whole way across the screen to a corner, and then out onto the screen again to click a workspace.

And as for MATE, the point of this thread is to decide whether I can "learn to like" Unity. (Or else configure it enough so I feel less awkward in it)

Thanks though. MATE remains one of my fallback options.

---

### Post by codingman on 2012-04-30
Unity is still being progressed. DE's like gnome are advanced and have been around. So they know how to fit it to the user's benefits. I,personally still do not like unity, I just use it to help find bugs and make it more advanced. I like gnome or LXDE, those are the good ones.

---

### Post by Stray Wolf on 2012-05-01
Sorry for not being able to help. Maybe you could submit your workspace switcher idea here: [http://brainstorm.ubuntu.com/.]("http://brainstorm.ubuntu.com/")

That's a bit long-term. I'm at a loss on a short-term solution.
[]("http://brainstorm.ubuntu.com/")

---

