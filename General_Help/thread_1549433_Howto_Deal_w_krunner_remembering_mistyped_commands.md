---
title: "Howto: Deal w/ krunner remembering mistyped commands"
date: 2010-08-09
forum: General Help
---

### Post by lodp on 2010-08-09
This should really be a blog post, but since I don't run a blog, it goes here..

Krunner is the application that makes a sort of command prompt pop up when you hit ALT+F2 in KDE4. It's great for getting quick access to your applications, bookmarks, devices and all sorts of other stuff.

It will remember all commands you enter and suggest them to you when you start typing the same letters the next time. Kind of like browsers will remember the content of forms you've used before.

What's been bugging me is that **when you enter a command with a typo just once, krunner will always keep suggesting that mis-spelled command to you **when you begin typing. Here's how to fix this:

Open ~/.kde/share/config/krunnerrc and find the section where it says "PastQueries=". The queries are separated by commas. Seek your mistyped commands and destroy them. Save, restart krunner (type "killall krunner&&krunner"), and enjoy.

---

