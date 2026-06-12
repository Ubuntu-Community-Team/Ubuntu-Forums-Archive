---
title: "Global Menu only for maximized windows?"
date: 2012-02-19
forum: General Help
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-19
I am aware that there is another similar thread, but unfortunately, over there it turned into a debate on why would you or why wouldn't you want to have this, without giving a clear answer on the initial question. I really wouldn't like to discuss whether it is a good or bad idea, I would just like to have a simple answer, since I haven't found one yet.

So here goes: Is there a way in Ubuntu with Unity (I'm currently using u12.04a2) to have Global Menu only for maximized windows, and local menus for the others? If yes, how?

---

### Post by JRV on 2012-02-19
No, but that is a good idea.
I would like that.

---

### Post by jingaling on 2012-02-19
Hi,

I'm not aware of way in which you can turn off the global menu for 'shrunken' windows but there is a way to turn the global menu off. This would mean that the applications menu (File, Edit, View etc) will be embedded in the shrunken window but this will also apply to maximised windows. When a window is maximised, the window controls (min, max & close) will still be on the top panel where then would normally be.

If you want to give this a try then you just need to run the following command and then reboot:

```
sudo apt-get remove appmenu-gtk3 appmenu-gtk appmenu-qt
```


If you decide you don't like that then you can put things back to normal by running this command, again it will need a reboot:

```
sudo apt-get install appmenu-gtk3 appmenu-gtk appmenu-qt
```

Sorry I couldn't completely answer your question but I hope this helps.

Kev

---

### Post by JRV on 2012-02-19
> **jingaling said:**
> Hi,

I'm not aware of way in which you can turn off the global menu for 'shrunken' windows but there is a way to turn the global menu off. This would mean that the applications menu (File, Edit, View etc) will be embedded in the shrunken window but this will also apply to maximised windows. When a window is maximised, the window controls (min, max & close) will still be on the top panel where then would normally be.

If you want to give this a try then you just need to run the following command and then reboot:

```
sudo apt-get remove appmenu-gtk3 appmenu-gtk appmenu-qt
```


If you decide you don't like that then you can put things back to normal by running this command, again it will need a reboot:

```
sudo apt-get install appmenu-gtk3 appmenu-gtk appmenu-qt
```

Sorry I couldn't completely answer your question but I hope this helps.

Kev

I turn off global menus with this command:
```
sudo apt-get remove indicator-appmenu
```

It is not necessary to reboot, just log off and on.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-19
Thanks for the help guys. What I think is that Global Menu is a great idea, but its realization is not good enough. In Gnome 2.0 I had some plugins (or applets) with which I had it functioning just the right way: menu was a part of a window if the window was restored, or it showed on the top panel if it was maximized. For maximized windows (only) I had control buttons on the top panel also (close, restore, minimize) as well as the window title. Now that was a neat implementation.

Global menus in Unity are not done right, as I see it: Although the idea is just fine enough for maximized windows, if I have a restored window in bottom right corner (and I do), it makes working in Ubuntu very annoying. And then imagine working on a 27-inch screen! Sadly, the bug report about this was marked as "won't fix".

Another thing which is not intuitional about Global Menu the way it is now is this: if I have an active restored window in front and a maximized window in the back which I want to close, I first need to activate the window in the background and only then I'd be able to close it, whereas that is both not necessary and doesn't exist e.g. for two restored windows. It does take away a lot of time during work and doesn't promote the idea about Global Menu in the right way.

---

### Post by jingaling on 2012-02-19
You're preaching to the converted dude! I totally agree that the global menu is so counter intuitive and incredibly annoying. Like you, it annoys me when you have to go the other windows to close then down. Really slows things down.

I'm personally finding myself using Elementary OS more and more.

Kev

---

### Post by JRV on 2012-02-20
I don't like the global menus on my desktop with it's large screen, but I am trying them on my nine inch netbook. I don't know what I think of them yet.  

What I really hate it the auto maximizing windows.  I always turn that off.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-20
jingaling sorry, that wasn't addressed to any of the guys who replied to my post. I tried to express my opinion in hope that at least someone who can affect Ubuntu development will read it. Thanks again everyone for your help.

---

