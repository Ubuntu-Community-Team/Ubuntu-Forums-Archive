---
title: "Stop windows from Maximizing"
date: 2012-04-26
forum: General Help
---

### Post by thedevilsjester on 2012-04-26
After being away for awhile, I have decided to try Unity again, as I cannot seem to find a good home with Gnome 3 or KDE 4 and I like Unity, I always have, but the choice to put the close box on the left side has always been a deal breaker for me.  Moving them to the right through Ubuntu Tweak or any of the other methods does not move them when the window is maximized, which is often the case for me.

I am wondering if there is a way to prevent a window from losing its title bar when it maximizes.  I have already removed the global menus and while this makes Unity nicer to use, it doesnt prevent maximization of the window. This would solve my last (and most important) issue and I could use Unity in peace.

Does anyone know a solution to this?

All of the results I could find on the forum have to do with the auto maximizing, or the drag to top maximizing, not the removal of the window decorations.

I am running 12.04

---

### Post by rg4w on 2012-04-26
I believe what you're referring to is the Automaximize value in the Unity plugin for Compiz Config.

The value there represents the percentage of the screen last occupied by a window which will then cause the window to be maximized next time it's opened.

I set mine 100 and now I'm in charge of my window sizes again.

I'd be very interested in reviewing the usability data that led to this decision.  Traditionally, anything that takes control away from the user must have unquestionable benefit to be worth taking that control away.  This one seems at best questionable, but if it tested better than alternatives in early prototyping, it would be interesting to see what those alternative prototypes looked like.

---

### Post by thedevilsjester on 2012-04-26
> **rg4w said:**
> I believe what you're referring to is the Automaximize value in the Unity plugin for Compiz Config.

This is not what I am asking about at all.

What I wish to do is prevent Unity from removing the window decorations when it maximizes so that I still have my tile bar with the close buttons on the right.

---

### Post by rg4w on 2012-04-29
> **thedevilsjester said:**
> This is not what I am asking about at all.
My apologogies.  Seems I misunderstood the title of this thread.

> What I wish to do is prevent Unity from removing the window decorations when it maximizes so that I still have my tile bar with the close buttons on the right.
For the last couple years the close/minimize/maximize buttons have been on the left of the window's title bar, not the right.  In 12.04 those button are still there, visible with you bring the mouse into the top panel to access them.

---

### Post by thedevilsjester on 2012-04-29
> **rg4w said:**
> For the last couple years the close/minimize/maximize buttons have been on the left of the window's title bar, not the right.
Yes but there is an easy option to move them back to the right, and until Unity, this was a complete 'fix'.

In Unity, I can move the buttons to the right, as I always could, but it ignores my choice to put them on the right when a window is maximized.

If I can prevent windows from losing their decorations when maximizing, this would solve the problem, since the decorations respect the settings.

> **rg4w said:**
> In 12.04 those button are still there, visible with you bring the mouse into the top panel to access them.
Yes but they are on the left, and I cannot use Unity for more than a couple minutes without becoming extremely frustration by 
their location and just booting to a different distribution.  

I am hoping for a simple fix to disable this nonstandard behavior, such as what can be done for global menus, and the scroll-bar overlay, and then I could use Unity without pulling my hair out! :P

---

### Post by rg4w on 2012-04-30
What is the plugin that lets you move the window controls to the right, and did you contact that author to find out why it's no longer compatible with Unity?

---

### Post by thedevilsjester on 2012-04-30
> **rg4w said:**
> What is the plugin that lets you move the window controls to the right, and did you contact that author to find out why it's no longer compatible with Unity?
It is not a plugin, its the normal functionality of the window manager that has been there for over a decade.  Its the setting that Ubuntu used to default everything to the left, and it works perfectly well to move it back to the right, but Ubuntu does their own custom thing when its full screen and does not respect this setting.

---

### Post by rg4w on 2012-04-30
> **thedevilsjester said:**
> It is not a plugin, its the normal functionality of the window manager that has been there for over a decade.  Its the setting that Ubuntu used to default everything to the left, and it works perfectly well to move it back to the right, but Ubuntu does their own custom thing when its full screen and does not respect this setting.
Perhaps my use of "plugin" was too specific.  What I meant to ask is what did you change to get this appearance?  

As you noted, Ubuntu ships with those controls on the left, so to move those requires some user action.

Did you change to a different theme, customize a theme, or use something else?

---

### Post by thedevilsjester on 2012-04-30
> **rg4w said:**
>  
As you noted, Ubuntu ships with those controls on the left, so to move those requires some user action.

Did you change to a different theme, customize a theme, or use something else?

No more than you would changing your desktop background.   Its a setting for the window manager an there are many ways to change it, easiest and most official is probably to use the settings dialog like gconf.

You keep on referring to this as if its some crazy fringe hack and not a standard setting  that Ubuntu choose to change the default on.  Ubuntu does something custom when in full screen, and that's what I am trying to prevent much like uninstalling the global menus or the scroll bar overlay reverts that back to standard.

