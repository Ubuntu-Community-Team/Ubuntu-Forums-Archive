---
title: "Key reprogramming"
date: 2009-09-02
forum: General Help
---

### Post by smayorgat on 2009-09-02
The tab key plastic on my laptop broke off so I can't use it anymore. I found that 'xmodmap -e "keycode 135 = 0xff09"' reprograms the otherwise useless Menu key to be used as Tab key. This worked but not when used as a combination: Alt+Tab doesn't work (when I do Alt+Menu). So I had to go to Keyboard Shortcuts (under System Preferences) and edit the "Move between windows with popup" to use the Alt+º combination.

I would still like to move between windows with the Alt+Tab (Alt+Menu) combination.

Any ideas about the reason for this odd behaviour?

---

### Post by Lostin60's on 2009-09-02
> **smayorgat said:**
> The tab key plastic on my laptop broke off so I can't use it anymore. I found that 'xmodmap -e "keycode 135 = 0xff09"' reprograms the otherwise useless Menu key to be used as Tab key. This worked but not when used as a combination: Alt+Tab doesn't work (when I do Alt+Menu). So I had to go to Keyboard Shortcuts (under System Preferences) and edit the "Move between windows with popup" to use the Alt+º combination.

I would still like to move between windows with the Alt+Tab (Alt+Menu) combination.

Any ideas about the reason for this odd behaviour?

It is because the menu key isn't associated with a modifier, at least not alt.  Look at your .xmodmap file.  Notice the second item for keycode 135 is NoSymbol.  That means that with one modifier key, typically shift, there is nothing there for the key to do.

Since you have xmodmap, I assume you have xbindkeys. If not, you will need it. Xmodmap deals with reassigning keys, not commands.  Xbindkeys deals with commands. Install xbindkeys and make a folder in you home folder called .xbindkeysrc.  This is where you assign keys to a command.

Run xbindkeys -mk. Hit your alt and menu key together. You will get an output something like this```
"(Scheme function)"
    m:0x8 + c:135
    Alt + Menu
"(Scheme function)"
    m:0x8 + c:64
    Alt + Alt_L

```
where "scheme function" is the command. So ```
"ROTATE_WINDOWS_FORWARD"
  m:0x8 + c:135
  Alt + Menu
``` (using your own output from xbindkeys -mk,) Is what you enter in .xbindkeysrc.  The xbindkeys manual explains the process very well.

Hope this helps.
[COLOR="White"]aa[/COLOR]

---

