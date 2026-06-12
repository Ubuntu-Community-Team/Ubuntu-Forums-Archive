---
title: "Firefox - mouse wheel click acting differently?"
date: 2012-09-06
forum: General Help
---

### Post by Bartender on 2012-09-06
Anyone else notice some odd behavior with the wheel click in Firefox?

I've been using the mouse wheel click in Firefox forever.  I'm pretty sure this problem arose with the latest updates because I got a bunch of updates yesterday and today's the first day I've seen this.  

Wheel-clicks from a web page open a new tab, just like always.  

But wheel-clicking on a Bookmark replaces the active tab with the Bookmark instead of opening a new tab.  To get a bookmark to open without overriding an existing tab I gotta open a new tab first, then left, right, or wheel click the Bookmark.  All 3 actions do the same thing.  

I swapped the Logitech M305 wireless mouse for an old wired Dell mouse.  The Dell mouse does the same thing, so this looks like a new problem in Firefox?  Firefox Help sez it's Firefox 15.0.

EDIT:  Wheel-clicking a tab makes it go away, just like always.  So it appears to me that the behavior is only altered when I'm in Bookmarks.  Outside of the Bookmarks wheel-clicking seems to work as expected.
Wheel-clicking the Home icon opens a new tab, so that's working like normal too.
Wheel-clicking a Bookmark in Chrome behaves as expected.  So it's not the mouse.

---

### Post by Bartender on 2012-09-07
Nobody?

I logged out of Unity, went to Gnome Classic.  Wheel-clicking on a Bookmark, or in History, works like it should.  This is on a laptop, running 12.04, Firefox 15.0.

Our main desktop PC (10.04, Firefox 15.0) works like always.

So, *only in Unity*, with Firefox 15.0, the laptop can't tell the difference between a right, wheel, or left-click in the Firefox header/toolbar (or whatever it is you call it).  It treats all clicks in Bookmarks, and webpages in History, as a left-click.  Outside of the Firefox toolbar/panel the wheel-click works fine.  In other words, if I wheel-click on a link on a webpage I get the link in a new tab.

I'll file a bug report if someone can verify they're seeing the same thing.

---

### Post by Wim Sturkenboom on 2012-09-07
Unity / Firefox on my system (12.04 64 bit) behaves as you describe; no difference between left, middle and right mous buttons in the bookmark menu. Right clicking an item in the bookmark menu does not open a context menu but indeed opens item in the same tab.

---

### Post by Bartender on 2012-09-07
OK, thanks, Wim for confirming the behavior!  

At least I'm not the only one.

I can't get into launchpad.  I was there an hour ago, now it doesn't like the password 

WTH

---

### Post by pqwoerituytrueiwoq on 2012-09-07
opens new tab here
ff 15 on 10.04 64bit
maybe cause i have something set in the tab utilities addon
edit:
works just like normal on 12.04 even on my guest account
**currently installing updates
edit:
still works the same after updates

---

### Post by Bartender on 2012-09-07
OK, I'm gonna take a look at that Tab Utilities add-on you mention...

What's weird though is that wheel-clicking works from a webpage.  It's the Firefox tools (Bookmarks, History) that aren't working right.

I found a Tab Utilities 1.1.5.  Will try that.

Well, I'll be hornswoggled.  Tab Utilities fixed the wheel-click issue.  I didn't change any settings in Tab Utilities 1.1.5 itself.  Just restarted Firefox, took a peek at the Tab Utilities settings, closed the settings and tried wheel-clicking bookmarks.

I'd prefer to know what caused the problem instead of just adding stuff, but it's working and that's good enough for now.

On our 32-bit 10.04 FF15.0 desktop PC the wheel-click never went sideways.  Just 12.04 laptop, and only in Unity, not Gnome Classic.

---

### Post by Bartender on 2012-11-18
I wanted to update this, just as an FYI & to drag it out in the open again.

I don't know why Firefox middle-click works goofy in Unity, but not in Lubuntu or Mint.  But installing the Tab Utilities add-on (I tried 1.2 this time and it did the same thing as 1.1.5) makes middle-click work like it should again. 

I installed Ubuntu 12.04 to an HP dc7800 that's going to be our daily-use PC.  The dc7800 has a Core 2 Duo CPU, and a budget nVidia 8400 video card so we can run two monitors.

For me, there are a few things that need to be done right away with a fresh install of Ubuntu.  

THE #1 FIRST THING TO DO: Go into "Brightness & Lock".  Disable the "ten minutes and you have to enter your password" setting.

With the nVidia card, I'd update the PC next, then use the Hardware Drivers utility to get the nVidia drivers.  Then ALt+F2, type in 

```
gksudo nvidia-settings
```

and get your two monitors working properly.  Save to Xconfig, then get out of nVidia setup.  Even if it says something about 'failed to parse Xconfig etc." I just follow the next prompts & the drivers work for me.  

*NOTE: If you just type in 'nvidia-settings' to access the nVidia setup GUI, your settings won't be saved and the monitors will go right back to whatever they were doing beforehand.*

With dual-monitors, there are several tweaks that must be done IMO.  

In the "Displays" window, disable "Sticky Edges" and tweak Launcher Placement to "Laptop".

Disabling Sticky Edges stops the mouse from hanging as it goes between screens, and the Launcher tweak puts one launcher on the left-hand screen instead of launchers on both screens.

Install Compiz Configuration Manager and turn on Wobbly Windows.  This stops a very annoying [bug]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/967266"), plus I kinda like Wobbly Windows.

---

### Post by greatsirkain on 2012-11-18
Mousewheel was being odd with me too. If you type 'about:config' in the firefox address bar and then type either middlemouse or mousewheel into the search filter you'll get all the options for the mouse wheel.

---

### Post by Bartender on 2012-11-28
The latest FF update (17.0) is incompatible with Tab Utilities.  Can you tell me what you toggled in about:config to get middle click working again?  I'm not having any luck so far & don't want to make things worse...

A related question - do you have to close FF to make a change in about:config stick, or does it take effect immediately?

EDIT - This is lame, but the sure-fire fix is to go into Tools>Add-ons and find your add-ons.  Disable Global Menu Bar Integration.  Restart Firefox.  The Firefox menubar will now appear just above your tabs, in the Firefox window itself, rather than right along the top of the screen in the Unity Panel.  Each time I tweak things so that they work like they did in a "traditional" desktop environment, I wonder anew why I'm bothering with Unity at all.  

I added "this affects me" to a launchpad [bug report]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/748850") describing this problem.  Launchpad status is "Won't fix".

---

### Post by Steeperton on 2012-11-28
Middle click doesn't work with the globalmenu - never has (nor does right click, which was much more useful for me). This is by design, to ensure a "consistent experience", according to Mark - I think it's inconsistent as it's what I'm used to with Firefox's menu, but heyho...

The solution I've found is to put the bookmarks button on your toolbar, (I&#8217;ve got it to the left of my tabs), then middle, right, etc works fine from that menu.

---

### Post by jerome1232 on 2012-11-28
I was going to mention that, I've always used a bookmarks toolbar with my bookmarks arranged into folders.

I guess I don't have the patience to drop down a menu for my bookmarks when I can have a little bar right in front of me. All clicks work as normal on the toolbar.

---

