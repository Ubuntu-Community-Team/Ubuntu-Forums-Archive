---
title: "[Unity] Usability issue with non-maximised windows"
date: 2011-04-29
forum: General Help
---

### Post by imbjr on 2011-04-29
If I want to work on two or more non-maximised windows, how do I simply access their menus without having to select a window into focus and then go to the top main menu?

I'm fairly impressed with Unity, but that really struck me as a major usability blunder. I can accept that the window has to brought into focus, because that's what you'd do anyway, but then having to move the mouse to the top of the screen to get at the menu options seems really off.

Is there a way of doing this that's as elegant as was the case previously?

Edit: wrongly applied [kubuntu], please ignore that.

---

### Post by soulsource on 2011-04-29
There are numerous ways to get rid of the global menu. Check the [Webupd8]("http://www.webupd8.org/2011/03/disable-appmenu-global-menu-in-ubuntu.html")-Site. 
Nevertheless, there is no "elegant" way of doing it and, what I consider a major drawback of Unity, there's no option to  enable the global menu only for maximized windows. I myself played with the thought to go back to Classic, yet after a few minutes I started to miss the Unity Launcher and I'm now back with Unity and the global menus (which I don't want to disable, for they are a great feature when working with maximized windows, they just suck when working with multiple windows visible).

---

### Post by imbjr on 2011-04-29
> **soulsource said:**
> There are numerous ways to get rid of the global menu. Check the [Webupd8]("http://www.webupd8.org/2011/03/disable-appmenu-global-menu-in-ubuntu.html")-Site. 
Nevertheless, there is no "elegant" way of doing it and, what I consider a major drawback of Unity, there's no option to  enable the global menu only for maximized windows. I myself played with the thought to go back to Classic, yet after a few minutes I started to miss the Unity Launcher and I'm now back with Unity and the global menus (which I don't want to disable, for they are a great feature when working with maximized windows, they just suck when working with multiple windows visible).

I've just fired-up Unity again and it's half-remembered my non-Unity Gnome settings. So I have non-minimised system menus on the right and when maximised, it jumps to the left. Well, I suppose that's my fault for wanting them on the right, as was the case for quite some time.

But also ...

I just noticed that the menu options are not always visible. you have to place the mouse over the global menu to see them. Well, if your "muscle memory" fails you, you are flying blind until the menu is revealed.

Seriously, the more I think this interface through, the less I like it. I imagine it's quite liked by those who like to use the keyboard a lot, but I've gotten to the point in my interface usage that I even right-click for copy and paste operations (caveat: that's usually when I'm at work at my XP machine)! I know some of you will roll your eyes at that, but basically whatever works for you, do it. But if an interface seems to be fighting you, well just don't use that interface.

I just visited that site you suggested. Made me laugh when I read:

> 
Considering the discussion on the Ayatana mailing list, who knows, maybe the AppMenu will get an option to disable the autohide or some other changes - everything is possible since Ubuntu 11.04 is still alpha.


Well not now it ain't. And the global menu still auto-hides.

---

### Post by imbjr on 2011-04-29
Had a bit of sniff around the 'net and found a much simpler way of disabling the global menu. Un-install the indicator-appmenu package. Nothing else depends on it and after logging back in, you get all your menus where they belong, or at least where I think they belong.

One other thing, as I was doing this I noticed synaptic appears to have retained its own menu. Do some apps not support the global menu? If so, that's another -1 point: the interface is not consistent.

---

### Post by imbjr on 2011-04-29
Currently looking into how to get a maximised windows buttons to the right, as I want.

Another usability FAIL has appeared: With Firefox maximised and two tabs open, I tried to drag tab 2 so it was to the left of tab 1. The Unity menu appeared and got in the way. I don't think that's acceptable and I don't think I should have to cripple the interface more by having the Unity menu pnly appear if I move the mouse to the top-left instead of just the left.

---

### Post by imbjr on 2011-04-29
Now for some nautilus FAIL:

1. I have a nautilus session open. But I want another. Well you can't get it via the Unity menu, you have to get it by the New Window menu. That feels awkward, but perhaps only because of what I've been used to.

2. More seriously, though, I started to notice that sometimes I can't select folders. I use List View and I was navigating a server via SFTP when I noticed I could not click on certain folders to select them. At first I thought it was perhaps something to do with SFTP (which by the way, now has a different password-related default of Remember Password for Session instead of Forget Immediately!), but then I noticed it happening in a regular browse of the root directory of my Natty install.

---

### Post by Traktion on 2011-05-02
Unity is really starting to grow on me, but I agree that there are some issues. Maybe these will help you and others:

1. In CompizConfiguration, change the Unity launcher to always show. It stops the auto-scroller from appearing when it shouldn't and also prevents the buggy auto-hide routine (which sticks the bar open, but in the way) from being a pain. Also, change the icon size to the smallest, so that it doesn't take up too much screen space, but is just as usable.

2. Remove the top bar app menu, so that non-maximised have their own menus. Unfortunately, the maximised window still has a menu below the top bar, but that is consistent and doesn't cause many problems. You also save some screen space as the title is still integrated into the top bar (which works well, IMO). EDIT: To add, if you have focus following the mouse, rather than on click as I do, this fixes a rather nasty bug with only being able to access menus when the window is maximised (or when windows are moved to the top of the screen):

sudo apt-get remove indicator-appmenu

3. Use either the middle mouse button and/or both 1 and 2 mouse buttons to launch another instance of a launcher app. This is very useful for nautilus, terminal etc.

4. Google for new indicator apps to show CPU usage and such. People have already written many replacements for the applets which used to run in the top menu.

Personally, with these changes, I'm finding Unity to be better than the previous interface. I'm still a little unhappy with the main menu, which should still allow easier category selection without lots of clicks and/or typing. The latter is very quick if you know what you are looking for, but not everyone remembers the name and then has to navigate (and the new menu is a bit clunky here).

I do love the new launcher though as when you have a bunch of applications open, the old task bar struggled to copy - too many tiny items made finding what you were looking for difficult. The launcher with its wee arrows works really well here, especially once you learn how to launch additional instances (this should be a right click option too, surely?).

A few more tweaks and fixes and the negatives will melt away. Even my non-computer oriented wife prefers the new interface, as she confused with launching icons with running icons, so the launcher helps her a lot. Considering it is an improvement for me too, as a software engineer and power user, that's a pretty impressive feat.

---

