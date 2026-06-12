---
title: "how can i disable desktop?"
date: 2010-04-26
forum: General Help
---

### Post by Max Destruction on 2010-04-26
hey, i want to set up my ubuntu so the desktop doesnt load but i can open nautilus/file manager and use the window manager from the command line to open other programs. any idea how i can accomplish this?

---

### Post by _0R10N on 2010-04-26
what do try to accomplish by not loading the desktop. I don't understand what did you mean. You'll need to provide an exact description of what you have in mind!:lolflag:

Kind regards!

_0R10N >>

---

### Post by Max Destruction on 2010-04-27
sorry there. i would like not to load the desktop when ubuntu starts. no desktop, no panels, nothing. however, i would like to be able to run the gnome terminal (window) and other programs that require windows (by calling them from the command line). essentially the idea is i log in to see a gnome terminal and that's it. 

i tried lowering the run level but that just disables all graphics.

---

### Post by Max Destruction on 2010-04-27
anyone know what I mean?

---

### Post by marshag63 on 2010-04-27
You mean a black screen with just the command line?  You do know, of course, that firefox and nautilus do not run in a terminal and you would have to have X started.  You would have to use terminal applications, i.e., links for webbrowsing, midnight commander for file manager, moc for playing music, irssi for IRC, etc.

If you are not sure, check out [http://inx.maincontent.net/](http://inx.maincontent.net/) - you can seen screenshots and videos there of the apps this live CLI CD includes and decide if that is what you are really looking for.

If you want to start apps from the GUI via the command line, use Alt + F2 + name of app/command.

Hope this helps.

MarshaG

---

### Post by _0R10N on 2010-04-27
You can delete your panels, and you can edit the nautilus preferences, through the gconf-editor, so no icons will be loaded at startup.

If you want to work in only-consoles environment, you can try with "awesome". Here's a screenshot:

[http://urukrama.files.wordpress.com/2008/10/dandelion02.png]("http://urukrama.files.wordpress.com/2008/10/dandelion02.png")

You can sudo aptitude install it, running

```
sudo aptitude install awesome
```

Kind regards!

_0R10N >>

---