---

### Post by rg4w on 2012-04-30
> **thedevilsjester said:**
> No more than you would changing your desktop background.   Its a setting for the window manager an there are many ways to change it, easiest and most official is probably to use the settings dialog like gconf.

You keep on referring to this as if its some crazy fringe hack and not a standard setting  that Ubuntu choose to change the default on.  Ubuntu does something custom when in full screen, and that's what I am trying to prevent much like uninstalling the global menus or the scroll bar overlay reverts that back to standard.
Sorry if it seems that way; that's not my intent.

Unity is a very picky thing, with so many of the flexibilities we've previously enjoyed no longer compatible with the new DE.  I'm a Compiz Cube fan myself, so I don't think such things are crazy at all.

What I'm hoping to be able to do is to find the specific element that isn't working for you, so we can find a way to make it compatible.

Very little work has been done on Unity thus far to make it fault-tolerant with any of the many changes Ubuntu users have been accustomed to being able to enjoy.  My hunch here is that if we can find the specific thing that was change, we can find a way to work around Unity's finicky/flakey nature and get you exactly what you want.

---

### Post by thedevilsjester on 2012-05-01
> **rg4w said:**
> What I'm hoping to be able to do is to find the specific element that isn't working for you, so we can find a way to make it compatible.

Ideally I would like to change how Unity places the window controls in the upper left hand corner of the window to the more standard, natural right hand side.

More realistically I would simply like to prevent Unity from removing the window decorations when a window maximizes, because the window decorations respect the control location setting, and this would bypass the need to actually change the behavior in Unity itself.  I am hoping for a solution similar to how I can remove the liboverlay-scrollbar package to 'fix' the scrollbars and remove the appmenu-* package(s) to 'fix' the global menu.  I would be willing to use a plugin if such a plugin existed and it was actively maintained, but I am not open to source modifications because I do not want to have to manually compile and patch Unity with each new build.

---

### Post by rg4w on 2012-05-01
Yes, modding Unity itself wouldn't be the way to go.  That's why I was hoping to learn which theme or other mod you'd used so perhaps there may be a way to fix it there.

---

### Post by thedevilsjester on 2012-05-01
> **rg4w said:**
> Yes, modding Unity itself wouldn't be the way to go.  That's why I was hoping to learn which theme or other mod you'd used so perhaps there may be a way to fix it there.
Again, its not a theme, its not a plugin, its not a mod, its not a hack, its a standard setting.  I am simply restoring the setting to its standard default.  This is done (typically) through standard settings tools like gconf, and has been done by a large number of Ubuntu users since the switch.

---

### Post by OzzyFrank on 2012-05-02
> **rg4w said:**
> As you noted, Ubuntu ships with those controls on the left, so to move those requires some user action.

Hey buddy, to move titlebar control buttons from left to right, just open a terminal and paste this:

gconftool-2 -t str --set /apps/metacity/general/button_layout "menu:minimize,maximize,close"

---

### Post by rg4w on 2012-05-02
> **OzzyFrank said:**
> Hey buddy, to move titlebar control buttons from left to right, just open a terminal and paste this:

gconftool-2 -t str --set /apps/metacity/general/button_layout "menu:minimize,maximize,close"
Hey buddy, thanks for that.  That's the sort of specific user action I was hoping to discover.

Metacity themes are easily editable.  Is the problem that Unity is ignoring Metacity directives when it renders the window controls, or is this something that can be addressed by editing the theme?

---

### Post by Paddy Landau on 2012-05-02
Unity is being designed to present a consistent interface between various devices, including desktop, tablet, TV, and smartphone.

Therefore, Unity does not have much flexibility in the way of customisation.

If you don't like Unity, it's best to look at using a different distro, such as Xubuntu (XFCE), Lubuntu (LXDE), Mint, and so forth. Otherwise you will end up tearing out your hair.

Alternatively, just get used to having the buttons on the right, as Mac users do.

---

### Post by thedevilsjester on 2012-05-02
> **rg4w said:**
> Hey buddy, thanks for that.  That's the sort of specific user action I was hoping to discover.

Metacity themes are easily editable.  Is the problem that Unity is ignoring Metacity directives when it renders the window controls, or is this something that can be addressed by editing the theme?
The problem is Unity kills the window decorations, thus metacity, when in full screen and does what ever they want without respecting existing settings.  Its unlikely that they will, so just preventing their full screen hack is the most ideal solution like you can do with their other hacks.

---

### Post by mc4man on 2012-05-02
There is currently only one way to prevent this on unity sessions

Don't maximize your windows if where the buttons are is such a big deal

---

### Post by OzzyFrank on 2012-05-02
The position of control buttons is indeed very theme-specific, which is why people sqealed with delight when they found changing GTK/Metacity themes could get their control buttons back to the right. But at least with the command I supplied, you can grab any theme you like - like the Ubuntu default - and put the buttons wherever you like. You can even [remove buttons or add spacers]("http://ubuntugenius.wordpress.com/2010/05/18/move-title-bar-control-buttons-to-the-right-or-left-even-add-a-spacer-in-ubuntugnome/") if you please.

