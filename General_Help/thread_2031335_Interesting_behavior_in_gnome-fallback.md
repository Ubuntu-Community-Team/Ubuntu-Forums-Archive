---
title: "Interesting behavior in gnome-fallback"
date: 2012-07-21
forum: General Help
---

### Post by hawthornso23 on 2012-07-21
If you are running gnome fallback and have a panel with a few launchers on it, try the following.

1. Open any window or windows, unmaximise them and move them so that some or all of the windows extend off screen.

2. Now with your mouse simply HOVER over any launcher in your panel. 

The instant your mouse goes over any launcher all windows that extend off screen will JUMP - shift their position - so that they no longer extend off screen. If a window is too big to fit on screen it will shrink itself until it can.

Obviously this isn't a bug - somebody carefully designed it to do that.  It is pretty cleverly done too. Very subtle. How many of you knew it did that?  I only really noticed it because when I have a lot of windows open I have a habit of shifting a few way down to  clear space to work instead of minimising. But now when I do that the instant I go to open a new terminal or something they all pop back up again. Looks like I'll need to change that habit.

---

### Post by Giant Speck on 2012-07-21
I was aware that it did this, and frankly, I find it a bit annoying.  Also, for some reason, when I have a Java applet window open, regardless of whether it's partially off screen or not, it still jumps anyway.

I've been trying to figure out how to change this behavior, but I haven't found anything that has worked.

---

### Post by haresear on 2012-07-21
I use gnome-fallback, but I'm not seeing the behavior you describe. My windows stay in place when I hover the mouse over any launchers. I don't know if it would matter, but I have "focus follows mouse" set.

---

### Post by Giant Speck on 2012-07-22
I believe it has something to do with Compiz's "Place Windows" plugin.  When I disable that plugin, the effect goes away.

---

### Post by Giant Speck on 2012-07-22
And just like that, I seem to have stumbled upon a patch to the Place Windows plugin that gets rid of this behavior:

```
sudo add-apt-repository ppa:oli/compiz-place-patch
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by hawthornso23 on 2012-07-22
Brilliant! Thanks for this.  Now I just have to decide if the behavior is annoying enough to bother with the patch. It does have its cool aspects once you understand what it is doing.

---

### Post by Giant Speck on 2012-07-22
True.  If it weren't for the fact that the plugin was causing Java applet windows to jump around the screen every time I hover over a panel applet, I wouldn't have cared so much.

Apparently, the bug that causes this behavior also causes the panel to become stuck on top of fullscreen windows.

---

### Post by haresear on 2012-07-22
I thought gnome-fallback used metacity, and gnome-classic used compiz. I'm pretty sure that my gnome-fallback session is using metacity, not compiz.

Update: Okay, I just checked, and I do see the window-jump behavior when running the gnome-classic desktop (which is using compiz). One slight difference is that my window jumps back into the desktop frame as soon as focus leaves the window -- I don't have to hover the mouse over a launcher.

In the gnome-fallback desktop session (which is using metacity) I don't see this behavior.

---

