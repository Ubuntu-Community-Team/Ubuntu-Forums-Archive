---
title: "Can't run Chromium browser in 10.04"
date: 2010-05-20
forum: General Help
---

### Post by Burtles on 2010-05-20
I have installed, un-installed several times but just won't run! Double click on icon gives spinning wheel for a few seconds then nothing!

Drawn a blank with this one and any help would be most appreciated!

(PS, it did run OK a few weeks ago, but I uninstalled it because of window buttons being on wrong side ;-) Would like to try again as this has been rectified)!

---

### Post by silkworm2.5 on 2010-05-20
What Linux Distro are you using? I'm using ubuntu 10.04 now with chromium and it works fine. Check your workspaces to see if it for some reason is opening in one of them

---

### Post by SlidingHorn on 2010-05-20
try running it in your terminal and see what error messages come up:

```
chromium-browser
```

---

### Post by uRock on 2010-05-20
> **silkworm2.5 said:**
> What Linux Distro are you using? I'm using ubuntu 10.04 now with chromium and it works fine. Check your workspaces to see if it for some reason is opening in one of them

**"Can't run Chromium browser in 10.04"**

---

### Post by jlaki on 2010-05-20
Try deleting Chrome's directory from Home. You need to unhide with Ctrl+H to find it. I think it's ".chrome" directory.

Note that this will delete all bookmarks and other user data for that app.

---

### Post by uRock on 2010-05-20
> **SlidingHorn said:**
> try running it in your terminal and see what error messages come up:

```
chromium-browser
```

This is the best way to find out what is going wrong with a program that is not working right.

Deleting the chromium folder in /home/.config/ folder after uninstalling Chromium will remove whatever bad configuration that may be causing your problems. A new folder will be created when you reinstall.

---

### Post by Burtles on 2010-05-21
This is the message I get when I run it in terminal:



[3075:3075:1304072817:ERROR:chrome/browser/process_singleton_linux.cc(830)] Failed to create /home/rob/.config/chromium/SingletonLock: Permission denied
[3075:3075:1304072975:ERROR:chrome/browser/browser_main.cc(968)] Failed to create a ProcessSingleton for your profile directory. This means that running multiple instances would start multiple browser processes rather than opening a new window in the existing process. Aborting now to avoid profile corruption.

---

### Post by Huh! on 2010-05-21
Their seems to be info all kinds about how to download, how to install, etc, etc. What what do I do with it then???????????? I've got like 30,000 programs and packages and what-not BUT I can't seem to find one shred of info on how to RUN, EXECUTE, LAUNCH, ACTIVATE or whatever this software???? CAN SOMEONE PLEASE TELL ME WHAT TO DO WITH SOFTWARE AND PACKAGES AFTER THEIR INSTALLED??????????:mad:

---

### Post by 23dornot23d on 2010-05-21
@Huh .... press ALT+F2 ..... and type in the name of any program you want to run

@Burtles .....Try and re-Install it from here .... [Google Chrome]("http://www.google.com/chrome") ..... how did you install it initially ? 
was it from here or another way ..... you should do it as a normal user ($) too .... if you did it as a root
user (#) ..... you may have got this problem from the way it was installed ? .....

---

### Post by JoelOl75 on 2010-05-21
Somehow there's a permission problem in your own home directory?

Try deleting the settings:

rm ~/.cache/chromium

And see if it helps.  Otherwise it's probably a more complicated permissions problem in your home directory involving alot more than just chromium

---

### Post by silkworm2.5 on 2010-05-21
> **uRock said:**
> **"Can't run Chromium browser in 10.04"**
Kubuntu? Xubuntu? Lubuntu? Ubuntu?

---

### Post by Nr90 on 2010-05-21
The thread is labeled Ubuntu.
So I guess he's using Ubuntu 10.04

I'm no Ubuntu expert but it seems you don't have the required permissions.
I think the config file you're looking for is in ~/.config/chromium
If you right click that folder --> properties --> permissions
What kind of permissions do you have and do you own the folder?

---

### Post by tango_ninja on 2010-05-21
I'm on Google's chrome right now.  I haven't used the chromium package but I recommend downloading Google Chrome for linux via this link: [http://www.google.com/chrome/eula.html?platform=linux](http://www.google.com/chrome/eula.html?platform=linux).

Once the file has downloaded, just open it with Package Manager.  There should be no problem installing and you should then be able to access it via the menu **Applications > Internet > Google Chrome**

---

### Post by uRock on 2010-05-21
> **silkworm2.5 said:**
> Kubuntu? Xubuntu? Lubuntu? Ubuntu?

[B][COLOR="DarkRed"][ubuntu][/COLOR] Can't run Chromium browser in 10.04
[/B]
Burtles, 
Did you try trashing the home/.config/chromium folder after uninstalling chromium, then reinstalling it?

---

