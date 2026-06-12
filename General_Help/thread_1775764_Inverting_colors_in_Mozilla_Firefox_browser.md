---
title: "Inverting colors in Mozilla Firefox browser ?"
date: 2011-06-05
forum: General Help
---

### Post by AlexeySol on 2011-06-05
Hello, 

a few months ago, I installed Ubuntu Studio 10.4 x64 edition on my computer, and I was able to invert the colors in Firefox by pressing "Windows-Key + M". 

Since I updated to the latest Ubuntu Studio release, 11.x, via the upgrade function, this inverting of colors does not work any more.  

How can I do it now ?  :(

PS: I'm using Firefox 4.0.1 right now - maybe I was using Firefox 3.6 (I don't recall it exactly) under Ubuntu 10.4 and hence it's got something to do with the browser rather than the OS ?

---

### Post by hawthornso23 on 2011-06-05
It is nothing to do with firefox. You were using the compiz negative plugin to achieve this effect. The reason why it went away is that the compiz settings all get changed during upgrade to Natty. That is because Natty includes Unity and Unity resets all your compiz settings to suit itself.

If you have the compiz config settings manager installed, you can simply  enable the negative plugin which will get the behavior you want back again. However there is a small possibility that this may damage your unity desktop. Unity will tolerate some changes to compiz settings quite well, but other changes can leave you staring at blank wallpaper. The negative plugin wouldn't seem to be one of the dangerous ones, however it is a bit unpredictable. If unity gets damaged then it can be fixed using
```
unity --repair
```
in a terminal. Getting to a terminal to run the fix is of course the fun part.

If you are using the ubuntu classic desktop ignore all that and just go ahead and enable the negative plugin.

---

### Post by AlexeySol on 2011-06-07
Thanks for the reply. I just installed the extended version of the Compiz  config settings manager, and activated the negative feature there. However, it still does not work. Do I have to restart my browser or the whole system, perhaps, to make the settings apply, or did the shortcut change ? It used to be Windows-key plus M.

Edit: I just rebooted the computer and it still does not work. I also verified the key combination / shortcut for negative, which is <super>m or n, for one or all windows. Yet it does not work. Any ideas ?

---

### Post by AlexeySol on 2011-06-08
No ideas ? 

By the way, I also noticed that my screensaver does not work anymore.

---

### Post by AlexeySol on 2011-06-09
Still nothing ? 

I think I'll have to revert to Ubuntu version 10.1 then, since Natty is just too buggy as of yet. I don't understand anyway why there would be a need to bring out a new OS every six months. I'm still running Windows Server 2003 R2 on my machines, and that system is well above 8 years old by now, and still doing everything I want. 

Maybe it's also due to a flawed update script, and I wouldn't be having these problems with a clean install of 11 ? :(

---

### Post by hawthornso23 on 2011-06-09
Sorry for the lack of reply - I've been very busy this last week and unable to check the forum. 

You say you enabled the negative plugin but you also ask which keyboard shortcuts it uses. That suggests to me that you may not have opened it up and checked how it is configured [Edit: I've just noticed your edit and it appears that you HAVE done this]. It is possible that the negative plugin is enabled but that the keyboard shortcuts for it are disabled. Double click on it in compiz config settings manager and have a look at how it is configured. Make sure the keyboard shortcuts are enabled and as you want them to be. Unity might have claimed those shortcuts to do something else.

[ My best guess is that Unity might clash with this plugin. Perhaps that is why it was disabled. ]

I wouldn't try to roll back to a previous version over just this issue. Rolling back is major surgery and probably not needed. Natty itself is fine. It is the unity desktop that most people are having trouble with. Try logging into the classic desktop on natty first. You'll find yourself back in an Gnome 2 environment which is very similar to 10.10 only better. [... because of the updated kernel and bugfixes ] 

[ See if it works in the classic desktop. I bet it will. ]

Good Luck

---

