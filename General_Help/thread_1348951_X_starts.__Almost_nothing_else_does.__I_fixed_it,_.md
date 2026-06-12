---
title: "X starts.  Almost nothing else does.  I fixed it, but how to permanently?"
date: 2009-12-07
forum: General Help
---

### Post by BslBryan on 2009-12-07
Okay, this is a huge problem in my Karmic install.  It's happened to one other person I know, who's also running Ubuntu, but 8.04.  

*I did not do anything to break Karmic.*  **This happened on its own.**

Upon bootup, the bootsplash is animated.  GDM does load, or at least a graphical login utility.  It consists of a blue screen (x background), and an input for a username and password.  I login with my normal stats, and the terminal shows that I am logged in as bryan (me).

**[COLOR="Red"]When I login, this is what I see:[/COLOR]**

[IMG]http://i61.photobucket.com/albums/h41/Adrenalinrush_2006/Screenshot-2.png[/IMG]

**[COLOR="Red"]I run nautilus as root, because I must.  I use sudo, and this is what I see:[/COLOR]**

[IMG]http://i61.photobucket.com/albums/h41/Adrenalinrush_2006/Screenshot-1-1.png[/IMG]

**[COLOR="Red"]I have to run nearly all processes as root, or they fail.  I still don't have a usable desktop, so I start up compiz.[/COLOR]**

[IMG]http://i61.photobucket.com/albums/h41/Adrenalinrush_2006/Screenshot-2-1.png[/IMG]

**[COLOR="Red"]Now I can move stuff.  Cool.  Still no panel.  Let's fix that.[/COLOR]**

[IMG]http://i61.photobucket.com/albums/h41/Adrenalinrush_2006/Screenshot-3.png[/IMG]

**[COLOR="Red"]My gnome-panel has lost its preferences.  I'm attributing this problem to the fact that since I am running these processes as root, I am seeing root's desktop, root's panel, root's compiz settings, etc.  So, I am logged in as bryan, running as root.  I have no workaround yet.  I change this to my preferences.[/COLOR]**

[IMG]http://i61.photobucket.com/albums/h41/Adrenalinrush_2006/Screenshot-4.png[/IMG]

**[COLOR="Red"]Still, though, the panel should be taking the colors and scheme of my current theme.  I am confused by why this is happening, and I open up Appearance settings from the right-click menu on the desktop.  When it opens, without doing anything else, to my surprise, it automatically applies my theme.[/COLOR]**

[IMG]http://i61.photobucket.com/albums/h41/Adrenalinrush_2006/Screenshot-5.png[/IMG]

**[COLOR="Red"]Now that I have a somewhat usable, familiar, comfortable desktop, I must keep the terminal processes open, or all of it disappears.  Of course I cannot shutdown or restart my computer without undergoing the tedious procedure I've laid out for you here.[/COLOR]**

[IMG]http://i61.photobucket.com/albums/h41/Adrenalinrush_2006/Screenshot-6.png[/IMG]


And I have *no idea* why this is happening.  

I might know a bit of a workaround, but this absolutely should not have to happen.  If anyone has **any** ideas, I'll embrace them.

---

### Post by BslBryan on 2009-12-07
Bump up my post.

---

### Post by BslBryan on 2009-12-10
Bump.  I can now start these processes without using sudo.  But I still have to start all processes manually.

---

### Post by BslBryan on 2009-12-13
Just going to reinstall the OS.  Probably reverting to Jaunty.  I'll let everyone know if it fixes the problem.  

Before I reinstall, I'm going to try to run update-manager and see if the updates help at all.

---

### Post by john newbuntu on 2009-12-13
Now from the command prompt, were you able to do:
sudo /etc/init.d/gdm start
Hopefully, that should have started gdm on its own.  Prior to doing this though, you may want to run sudo apt-get update
and
sudo dpkg-reconfigure gdm

---

