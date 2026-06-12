---
title: "Keyboard Shortcuts going Wonky"
date: 2012-03-30
forum: General Help
---

### Post by jrisreal on 2012-03-30
I can't add any keyboard shortcuts...it only asks what command would be executed and doesn't allow me to input which keys would activate the shortcut.  Also, the shortcuts that were there before have stopped working as far as I can tell.  I can't take a screenshot with prtsc anymore, etc.  Anybody have any clue?  I'm running Xubuntu 11.10, installed it fresh yesterday.  If there is no solution, please tell me how to backup my third-party apps, because they always tend to get deleted whenever I reinstall the OS.

Here is a screenshot of the keyboard shortcut menu not allowing me to specify keyboard combination for the shortcut.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=215131&stc=1&d=1333096969[/IMG]

---

### Post by jrisreal on 2012-03-30
Bump

---

### Post by HiImTye on 2012-03-30
if it's anything like in Gnome, you need to click on where it says 'disabled' on the right, after you tell it what it's supposed to do

in other words, tell it the command and what not, hit the check mark button, it will return you to the list.
click on the right side where it says 'disabled' then press the keys you want
make sure you actually click 'disabled'

---

### Post by LewisTM on 2012-03-30
Lets delete your shortcuts config file and see if that helps.
First you have to logout and enter a virtual terminal (Ctrl-Alt-F1)
Log in at the prompt then delete the config file
```
rm ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml
```
Switch back to the login manager (Ctrl-Alt-F7) and return to Xubuntu.
Hopefully your shortcuts will have been reset to defaults.

Cheers!

---

### Post by GreatDanton on 2012-03-30
I don't know if this is the right place to put my question, but anyway.

The keyboard shortcut for changing languages doesn't save. I modified, so i can change the language with pressing the both shift keys together, but when i restart the computer this shortcut doesn't work.

Why my OS doesn't save the shortcut?

---

### Post by LewisTM on 2012-03-30
> **GreatDanton said:**
> I don't know if this is the right place to put my question, but anyway.

The keyboard shortcut for changing languages doesn't save. I modified, so i can change the language with pressing the both shift keys together, but when i restart the computer this shortcut doesn't work.

Why my OS doesn't save the shortcut?
This bug has been discussed many times in these forums and elsewhere. 
Basically the fix is to check 'Use system defaults' in the Xfce Settings Manager/Keyboard/Layout to prevent any conflict.

---

### Post by jrisreal on 2012-03-31
> **LewisTM said:**
> Lets delete your shortcuts config file and see if that helps.
First you have to logout and enter a virtual terminal (Ctrl-Alt-F1)
Log in at the prompt then delete the config file
```
rm ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml
```Switch back to the login manager (Ctrl-Alt-F7) and return to Xubuntu.
Hopefully your shortcuts will have been reset to defaults.

Cheers!
!!!!! I love you man!  It worked!

---

### Post by LewisTM on 2012-03-31
Good stuff!
Please mark the thread as SOLVED.

---

