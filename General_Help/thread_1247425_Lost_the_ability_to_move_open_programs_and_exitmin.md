---
title: "Lost the ability to move open programs and exit/minimize/maximize"
date: 2009-08-22
forum: General Help
---

### Post by Losl_Logan on 2009-08-22
I was working on this [http://webupd8.blogspot.com/2009/05/ubuntu-embed-terminal-into-you-desktop.html](http://webupd8.blogspot.com/2009/05/ubuntu-embed-terminal-into-you-desktop.html) and I actually got it to work, but now my computer doesn't have a exit/minimize/maximize button. I don't know what to do. It is really bugging me not being able to move any windows, so if you have any advise it would really help. I have tried turning off the window rule that I enabled but it didn't do anything. I looked around and people have said that you can changed themes, and that didn't work either. I am at a loss.

---

### Post by gldearman on 2009-08-22
Y'know, I tried the same thing, and ran into the same problem.  The rule I wrote in Compiz Fusion to apply only to the "trans" window was being applied to all windows, so they all lost the window decoration and were stuck in place.

I just removed the rule I wrote, and it was fixed.  Are you absolutely certain that you removed all of the rules you added to Compiz fusion?  Are you absolutely certain that you put it back the way it was when you started?

As a troubleshooting step, try disabling the Window Decorations plugin, and see if your problem goes away.  Failing that, try disabling the Window Rules plugin and see if the problem goes away.  Obviously, you'll want to turn these back on when the problem is fixed, but this way, you can narrow down which plugin is causing the problem.

---

### Post by gldearman on 2009-08-22
And just to make sure -- go to CompizConfig Settings Manager, and go to the Window Decoration plugin.  On that screen, in the "Decoration windows" field, it still reads "any", right?  If not, type "any" in that field, and see if your problem is fixed.

---

### Post by earthpigg on 2009-08-23
food for thought:

if compiz ever messes things up completely beyond belief, do this:

alt+f2

then, type "metacity --replace"

"compiz --replace" will put compiz back in charge.

---

### Post by Losl_Logan on 2009-08-23
hey Earthpigg, that did it. but Now i have to try and get the terminal to embed, but thanks, now I know how to fix it. thanks!

---

### Post by Losl_Logan on 2009-08-23
can anyone find a way for both of these things to work, the embeded terminal and the exit/minimize/maximize. so far when I follow the guide it causes my exit/minimize/maximize. any help is greatly appreciated.

---

### Post by gldearman on 2009-08-23
I mostly got the embedded terminal to work without losing the ability to control my other windows.  I followed the [same tutorial]("http://webupd8.blogspot.com/2009/05/ubuntu-embed-terminal-into-you-desktop.html") you initially did, so this may not solve your problem, but here's what I did.

First, I am running 9.04 Jaunty with the Gnome desktop.  In order for this to work, you must enable Compiz Fusion.  If you fixed your earlier problem by following earthpigg's suggestion and switching to Metacity, you will have to switch back (just turn on Visual Effects with System > Preferences > Visual Effects).

Also, you should make sure that you have the CompizConfig Settings Manager installed.  It should be under System > Preferences.  If it isn't there, you can install it from the repos.

To start, just like the tutorial said, create a new Gnome-Terminal profile.  In a Terminal window, you can do this under File > New Profile.  I called mine "trans."

From that Terminal window, do the following, just like in the tutorial:
[LIST]
[*]"General" tab: uncheck "Show menubar by default in new terminals"
[*]"Background" tab: check "Transparent background" and set opacity to minimum ("None")
[*]"Scrolling" tab: disable scrollbar
[/LIST]

Also -- this is **important and different from what the tutorial says**:
In the "Title and Command"  tab, select "Replace initial title," **not** "Keep initial title."  This means that the title of a terminal window with this profile will be "trans".  That's important, because it is how we tell Compiz Fusion to identify the window.

That's it in a Terminal window.  The rest is in CompizConfig Settings Manager.  First, make sure that you have the following plugins enabled:
[LIST]
[*]Window Decoration in the "Effects" section
[*]Regex Matching in the "Utility" section (the tutorial does **not** mention this, but it is necessary)
[*]Window Rules in the "Window Management" section
[/LIST]

Go to the Window Decoration settings.  There will be a field that is called "Decoration windows."  Odds are, the current value of this field is:
```
any
```

change it to:
```
any & !title=trans
```

That excludes any window called "trans" from your window decoration rules.  So, every other window will follow your previous window decoration setting.

Now, we set special settings for the "trans" window.  Go to the Window Rules settings.  There will be a bunch of fields, most or all empty.  Put the following code:

```
title=trans
```

into these fields:
[LIST]
[*]Skip taskbar
[*]Skip pager
[*]Below
[*]Non movable windows
[*]Non resizable windows
[*]Non minimizable windows
[*]Non maximizable windows
[*]Non closable windows
[/LIST]

That applies that whole list of properties to all windows called "trans".  You'll notice that I skipped "Sticky," which was used in the tutorial.  That would put this window in every one of my workspaces.

Now, the embedded terminal is set up.  To run it, I added a custom launcher to my top Gnome panel.  The launcher executes this command:
```
gnome-terminal --window-with-profile=trans --geometry 1024x743+0+0
```

Here's what my desktop looks like running the embedded terminal:
[URL="http://ubuntuforums.org/picture.php?albumid=1321&pictureid=4637"]
[IMG]http://ubuntuforums.org/picture.php?albumid=1321&pictureid=4639[/IMG][/URL]

And here's what it looks like with some other windows.  As you can see, I didn't lose the minimize/maximize/close buttons, or the ability to move the windows:

[[IMG]http://ubuntuforums.org/picture.php?albumid=1321&pictureid=4640[/IMG]]("http://ubuntuforums.org/picture.php?albumid=1321&pictureid=4638")

(Sorry, I have my desktop wallpaper set to rotate automatically, and it changed in between screenshots -- but those were taken just minutes apart.)

You'll notice at the beginning of the post I said that I had the embedded terminal *mostly* working.  There are still some problems.

[LIST=1]
[*]There is a white stripe just a pixel or two wide down the left side of my screen whenever the embedded terminal is open.  I can't seem to get rid of it -- if I offset the terminal window to the left, it cuts off the first letter of my prompt. You'll notice that the guy in the tutorial uses Emerald for window decorations.  I don't, so that may be my problem.
[*]The embedded terminal shows up on my bottom Gnome panel just like any other window. This seems kinda clumsy to me.  There's probably a way to get that gone.  You'll notice the guy who wrote the tutorial had replaced his bottom panel with a dock, so he probably never even noticed this issue.
[*]I thought that the "Lower" option in the Window Rules would automatically display the embedded terminal below other windows.  It does not.  The embedded terminal will surface like any other window, at which point it is illegible.  Also, since it's all but invisible, it's hard to tell what's going on when this happens.  There's probably a way to fix that.
[*]I cannot access icons on the desktop while the embedded terminal is displayed.
[/LIST]

Anyway, I'm killing the embedded terminal because it doesn't work so well with automatically changing wallapaper (switch from a dark wallpaper to a light one, the terminal becomes illegible).  But, at least, I was able to do this without running into the problem you had, so I hope this helps!

---

