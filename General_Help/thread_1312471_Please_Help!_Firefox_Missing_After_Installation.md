---
title: "Please Help! Firefox Missing After Installation"
date: 2009-11-03
forum: General Help
---

### Post by joelandsonja on 2009-11-03
I am new to Ubuntu, and have setting up my system the last few days, only to find a problem with the installation process. 

While I was surfing the net a minor problem occurred with firefox which led me to uninstall and reinstall it. After doing so, the icon now seems to be missing from the Applications Menu, and I can't find it anywhere! I am just getting started on the whole Ubuntu thing, and I don't know what the file extension would be so I can search for it. I have tried to uninstall and reinstall it several times (Not too mention rebooting the system) and nothing seems to work. As a matter of fact, the same thing happened when I installed 7-Zip ... it doesn't show up on the Applications Menu.

Any suggestions on how to find it ... just remember I don't know a lot about the whole coding thing, so any suggestions of entering code will most likely be over my head. 

Thanks!

---

### Post by sliketymo on 2009-11-03
> **joelandsonja said:**
> I am new to Ubuntu, and have setting up my system the last few days, only to find a problem with the installation process. 

While I was surfing the net a minor problem occurred with firefox which led me to uninstall and reinstall it. After doing so, the icon now seems to be missing from the Applications Menu, and I can't find it anywhere! I am just getting started on the whole Ubuntu thing, and I don't know what the file extension would be so I can search for it. I have tried to uninstall and reinstall it several times (Not too mention rebooting the system) and nothing seems to work. As a matter of fact, the same thing happened when I installed 7-Zip ... it doesn't show up on the Applications Menu.

Any suggestions on how to find it ... just remember I don't know a lot about the whole coding thing, so any suggestions of entering code will most likely be over my head. 

Thanks!

Terminal: code firefox . See what shows up.

---

### Post by joelandsonja on 2009-11-03
Alright, I'll be honest ... I have no idea what Terminal means, and how I'm supposed to get there ... would you mind walking me through this as if you are explaining it to a 5 year old? 

Thanks for the help!

---

### Post by pastalavista on 2009-11-03
Open Synaptic Package Manager in the System-> Administration menu. Type 'firefox-3.5' in the search box. Check the box by the entry and click 'apply'.

Or, much easier, open a Terminal (from the Applications-> Accessories menu) and enter this ```
sudo apt-get install firefox-3.5
``` It will ask for your password and when you enter it, nothing will show but hit 'enter' after you've typed it.

---

### Post by joelandsonja on 2009-11-03
Ok, I managed to find the Terminal and typed in Firefox ... firefox opened up, but I still don't know where the shortcut would be located. How and I able to place the shortcut on the desktop?

---

### Post by pastalavista on 2009-11-03
> **joelandsonja said:**
> Ok, I managed to find the Terminal and typed in Firefox ... firefox opened up, but I still don't know where the shortcut would be located. How and I able to place the shortcut on the desktop?

The icon was missing because you installed firefox 3 instead of firefox 3.5 which is what comes with Karmic 9.10. You can right click on the menu item in Applications-> Internet and select "Add to Panel" or "Add to Desktop"

---

### Post by pastalavista on 2009-11-03
Just realized it isn't in the Applications menu. You can add it to the menu by right-clicking the Applications menu and select "Edit Menus". How exactly did you uninstall and re-install it?

---

### Post by joelandsonja on 2009-11-03
I used the 'Ubuntu Software Centre' to uninstall and reinstall ... 

I just finished installing Firefox 3.5 after I read your post, and it's still not there ...

Oh, and it doesn't actually show up in the Edit Menu mode for some reason ...

This is beyond frustrating ....

I'm heading off to sleep now, but I would appreciate any suggestions you can give me in the meantime!

---

### Post by pastalavista on 2009-11-03
You know, I still haven't used the Software Center. I guess I'm just too used to Synaptic and terminal commands now. I don't know why it wouldn't add it back to the menus. Must be a bug. Try checking in Synaptic (the 'Custom Filters' section) for broken packages.

---

### Post by konqueror7 on 2009-11-03
try,
```
sudo apt-get remove --purge firefox-3.5
sudo apt-get install firefox-3.5
```

---

### Post by joelandsonja on 2009-11-03
Still nothing ... 

I'm willing to use some codes if any of you have some that you might think would work. I'm getting a bit more familiar with the system now. Oh, and is there any way to make a desktop icon from the web browser itself? I managed to get on the browser by typing 'firefox' into the terminal, but I can't figure out how to bookmark it from that point.

---

### Post by joelandsonja on 2009-11-03
Ok, it now works ... here's what I did ... this is from [scouser73]("http://ubuntuforums.org/member.php?u=536148") ...

Thanks for all the help folks!

> Ok, firstly it seems that you've totally messed up installing Firefox.  Let me try and help you sort it out.

**1** - Right click & Extract the Firefox tar.bz2

**2** - Enter **gksudo nautilus** in Terminal

**3** - Copy & paste the Firefox file that you have just extracted to **/opt**

**4** - Right click on the Ubuntu start logo, select **Edit Menus**, 

**5** - Highlight the Internet sub menu & click New Item

**You will now see a small dialogue box appear**

**6** - In the Name field, type **Firefox**

**7** - In the Command field type **/opt/firefox/firefox**

**8** - In the Comment field type **Firefox**

You will now have Firefox installed.

---

