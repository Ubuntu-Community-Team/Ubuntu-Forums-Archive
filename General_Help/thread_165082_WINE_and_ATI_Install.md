---
title: "WINE and ATI Install"
date: 2006-04-23
forum: General Help
---

### Post by Binny45 on 2006-04-23
Howdy folks

Wow, gotta say I'm loving the new OS.  Trying to get myself using it more and more, however still need to migrate some of my stuff.  I guess that's where Wine comes in.

I went to the site, downloaded (or loaded that URL that was listed) and installed it. So does Wine just sit there or do I need to load a window or some sort of program before I install my software? (IE World of Warcraft, Ventrillo).  Do I just simply put the CD in and do a setup?  I'm so scared of messing this up LMAO.

Also, I've been looking around the forums for a guide to installing my ATI X800 GTO Fireblade edition (PCI-Express) vid card, however all I'm able to find is stuff on installing mobile graphics cards, or AGP cards.  Any and all help would be immensely appreciated.

I guess the last thing is, are there any books out there specifically written to help a person learn about Ubuntu?  Could I go to a book store and find something that would help me learn more so I can stop bugging you good folks?

---

### Post by incubus on 2006-04-24
Hey Binny,

Welcome aboard! Good to see you're making a lot of progress quickly. You don't have to worry about bugging anybody, the beauty of the process is that your question may help other people later.

If you google "ubuntu guide" you can find some useful links as well. If you really prefer a book, Wikipedia has some references in the Ubuntu article.

Wine works like this. It creates a folder ".wine" in your home directory. All your "windows" stuff will be installed there. To run a windows executable you just have to type "wine" before, like:
$ wine setup.exe

You can configure it with:
$ winecfg

Search for World of Warcraft in the forums, I think there are "how to"s on the topic.

As for ATI, I have an X700 and it works flawlessly with the existing drivers. You have to install the package "fglrx". I'm not the best person to help you here because I've been using Dapper and don't remember the steps in Breezy anymore. Search the forums for that and post your questions.

best,
incubus

---

