---
title: "Eudora 1.0 OSE as default email client"
date: 2011-08-30
forum: General Help
---

### Post by Anafiel on 2011-08-30
I'm running Zorin 5.0 (Ubuntu 11.04), and I've installed Eudora 1.0 OSE (thunderbird w/penelope extension), and I want to make this my default email client.

Right now evolution is the default.  I've gone to preferences/preferred applications and tried to set OSE as the default, but on the internet tab, only evolution is showing in the email drop-down box.

The three other tabs (Multimedia, System, Accessibility) allow for a "custom" program entry, but on the Internet tab I don't have that option.  There is no "custom" option in the drop-down for either the browser (google chrome), or mail reader.

How in the world am I supposed to add Eudora OSE??

Thanks for any help,
Anafiel

---

### Post by kyphi on 2011-08-31
You are quite right about there being no choice to set which email program you prefer but that is of no consequence.

I have not used Evolution for a long time but I have deleted the Evolution icon and removed it from my menu.  Parts of Evolution are embedded and it can therefore not be removed entirely.

As to Eudora, as far as I know, the Linux compatible version is Eudora 8 and you can run it at any time by typing "eudora" (without quotes) in a terminal.

Why not create an icon for Eudora and put it in your "Internet" menu.  You can then easily drag it to your panel for easy launch.  If you need help with that just ask.

---

### Post by Anafiel on 2011-08-31
> **kyphi said:**
> You are quite right about there being no choice to set which email program you prefer but that is of no consequence.

I have not used Evolution for a long time but I have deleted the Evolution icon and removed it from my menu.  Parts of Evolution are embedded and it can therefore not be removed entirely.

As to Eudora, as far as I know, the Linux compatible version is Eudora 8 and you can run it at any time by typing "eudora" (without quotes) in a terminal.

Why not create an icon for Eudora and put it in your "Internet" menu.  You can then easily drag it to your panel for easy launch.  If you need help with that just ask.

Thanks for the offer of help.  I've done just what you've suggested already, I'm now just trying to get rid of the annoyance of evolution spawning when I'm trying to send a link to my wife for research.  I've got a browser bookmarklet that allows me to send a page link through gmail, which is "ok", but I'd rather use my contacts in Eudora.

Evolution just doesn't have to functionally I need for all my mail accounts.  I must have over a 50 folders and sub-folders that I really need for our business and research.

---

### Post by donato roque on 2011-08-31
You might find what you're looking for in this [Ubuntu Forum thread.]("http://ubuntuforums.org/showthread.php?t=866792")

You need to use the terminal for what you want to accomplish and modify a file.

---

### Post by Anafiel on 2011-08-31
> **donato roque said:**
> You might find what you're looking for in this [Ubuntu Forum thread.]("http://ubuntuforums.org/showthread.php?t=866792")

You need to use the terminal for what you want to accomplish and modify a file.

Tried that.  I edited mimeapps.list and wherever it said evolution, I just replaced it with eudora.  What happened then is NO client was spawned.  Changed it back to evolution, and evolution was spawned.

What did I do wrong?


[Added Associations]
text/x-uri=google-chrome.desktop;
x-content/blank-dvd=brasero.desktop;
x-content/blank-cd=brasero.desktop;
##x-scheme-handler/mailto=evolution.desktop;
x-scheme-handler/mailto=eudora.desktop;


[Default Applications]
text/html=google-chrome.desktop
x-scheme-handler/http=google-chrome.desktop
x-scheme-handler/https=google-chrome.desktop
x-scheme-handler/about=google-chrome.desktop
x-scheme-handler/unknown=google-chrome.desktop
x-content/blank-dvd=brasero.desktop
x-content/blank-cd=brasero.desktop
##x-scheme-handler/mailto=evolution.desktop
x-scheme-handler/mailto=eudora.desktop

---

