---
title: "Strange problem: half of my desktop is missing!"
date: 2010-07-17
forum: General Help
---

### Post by deafiant on 2010-07-17
My desktop has been shifted about half way to the right and a "black hole" has been left. I'm not sure how else to describe this, so I will include a picture to try to make things clearer:
[IMG]http://dl.dropbox.com/u/3361022/screenshot_1.png[/IMG]

I have no idea how I have done this. The Android SDK Emulator is the only thing I have downloaded and played with recently. I've checked monitor settings, changed the background image, adjusted the number of desktops (all desktops are affected), logged out & back in and rebooted. I'm not sure where else to look. Googling hasn't given me any more clues so far.

Everything else is working fine. Windows will open up normally and cover up the "black hole". Although they do leave an after-image, particularly when you move them around - like a 70s video clip!
[IMG]http://dl.dropbox.com/u/3361022/screenshot_2.png[/IMG]

Does anyone have any ideas to diagnose and fix the issue? Thanks.

---

### Post by deafiant on 2010-07-18
SOLVED!

Nautilus writes to the root window and allows icons, etc. to be displayed. I've learnt that you can turn this off to allow a screen-saver or movie show through as your background.

So using gconf, I went to the key /apps/nautilus/preferences/show_desktop and changed the value to false. Desktop icons disappeared but the desktop took up the whole area. Changing the value back to true brought back the desktop icons. Strangely, this did not stick after the first reboot - I was back to the corrupted desktop. I repeated the procedure and it has been fine since. You beauty! :D

---

### Post by deafiant on 2010-07-27
I was browsing with Nautilus trying different desktop backgrounds by selecting a picture, right clicking and selecting "Set as Wallpaper..." when my desktop got borked again! Same issue - desktop shifted half-way to the right leaving a "black-hole". This seems to be some type of re-drawing bug.

At least I know how to fix it.

---

### Post by dino99 on 2010-07-27
the "set as a wallpaper" often have issue due to size definition of the saved screenshot

---

### Post by vcrpcant on 2012-02-03
I've been facing with this situation too.
I'm on dual monitors, whith GeForce 430 and using the Nvidia driver app gui, with two separat x screens (not xinerama).


Here's my two cents. Although not a definite solution, what I do is this (in the terminal, run):
$ **gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false & gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop true**


After that, and as it ocurred more than once, I set two keyboard shortcuts that do the same thing.

1st keyboard shortcut:
Go to menu "/System/Preferences/Keyboard Shortcuts", click "Add", in the "Name" field place "DESKTOP_FALSE" (or whatever you like), in the "Command" place:
**gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop _false_**
Then, click "Apply" and a new line with the shortcut will be created;  finally, click on it where it says "New Shortcut" and then press key  "**F8**"

2nd keyboard shortcut:
Go to menu "/System/Preferences/Keyboard Shortcuts", click "Add", in the  "Name" field place "DESKTOP_TRUE" (or whatever you like), in the  "Command" place:
**gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop _[COLOR=Black]true[/COLOR]_**
Then, click "Apply" and a new line with the shortcut will be created; finally, click on it where it says "New Shortcut" and then press key "**F9**"

So, next time this situation happens, you'll just have to press F8 and F9, not simultaneously but one after the other.

I tried to make it work with only one shortcut, but it didn'd work.

---

### Post by potherca on 2012-07-26
I had the same problem, it went away when I restarted nautilus with

```
sudo killall nautilus
```

---

