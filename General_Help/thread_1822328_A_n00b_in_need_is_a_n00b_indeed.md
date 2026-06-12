---
title: "A n00b in need is a n00b indeed"
date: 2011-08-10
forum: General Help
---

### Post by mod2max on 2011-08-10
Hi ya all,

I've recently been using Ubuntu 11.04 as a replacement for Windows 7 on my Samsung N150+, having never properly used any Linux distro before, other then Debian Live a few years ago when I was trying to force my self towards being able to use Linux aswell as Windows, I must say I'm extremely impressed at how easy the transition was.

There are a few things that I'm finding difficult and confusing, It's not the operating system, it's awesome soooooooo flexible... it's me! I'm really struggling to get to grips with all the different parts that make up Ubuntu and how to control them.

So I'm wondering if I can have some (what I believe must be simple) questions answered.

First off are these first two question to do with the Gnome shell (commands)? Not Linux (commands?) it's self?
What is gconf?
What is gedit?

Now for even more silly questions...
Why isn't there a .gnome2 folder in my home directory?
What is the Gnome2 tool for?
How on earth do I remove the "Recent Docs" from the places menu?
I've said "Gnome" already, and thats what it tells me I'm using, so what's Unity? (Another GUI?) I know it created quite an argument.

That's about it... I think, I'm sure I'll come up with more questions as time goes on.

I have tried to more recent docs by looking of here but without know what I'm doing it doesn't help, for example, what the hell is Edge? A devs tool of sort? I did copy and paste some code into a text file, saved it, etc but it don't do anything and I don't know how to set "the proper permissions" and so on.

Thanks to all that can help :)

---

### Post by leilei1 on 2011-08-10
I can answer two of those questions I guess. Gedit is the text editor that come with Ubuntu as can be seen from Applications -> Accesories -> Gedit Text Editor. From the command shell you can use the command gedit followed by a file path name to open a file. You can also put the word sudo in front of the command so that you can edit root owned files.
Ex. gedit /file/path/name
      sudo gedit /file/path/name
***I wouldn't recommend editing root owned files unless you absolutely know what you're doing because it might break your system.

Unity is more like an extension of the GUI. There's an option in Compiz setting manager which is for the plugin Unity. I wouldn't try enabling or disabling it because when I did that on my system it came out to be quite catastrophic for my GUI.

That's as much as I can answer from questions, hope it helps.

Well here's also a tutorial to disable the recent documents menu as well.
[http://ubuntuforums.org/showthread.php?t=91154](http://ubuntuforums.org/showthread.php?t=91154)

---

### Post by Avoozl on 2011-08-10
Gconf-editor is for editing some settings related to gnome.  It's sort of like the registry editor in windows.

---

### Post by Ad1217 on 2011-08-10
suggestion: do not mess around with gconf. it can break your system VERY easily.

---

### Post by gandaran on 2011-08-10
> **Ad1217 said:**
> suggestion: do not mess around with gconf. it can break your system VERY easily.
NO! gconf-editor is a very handy tool and wont break your system unless you miss use it or run it as root, using it just as any user on your account is very helpful to set up things as you want them to be.

---

