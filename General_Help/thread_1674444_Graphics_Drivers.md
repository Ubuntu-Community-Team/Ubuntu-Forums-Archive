---
title: "Graphics Drivers"
date: 2011-01-23
forum: General Help
---

### Post by SquidMeal on 2011-01-23
I'm having a problem with my disc drive when trying to use Windows-designed discs.
I spent quiet some time fooling around in the terminal until I made a game install in full akd be able to launch. I finally managed to get Warcraft III to install and launch. However, I then realized that I hadn't installed my graphics drivers (which are formatted for a Win OS)

I inserted my drivers cd and tried to open the autorun.exe file on it through Wine. Since I have yet to find a .exe on-disc that Wine actually trusts and will allow to install, that didn't work.

I then tried to boot it through win using the terminal with this command line

wine /media/[disc name here]/autorun.exe

this launches the installer thingy, but as soon as I try to click any of the options on the menu that pops up, I'm told that the disc isn't in the drive (which it very clearly is)

now, I was frustrated when this happened with a plethera of games that I tried, but now that it won't let me install a driver, I'm pissed.

Help/ solution will be very much appreciated

---

### Post by yetiman64 on 2011-01-23
> However, I then realized that I hadn't installed my graphics drivers (which are formatted for a Win OS)Installing Windows drivers via Wine is of no use to you. They won't work or at least they won't be used under Linux for anything.

> now, I was frustrated when this happened with a plethera of games that I  tried, but now that it won't let me install a driver, I'm pissed.Maybe, by the sounds of it, you should check out the "Play On Linux" package, it helps by setting up automatically many supported games. Remember not everything will work perfectly under Wine. Also Wine is only a code compatibility layer which allows some Windows code to work on Linux, it is not a "drop in replacement" for a Windows environment (read here "forget about using any Windows drivers".)

Also check the [[COLOR=Blue]--winehq database--[/COLOR]]("http://appdb.winehq.org/") to see if your game/application is supported first, it may save you a lot of frustration. Click on the "Platinum", "Gold" or "Silver" top ten titles to get a full list for each category.

---

### Post by Mark Phelps on 2011-01-24
As already mentioned, you can't use Wine to install Windows drivers.

What make/model graphics card do you have? If it's an ATI card, and it's not one of the newer HD 3x/4x/5x card, there are NO drivers for it that you can install.

---