As for Unity, I don't use it, but had fun after upgrading to 12.04 when Unity appeared over Gnome 3 Classic - both functioned perfect well together (I could switch between the panels with a click) until I disabled the Unity plugin.

But yeah, anyone not happy with Unity should [install Gnome Classic and/or Gnome Shell]("http://ubuntugenius.wordpress.com/2011/10/23/ubuntu-11-10-fix-how-to-add-the-classic-desktop-and-gnome-3-shell-as-login-options/"), or other desktop environments like Cinnamon, KDE or Xfce.

---

### Post by OzzyFrank on 2012-05-02
> **rg4w said:**
> Is the problem that Unity is ignoring Metacity directives when it renders the window controls, or is this something that can be addressed by editing the theme?

In other words, Unity has nothing to do with it - any theme with control buttons on the left look the same in Gnome Classic or any other DE. So you can definitely edit a theme, or just reset the buttons with that command.

Note that when you upgrade, or whenever the default theme gets updated, the buttons will return to the left, but you can apply that command and watch them shoot straight back to the right. And if you want an easy way to do so each time you need to, you can make a launcher witht that command, or [create a command "alias" for it]("http://ubuntugenius.wordpress.com/2009/08/31/custom-terminal-shortcuts-via-bash-aliases/") like "reset-buttons", which is easy to remember.

---

### Post by Paddy Landau on 2012-05-03
I don't know why people are so upset about the positioning of the close buttons. What I would like is to find out how to put the Microsoft Windows buttons on the left, just like Ubuntu and Mac. But I'm really not that bothered to find out how.

---

### Post by OzzyFrank on 2012-05-03
> **Paddy Landau said:**
> I don't know why people are so upset about the positioning of the close buttons. What I would like is to find out how to put the Microsoft Windows buttons on the left, just like Ubuntu and Mac. But I'm really not that bothered to find out how.

OK, I'm daring to venture you're a Mac user, or a former one? I've been using computers since 1993, from Windows 3.11 onwards, and migrated to Ubuntu in 2006. In all that time, the buttons have been on the right.

When Ubuntu decided to put them on the left, all the Mac users went "Yay!", but those of us used to all those previous versions of Windows, not to mention the many various flavours of Linux, were at a loss as to WHY. I mean, for people like me, it meant ignoring over 15 years of automatically moving my cursor to the top-right to close, minimise or maximise a window.

But as you see, it's really just a theme, so you can pick another, or you can change the button layout with a simple command-line hack. BUT I can see why many people are bothered by this, as Mac users are a minority, so the Ubuntu team should have included a setting that could be changed somewhere (or something like that - I actually saw a lot of people jump ship to other distros based on the left control buttons).

As for Windows, not only is there no way to change that, if you were a programmer and found out how to hack that, you are legally prevented from doing so, even on a single copy that is only on your computer. Windows ain't linux, unfortunately.

---

### Post by Paddy Landau on 2012-05-04
> **OzzyFrank said:**
> OK, I'm daring to venture you're a Mac user, or a former one?No. The last time I used a Mac was in the 1980's. I used to be an expert Windows user, but having become fed up with the time wasted on fixing Windows problems, I became an Ubuntu user four years ago. When Ubuntu changed its close buttons to the left, I found it took me maybe a day to get used to. It's really not a big deal.

> **OzzyFrank said:**
> As for Windows, not only is there no way to change that, if you were a programmer and found out how to hack that, you are legally prevented from doing so, even on a single copy that is only on your computer. Windows ain't linux, unfortunately.
Ah. Time for another antitrust case against Microsoft? (I'm kidding.)

---

### Post by silviobandeira on 2012-05-10
Just see this post:

[http://ubuntuforums.org/showthread.php?p=11924571#post11924571](http://ubuntuforums.org/showthread.php?p=11924571#post11924571)

---

### Post by JohnAadams on 2012-05-10
I turned off the maximize function and am much happier now.

---

### Post by JohnAadams on 2012-05-16
I dunno how else to explain it, but whenver I move a window to the top of the screen, it freakin' auto-maximizes it. It's driving me NUTS! How do I turn it off?

---

### Post by Paddy Landau on 2012-05-17
> **JohnAadams said:**
> I dunno how else to explain it, but whenver I move a window to the top of the screen, it freakin' auto-maximizes it. It's driving me NUTS! How do I turn it off?
Which version of Ubuntu are you using? If it's Precise 12.04, do this:

[LIST]
[*]Install [CompizConfig Settings Manager]("apt:compizconfig-settings-manager") (CCSM)
[*]Run CCSM
[*]Desktop (left-hand side) > Ubuntu Unity Plugin > Experimental > Automaximize value > 100
[/LIST]
If you are using a different version of Ubuntu, let us know which one.

---

