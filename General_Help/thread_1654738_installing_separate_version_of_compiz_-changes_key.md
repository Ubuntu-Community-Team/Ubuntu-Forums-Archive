---
title: "installing separate version of compiz -changes keyboard shortcuts"
date: 2010-12-28
forum: General Help
---

### Post by lcdrovers on 2010-12-28
Hello, I've just had the most irritating problem when attempting to install some separate compiz animation plugins. The script for installing them is in a git repository, at git://anongit.compiz.org/users/soreau/scripts. The same git repository also has a script to install something called "compiz++," which I assume is an alternate version of compiz. Instead of running the executable "./compiz-addons" I accidentally ran "./build_compiz++," which was a very long installation process. During the build process, my computer froze, and I was forced to manually power it off by holding down the power button. When I restarted it, I figured that I might as well finish the installation that had already started, so I ran "./build_compiz++" again, which completed the installation. Then I realized that not only were none of my compiz plugins enabled, and when set, simply reverted back to being deselected, but also that all of the "Window Management" keyboard shortcuts had been erased. Not set to "disabled," they simply weren't there.

I honesetly have no idea what could possibly be happening at the moment. However, most of my questions can be boiled down to three simple ones.
1) What is "compiz++"? From the messages as it was building, it looked like some alternate version of compiz.
2) What happened to my normal compiz? Why is it not applying any plugins, and simply unchecking the plugins I do enable?
3) What happened to my keyboard shortcuts? They just randomly disappeared.

I realize this is an exceedingly obscure problem, and that I should probably be asking this on compiz forums, but the way it just wrecked my compiz settings and messed up my keyboard shortcuts made it seem to me that it might not be all due to compiz; it might be more general, and therefore more suited to these forums. I hope that this was detailed enough to answer well, and I thank you in advance for taking a look at my problem.

---

### Post by Deadite81 on 2010-12-28
Actually, it's not obscure.  It's very simple!  The compiz++ script installs the new version of Compiz (0.9), which is a total re-write and will make it's official appearance in Ubuntu 11.04.  It actually didn't wreak anything, at least as far as I know.  I haven't tried it for about a month, but back when I gave it a shot it didn't override any of my settings.  It actually installs everything separately from your 0.8.6 version of Compiz that you already had installed. 

I'm not sure what else you might have done, or how 0.9 has changed since I last tried it, but all your old settings should still be there.  First you should notice a new directory in your home folder "src".  This is were all the compiz++ stuff got built.  Also there should be a hidden folder, I think it was in ~/.config/compiz-1 that holds the new compiz 0.9 configurations.  You will notice that your original settings are still in the folder compiz. 

Last time I tried it, 0.9 used a text config back-end rather than gconf, so even though your 0.9 settings are in "compiz-1" your 0.8.6 settings are registered with gconf (use the command "gconf-editor" w/o quotes to find them, or just use ccsm).  I've gone on way too long.  Your problem probably is the fact that there is a problem with the window decoration and sharing the settings between the 2 versions. 

To remove what you've done delete the "src" folder in your home directory (assuming you've put nothing else in it, which you likely haven't).  Delete the "compiz-1" folder previously mentioned (be sure it has the "-1"!).  These actions are not explicitly necessary to getting your old settings back, so only do it if you want to. 

Then got to your /usr/local directory and delete all references to compiz in all folders (ONLY WITHIN /USR/LOCAL, such as /usr/local/bin/compiz++, etc).  This is where your problem probably is because the newly installed "compiz-decorator" is overriding your old one.  You must have superuser privileges to do this.  

After you do that assure that your settings are correct in Appearance Preferences (Normal, Custom, or whatever) and then log out or restart and everything should be back to normal.  

Some of this you have to do as root, and sorry for lack of formatting.  If there is something you don't understand or if you believe I have made a mistake let me know.  

Of course you could try out the new Compiz while you have it, I believe the command is "/usr/local/bin/compiz++ --replace" and to open the new ccsm "/usr/local/bin/ccsm++"  (I think, look in /usr/local/bin to see what the commands are for sure.) 

Hope that helped!

---

### Post by lcdrovers on 2010-12-28
I deleted the src folder, and the ~/.config/compiz-1 folder, and then restarted my computer. When I restarted, and then changed my settings, and then restarted again, however, I had lost my settings. I tried looking at the preferences in ccsm, and selected the gconf backend, as it had changed to the "Flat-file configuration backend." After doing this, I was able to get back and keep my settings, but there are still no window management keyboard shortcuts shown, although after selecting the gconf backend, the keyboard shortcuts worked as they should. I'm quite stumped.

