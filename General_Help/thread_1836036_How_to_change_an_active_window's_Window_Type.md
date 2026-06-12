---
title: "How to change an active window's Window Type?"
date: 2011-08-30
forum: General Help
---

### Post by Zorgoth on 2011-08-30
I use a terminator (a terminal emulator) as part of my desktop background, and it works seamlessly, except for on show desktop, where it minimizaes and I don't want it to.  In Natty there is a bug that makes it so as far as I can tell the previous method of preventing windows from being minimized by show desktop doesn't work anymore.  In 10.04 I had it working fine.

My idea is that if I can find a way to change the type of the window to something like Dock, it might fix this issue.  Unfortunately wmctrl doesn't seem to be able to do that.  Does anyone know of a utility that could help me?

---

### Post by mcduck on 2011-08-30
I have no idea if that's even possible. Probably it itn't.

However using the Window Rules-plugin in Compiz should be much easier way to stop your Terminator from minimizing. If you are using Compiz, that is. :)

---

### Post by tmette on 2011-08-30
I believe there are ways to embed the terminal into the desktop too, if this helps any:

[http://lifehacker.com/294005/embed-a-terminal-in-the-desktop-with-compiz-fusion](http://lifehacker.com/294005/embed-a-terminal-in-the-desktop-with-compiz-fusion)

---

### Post by Zorgoth on 2011-08-30
I'll have a look later since I need to get moving for my day, but Window Rules is the method I am currently using to do everything to make it act like it's in the background.  I have done everything in ccsm is multiple plugins and looked through the keys in gconf-editor and compiz just doesn't seem to be able to decide that a window is immune to show desktop except by considering its type.  There are some things that *ought* to have that effect, but they don't work.

I found a tool that changes the window type to dock, devilspie; it's exhibited a bit of odd behavior though.  The first time I show desktop in a session it makes it impossible to focus the terminal.  I can refocus it after doing something like changing workspaces, and after that it seems to work fine.  Although now I find myself unable to reproduce the behavior.  If it comes up again, I'll post more.

I also have a bit of an objection to using devilspie because it's a daemon, and all I want is to change the window type of one window once per session, so a simpler command that does it's job and is then done would be better.

---

