---
title: "Rhythmbox to start maximized"
date: 2010-06-17
forum: General Help
---

### Post by Ivkosky on 2010-06-17
Hi all


I would like to start Rhythmbox always maximized, but somehow I wasn't able to do that. :(

Rhythmbox always starts in the same way as it was closed before, i.e. if I close it by right-click when minimized in system tray, then it will open minimized and vice versa.

I found that if I want to have it maximized every time I start it, I should have window-visible box to be checked:

[https://help.ubuntu.com/community/Rhythmbox#Minimizing at start up](https://help.ubuntu.com/community/Rhythmbox#Minimizing at start up)

The issue is that I have it checked and nothing changed. :( I don't know whether this applies just to 10.04 (I am using 9.10).

I would appreciate your help! :)

---

### Post by Ivkosky on 2010-06-19
bump

---

### Post by WorMzy on 2010-06-19
Change your launchers so that they run rhythmbox-client. You can edit the one in your Applications -> Sound and Video menu by right-clicking on the unopened menu, and choosing "edit menus"; or by pressing Alt+F2 and running "alacarte".

---

### Post by Ivkosky on 2010-06-19
Hi WorMzy


Thanks for your suggestion. Unfortunately, I don't have rhythmbox in that menu. Even if I had, I wouldn't probably run rhythmbox from that menu, beacause I am used to run it from the "media" button on my Dell XPS M1330 laptop...

Any other ideas? :(

Thanks a lot!

---

### Post by WorMzy on 2010-06-19
I don't have such a key, so I can't test this, but I think you can modify the actions that such keys preform under Preferences -> Keyboard Shortcuts. I think you will need to create a new shortcut that runs rhythmbox-client, and then assign the media button to it.

Or you might be able to just change the Preferred Application (under System -> Preferences -> Preferred Applications -> Multimedia) to rhythmbox-client, although this might affect how files react when you double-click them in nautilus.

---

### Post by Ivkosky on 2010-06-19
Thanks a lot!


I've changed the preferred application to rhythmbox-client and now it opens the rhythmbox maximized by double-clicking on .mp3 file as well as by clicking on the media button.

I will be testing it for a while now, because I've tried it several times so far and rhythmbox crashed once...

---

### Post by Dngrsone on 2010-06-22
If you go into Edit, Plugins you will find a checkbox marked 'Status Icon'.

Unchecking that will remove the icon from your status bar and allow you to open and close Rhythmbox normally.

---

### Post by Ivkosky on 2010-06-23
> **Dngrsone said:**
> If you go into Edit, Plugins you will find a checkbox marked 'Status Icon'.

Unchecking that will remove the icon from your status bar and allow you to open and close Rhythmbox normally.

That's right. But what I wanted to achieve was to open Rhythmbox always maximized, but still have a possibility to minimize it to tray icon (which wouldn't be possible by unchecking the "Status Icon" plugin).

The solution suggested by WorMzy worked fine although I had few crashes. I will investigate it further, especially now, when I switched to 10.04. So far I will consider my issue as solved.

Thanks!

---