To explain the situation the shortcuts are in, take a look at this image : [http://i.imgur.com/yHrcO.png](http://i.imgur.com/yHrcO.png)
But the window management keyboard shortcuts, although not shown, began to work after selecting the gconf backend in ccsm. Even shortcuts I had changed, i.e. pressing Super+Space to minimize windows, came back, but are still not shown in keyboard shortcuts.

---

### Post by Deadite81 on 2010-12-28
Yes, the same thing happened to me.  Did you delete the items in /usr/local/* that related to Compiz?  Your settings will always be there and stored in ~/.gconf unless you do something to them, including the Metacity shortcut keys.

My key bindings utility window looked like yours until I cleared /usr/local/ of the Compiz 0.9 stuff.  /usr/local only contains things that you installed by hand, notthing from Synaptic or Ubuntu Software Center goes in there.  **If there is nothing else you've put in there other than the Compiz 0.9 stuff** it safe to simply remove everything inside /usr/local rather than hunting the files down individually.  You have to run nautilus as root to do it.

Typing "gksu nautilus" into a terminal or Att+F2 dialog will allow you to do it.

I find it odd that your ccsm was set to use the flat file back-end.  That is not default.  If you have removed the /usr/local stuff or after you remove it it still doesn't work let me know and we can check some settings.

---

### Post by lcdrovers on 2010-12-28
There was nothing in /usr/local/ that related to compiz. /bin was empty, and most of the others were too. The ones that weren't had files relating to other programs like emacs, but none had compiz files. I'm sorry.

---

### Post by Deadite81 on 2010-12-28
Hm.  Try typing this into a terminal:
```
ls /usr/bin | grep compiz
```

If you see a compiz++ entry among the results then it installed in /usr instead of /usr/local.  It has to be somewhere:)

I am willing to venture that simply reinstalling compiz will fix it.  You'll *maybe* only need to reinstall compiz-gnome, that's the part with the window decorator, but it won't hurt anything if if you open up Synaptic Package Manager search "compiz" and then filter the results with the "Installed" tag on the left.  Highlight them all and then choose reinstall.  That should overwrite any conflicting items installed by compiz++ under /usr.  You shouldn't get any overwrite errors since compiz++ was never registered with apt.

You will have to log out or use the cmd:
```
nohup compiz --replace
```
after you do it.

---

### Post by lcdrovers on 2010-12-28
ls /usr/bin | grep compiz returned:
```
danny@danny-Studio-1557 ~ $ ls /usr/bin | grep compiz                   
compiz
compiz-decorator
```

I'm hesitant to reinstall compiz, because I'm afraid I'll lose my settings, and I've taken too long to reset them anyway. Will reinstalling compiz through synaptic remove the settings, like custom window animations, that I've setup?

---

### Post by Deadite81 on 2010-12-29
No, all your settings will remain intact.  Reinstalling will only affect the system files (libs, binaries,etc.), none of which are your settings.  Packages when installed/uninstalled should never affect your home directory, which is generally where all your user settings are stored.  You could uninstall compiz and install it a month latter and your setting would still be in gconf.  (I see this as a feature, some, however, disagree.)

There is a way under "Preferences" in the lower left-hand corner of ccsm that will allow you to import/export your settings for easy backup if it concerns you.

I should ask, is everything working correctly for you other than not seeing the shortcuts?  Such as the animations and whatnot?  I only ask because I still find it strange that you had to set it to gconf back-end.  Does your Compiz Config Settings Manager look correct?  That is are there new plugin buttons, such as "Open GL"?

The only other place I can think that the Compiz++ stuff may be stored is in /opt, unless you set a path yourself.  Do you have a /home/you/bin folder?  It might be in there.

Try the reinstall and if that doesn't help, I have the script you ran, and I'll compile it to see what it does now as opposed to when I tried it before.  If all else fails we can both have a broken key bindings config:)

---

### Post by lcdrovers on 2010-12-29
It is stored in /opt. Should I delete /opt/compiz++, reinstall, and then restart?

---

### Post by Deadite81 on 2010-12-29
Aha!  Yes, you should delete all references to compiz in /opt, especially "compiz-decorator", if it exists.  Once you do that then log out and in.  Everything should return to normal.

If it doesn't then try the reinstall.  As I said, the reinstall won't hurt anything, and may be worth doing just to make sure everything is back to normal.

---

### Post by lcdrovers on 2010-12-29
/opt only contained the compiz++ directory. I deleted that, but my keyboard shortcuts were still not shown. However, when I reinstalled every compiz package and logged out and back in, they were all there! Thanks a lot man, I really appreciate it. I thought this would be an incredibly obscure problem that I'd have to ask in multiple forums. You've made my life much easier, and I appreciate it immensely. Marking as solved.

---

### Post by Deadite81 on 2010-12-29
Glad to help!

---

